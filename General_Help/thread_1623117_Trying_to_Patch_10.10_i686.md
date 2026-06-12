---
title: "Trying to Patch 10.10 i686"
date: 2010-11-16
forum: General Help
---

### Post by partyk1d24 on 2010-11-16
So I saw this forum [post]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1") and I want to try it out so I went [here]("http://marc.info/?l=linux-kernel&m=128978361700898&w=2") and copied and pasted the following text into a file called test.patch.
```
---
 Documentation/kernel-parameters.txt |    2 
 drivers/tty/tty_io.c                |    1 
 include/linux/sched.h               |   19 ++++
 init/Kconfig                        |   12 +++
 kernel/fork.c                       |    5 +
 kernel/sched.c                      |   25 ++++--
 kernel/sched_autogroup.c            |  140 ++++++++++++++++++++++++++++++++++++
 kernel/sched_autogroup.h            |   18 ++++
 kernel/sysctl.c                     |   11 ++
 9 files changed, 224 insertions(+), 9 deletions(-)

Index: linux-2.6/include/linux/sched.h
===================================================================
--- linux-2.6.orig/include/linux/sched.h
+++ linux-2.6/include/linux/sched.h
@@ -509,6 +509,8 @@ struct thread_group_cputimer {
 	spinlock_t lock;
 };
 
+struct autogroup;
+
 /*
  * NOTE! "signal_struct" does not have it's own
  * locking, because a shared signal_struct always
@@ -576,6 +578,9 @@ struct signal_struct {
 
 	struct tty_struct *tty; /* NULL if no tty */
 
+#ifdef CONFIG_SCHED_AUTOGROUP
+	struct autogroup *autogroup;
+#endif
 	/*
 	 * Cumulative resource counters for dead threads in the group,
 	 * and for reaped dead child processes forked by this group.
@@ -1931,6 +1936,20 @@ int sched_rt_handler(struct ctl_table *t
 
 extern unsigned int sysctl_sched_compat_yield;
 
+#ifdef CONFIG_SCHED_AUTOGROUP
+extern unsigned int sysctl_sched_autogroup_enabled;
+
+extern void sched_autogroup_create_attach(struct task_struct *p);
+extern void sched_autogroup_detach(struct task_struct *p);
+extern void sched_autogroup_fork(struct signal_struct *sig);
+extern void sched_autogroup_exit(struct signal_struct *sig);
+#else
+static inline void sched_autogroup_create_attach(struct task_struct *p) { }
+static inline void sched_autogroup_detach(struct task_struct *p) { }
+static inline void sched_autogroup_fork(struct signal_struct *sig) { }
+static inline void sched_autogroup_exit(struct signal_struct *sig) { }
+#endif
+
 #ifdef CONFIG_RT_MUTEXES
 extern int rt_mutex_getprio(struct task_struct *p);
 extern void rt_mutex_setprio(struct task_struct *p, int prio);
Index: linux-2.6/kernel/sched.c
===================================================================
--- linux-2.6.orig/kernel/sched.c
+++ linux-2.6/kernel/sched.c
@@ -78,6 +78,7 @@
 
 #include "sched_cpupri.h"
 #include "workqueue_sched.h"
+#include "sched_autogroup.h"
 
 #define CREATE_TRACE_POINTS
 #include <trace/events/sched.h>
@@ -605,11 +606,14 @@ static inline int cpu_of(struct rq *rq)
  */
 static inline struct task_group *task_group(struct task_struct *p)
 {
+	struct task_group *tg;
 	struct cgroup_subsys_state *css;
 
 	css = task_subsys_state_check(p, cpu_cgroup_subsys_id,
 			lockdep_is_held(&task_rq(p)->lock));
-	return container_of(css, struct task_group, css);
+	tg = container_of(css, struct task_group, css);
+
+	return autogroup_task_group(p, tg);
 }
 
 /* Change a task's cfs_rq and parent entity if it moves across CPUs/groups */
@@ -2006,6 +2010,7 @@ static void sched_irq_time_avg_update(st
 #include "sched_idletask.c"
 #include "sched_fair.c"
 #include "sched_rt.c"
+#include "sched_autogroup.c"
 #include "sched_stoptask.c"
 #ifdef CONFIG_SCHED_DEBUG
 # include "sched_debug.c"
@@ -7979,7 +7984,7 @@ void __init sched_init(void)
 #ifdef CONFIG_CGROUP_SCHED
 	list_add(&init_task_group.list, &task_groups);
 	INIT_LIST_HEAD(&init_task_group.children);
-
+	autogroup_init(&init_task);
 #endif /* CONFIG_CGROUP_SCHED */
 
 #if defined CONFIG_FAIR_GROUP_SCHED && defined CONFIG_SMP
@@ -8509,15 +8514,11 @@ void sched_destroy_group(struct task_gro
 /* change task's runqueue when it moves between groups.
  *	The caller of this function should have put the task in its new group
  *	by now. This function just updates tsk->se.cfs_rq and tsk->se.parent to
- *	reflect its new group.
+ *	reflect its new group.  Called with the runqueue lock held.
  */
-void sched_move_task(struct task_struct *tsk)
+void __sched_move_task(struct task_struct *tsk, struct rq *rq)
 {
 	int on_rq, running;
-	unsigned long flags;
-	struct rq *rq;
-
-	rq = task_rq_lock(tsk, &flags);
 
 	running = task_current(rq, tsk);
 	on_rq = tsk->se.on_rq;
@@ -8538,7 +8539,15 @@ void sched_move_task(struct task_struct
 		tsk->sched_class->set_curr_task(rq);
 	if (on_rq)
 		enqueue_task(rq, tsk, 0);
+}
 
+void sched_move_task(struct task_struct *tsk)
+{
+	struct rq *rq;
+	unsigned long flags;
+
+	rq = task_rq_lock(tsk, &flags);
+	__sched_move_task(tsk, rq);
 	task_rq_unlock(rq, &flags);
 }
 #endif /* CONFIG_CGROUP_SCHED */
Index: linux-2.6/kernel/fork.c
===================================================================
--- linux-2.6.orig/kernel/fork.c
+++ linux-2.6/kernel/fork.c
@@ -174,8 +174,10 @@ static inline void free_signal_struct(st
 
 static inline void put_signal_struct(struct signal_struct *sig)
 {
-	if (atomic_dec_and_test(&sig->sigcnt))
+	if (atomic_dec_and_test(&sig->sigcnt)) {
+		sched_autogroup_exit(sig);
 		free_signal_struct(sig);
+	}
 }
 
 void __put_task_struct(struct task_struct *tsk)
@@ -904,6 +906,7 @@ static int copy_signal(unsigned long clo
 	posix_cpu_timers_init_group(sig);
 
 	tty_audit_fork(sig);
+	sched_autogroup_fork(sig);
 
 	sig->oom_adj = current->signal->oom_adj;
 	sig->oom_score_adj = current->signal->oom_score_adj;
Index: linux-2.6/drivers/tty/tty_io.c
===================================================================
--- linux-2.6.orig/drivers/tty/tty_io.c
+++ linux-2.6/drivers/tty/tty_io.c
@@ -3160,6 +3160,7 @@ static void __proc_set_tty(struct task_s
 	put_pid(tsk->signal->tty_old_pgrp);
 	tsk->signal->tty = tty_kref_get(tty);
 	tsk->signal->tty_old_pgrp = NULL;
+	sched_autogroup_create_attach(tsk);
 }
 
 static void proc_set_tty(struct task_struct *tsk, struct tty_struct *tty)
Index: linux-2.6/kernel/sched_autogroup.h
===================================================================
--- /dev/null
+++ linux-2.6/kernel/sched_autogroup.h
@@ -0,0 +1,18 @@
+#ifdef CONFIG_SCHED_AUTOGROUP
+
+static void __sched_move_task(struct task_struct *tsk, struct rq *rq);
+
+static inline struct task_group *
+autogroup_task_group(struct task_struct *p, struct task_group *tg);
+
+#else /* !CONFIG_SCHED_AUTOGROUP */
+
+static inline void autogroup_init(struct task_struct *init_task) {  }
+
+static inline struct task_group *
+autogroup_task_group(struct task_struct *p, struct task_group *tg)
+{
+	return tg;
+}
+
+#endif /* CONFIG_SCHED_AUTOGROUP */
Index: linux-2.6/kernel/sched_autogroup.c
===================================================================
--- /dev/null
+++ linux-2.6/kernel/sched_autogroup.c
@@ -0,0 +1,140 @@
+#ifdef CONFIG_SCHED_AUTOGROUP
+
+unsigned int __read_mostly sysctl_sched_autogroup_enabled = 1;
+
+struct autogroup {
+	struct kref		kref;
+	struct task_group	*tg;
+};
+
+static struct autogroup autogroup_default;
+
+static void autogroup_init(struct task_struct *init_task)
+{
+	autogroup_default.tg = &init_task_group;
+	kref_init(&autogroup_default.kref);
+	init_task->signal->autogroup = &autogroup_default;
+}
+
+static inline void autogroup_destroy(struct kref *kref)
+{
+	struct autogroup *ag = container_of(kref, struct autogroup, kref);
+	struct task_group *tg = ag->tg;
+
+	kfree(ag);
+	sched_destroy_group(tg);
+}
+
+static inline void autogroup_kref_put(struct autogroup *ag)
+{
+	kref_put(&ag->kref, autogroup_destroy);
+}
+
+static inline struct autogroup *autogroup_kref_get(struct autogroup *ag)
+{
+	kref_get(&ag->kref);
+	return ag;
+}
+
+static inline struct autogroup *autogroup_create(void)
+{
+	struct autogroup *ag = kmalloc(sizeof(*ag), GFP_KERNEL);
+
+	if (!ag)
+		goto out_fail;
+
+	ag->tg = sched_create_group(&init_task_group);
+	kref_init(&ag->kref);
+
+	if (!(IS_ERR(ag->tg)))
+		return ag;
+
+out_fail:
+	if (ag) {
+		kfree(ag);
+		WARN_ON(1);
+	} else
+		WARN_ON(1);
+
+	return autogroup_kref_get(&autogroup_default);
+}
+
+static inline struct task_group *
+autogroup_task_group(struct task_struct *p, struct task_group *tg)
+{
+	int enabled = ACCESS_ONCE(sysctl_sched_autogroup_enabled);
+
+	enabled &= (tg == &root_task_group);
+	enabled &= (p->sched_class == &fair_sched_class);
+	enabled &= (!(p->flags & PF_EXITING));
+
+	if (enabled)
+		return p->signal->autogroup->tg;
+
+	return tg;
+}
+
+static void
+autogroup_move_group(struct task_struct *p, struct autogroup *ag)
+{
+	struct autogroup *prev;
+	struct task_struct *t;
+	struct rq *rq;
+	unsigned long flags;
+
+	rq = task_rq_lock(p, &flags);
+	prev = p->signal->autogroup;
+	if (prev == ag) {
+		task_rq_unlock(rq, &flags);
+		return;
+	}
+
+	p->signal->autogroup = autogroup_kref_get(ag);
+	__sched_move_task(p, rq);
+	task_rq_unlock(rq, &flags);
+
+	rcu_read_lock();
+	list_for_each_entry_rcu(t, &p->thread_group, thread_group) {
+		sched_move_task(t);
+	}
+	rcu_read_unlock();
+
+	autogroup_kref_put(prev);
+}
+
+void sched_autogroup_create_attach(struct task_struct *p)
+{
+	struct autogroup *ag = autogroup_create();
+
+	autogroup_move_group(p, ag);
+	/* drop extra refrence added by autogroup_create() */
+	autogroup_kref_put(ag);
+}
+EXPORT_SYMBOL(sched_autogroup_create_attach);
+
+/* currently has no users */
+void sched_autogroup_detach(struct task_struct *p)
+{
+	autogroup_move_group(p, &autogroup_default);
+}
+EXPORT_SYMBOL(sched_autogroup_detach);
+
+void sched_autogroup_fork(struct signal_struct *sig)
+{
+	sig->autogroup = autogroup_kref_get(current->signal->autogroup);
+}
+
+void sched_autogroup_exit(struct signal_struct *sig)
+{
+	autogroup_kref_put(sig->autogroup);
+}
+
+static int __init setup_autogroup(char *str)
+{
+	sysctl_sched_autogroup_enabled = 0;
+
+	return 1;
+}
+
+__setup("noautogroup", setup_autogroup);
+#endif
Index: linux-2.6/kernel/sysctl.c
===================================================================
--- linux-2.6.orig/kernel/sysctl.c
+++ linux-2.6/kernel/sysctl.c
@@ -382,6 +382,17 @@ static struct ctl_table kern_table[] = {
 		.mode		= 0644,
 		.proc_handler	= proc_dointvec,
 	},
+#ifdef CONFIG_SCHED_AUTOGROUP
+	{
+		.procname	= "sched_autogroup_enabled",
+		.data		= &sysctl_sched_autogroup_enabled,
+		.maxlen		= sizeof(unsigned int),
+		.mode		= 0644,
+		.proc_handler	= proc_dointvec,
+		.extra1		= &zero,
+		.extra2		= &one,
+	},
+#endif
 #ifdef CONFIG_PROVE_LOCKING
 	{
 		.procname	= "prove_locking",
Index: linux-2.6/init/Kconfig
===================================================================
--- linux-2.6.orig/init/Kconfig
+++ linux-2.6/init/Kconfig
@@ -728,6 +728,18 @@ config NET_NS
 
 endif # NAMESPACES
 
+config SCHED_AUTOGROUP
+	bool "Automatic process group scheduling"
+	select CGROUPS
+	select CGROUP_SCHED
+	select FAIR_GROUP_SCHED
+	help
+	  This option optimizes the scheduler for common desktop workloads by
+	  automatically creating and populating task groups.  This separation
+	  of workloads isolates aggressive CPU burners (like build jobs) from
+	  desktop applications.  Task group autogeneration is currently based
+	  upon task tty association.
+
 config MM_OWNER
 	bool
 
Index: linux-2.6/Documentation/kernel-parameters.txt
===================================================================
--- linux-2.6.orig/Documentation/kernel-parameters.txt
+++ linux-2.6/Documentation/kernel-parameters.txt
@@ -1622,6 +1622,8 @@ and is between 256 and 4096 characters.
 	noapic		[SMP,APIC] Tells the kernel to not make use of any
 			IOAPICs that may be present in the system.
 
+	noautogroup	Disable scheduler automatic task group creation.
+
 	nobats		[PPC] Do not use BATs for mapping kernel lowmem
 			on "Classic" PPC cores.
```

When I run it () I get the following...
```
patch -p0 < test.patch 
patching file linux-2.6/include/linux/sched.h
Hunk #1 FAILED at 509.
Hunk #2 FAILED at 576.
Hunk #3 FAILED at 1931.
3 out of 3 hunks FAILED -- saving rejects to file linux-2.6/include/linux/sched.h.rej
patching file linux-2.6/kernel/sched.c
Hunk #1 FAILED at 78.
Hunk #2 FAILED at 605.
Hunk #3 FAILED at 2006.
Hunk #4 FAILED at 7979.
Hunk #5 FAILED at 8509.
Hunk #6 FAILED at 8538.
6 out of 6 hunks FAILED -- saving rejects to file linux-2.6/kernel/sched.c.rej
patching file linux-2.6/kernel/fork.c
Hunk #1 FAILED at 174.
Hunk #2 FAILED at 904.
2 out of 2 hunks FAILED -- saving rejects to file linux-2.6/kernel/fork.c.rej
patching file linux-2.6/drivers/tty/tty_io.c
Hunk #1 FAILED at 3160.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/drivers/tty/tty_io.c.rej
patching file linux-2.6/kernel/sched_autogroup.h
patching file linux-2.6/kernel/sched_autogroup.c
patching file linux-2.6/kernel/sysctl.c
Hunk #1 FAILED at 382.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/kernel/sysctl.c.rej
patching file linux-2.6/init/Kconfig
Hunk #1 FAILED at 728.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/init/Kconfig.rej
patching file linux-2.6/Documentation/kernel-parameters.txt
Hunk #1 FAILED at 1622.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/Documentation/kernel-parameters.txt.rej
jackie@jackie-laptop:~$ sudo patch -p0 < test.patch 
[sudo] password for jackie: 
patching file linux-2.6/include/linux/sched.h
Hunk #1 FAILED at 509.
Hunk #2 FAILED at 576.
Hunk #3 FAILED at 1931.
3 out of 3 hunks FAILED -- saving rejects to file linux-2.6/include/linux/sched.h.rej
patching file linux-2.6/kernel/sched.c
Hunk #1 FAILED at 78.
Hunk #2 FAILED at 605.
Hunk #3 FAILED at 2006.
Hunk #4 FAILED at 7979.
Hunk #5 FAILED at 8509.
Hunk #6 FAILED at 8538.
6 out of 6 hunks FAILED -- saving rejects to file linux-2.6/kernel/sched.c.rej
patching file linux-2.6/kernel/fork.c
Hunk #1 FAILED at 174.
Hunk #2 FAILED at 904.
2 out of 2 hunks FAILED -- saving rejects to file linux-2.6/kernel/fork.c.rej
patching file linux-2.6/drivers/tty/tty_io.c
Hunk #1 FAILED at 3160.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/drivers/tty/tty_io.c.rej
The next patch would create the file linux-2.6/kernel/sched_autogroup.h,
which already exists!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
1 out of 1 hunk ignored
The next patch would create the file linux-2.6/kernel/sched_autogroup.c,
which already exists!  Assume -R? [n] n
Apply anyway? [n] n
Skipping patch.
1 out of 1 hunk ignored
patching file linux-2.6/kernel/sysctl.c
Hunk #1 FAILED at 382.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/kernel/sysctl.c.rej
patching file linux-2.6/init/Kconfig
Hunk #1 FAILED at 728.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/init/Kconfig.rej
patching file linux-2.6/Documentation/kernel-parameters.txt
Hunk #1 FAILED at 1622.
1 out of 1 hunk FAILED -- saving rejects to file linux-2.6/Documentation/kernel-parameters.txt.rej

```

I'm not so good with patching so I am sure it is probably something easy. Can anyone help?!?

Thanks

---

### Post by partyk1d24 on 2010-11-16
Just thought about it should I be in a particular directory?

---

### Post by a-user on 2010-11-16
if you use -p0 for path then you should be just out of the linux src directory, e.g. you should be in /usr/src

edit: just in case, there is a more recent version of this responsivness patch
[http://marc.info/?l=linux-kernel&m=128985638523271&w=2](http://marc.info/?l=linux-kernel&m=128985638523271&w=2)

as fas i know this is the most recent one. but it is still work in progress, so maybe there is a bug or who knows what. it may change several times a day ;)

i'm currently compiling the recent 2.6.37-rc2 kernel with this patch. but this little thing won't have any effect for most users as it only increases responsiveniss during heavy load.

edit2: i guess you should remove the first line from your patch text file. i mean the one with only "---". i don't have it and patching worked (ofcourse being in the right directory).

---

### Post by fuxialis on 2010-11-16
It would be really intresting to try out .deb if anybody made it. I personally would need amd64 one :)

---

### Post by shurak on 2010-11-16
Would be great to have a .deb of kernel with the "automated per tty task groups patch" applied for Ubuntu 10.04 (32 and 64 bits) :) 
or the "how to" to do it :)

---

### Post by a-user on 2010-11-17
don't bother with this patch. currently it is nothing that has any effect for most users. see my short explanation here:
[http://forum.xbmc.org/showpost.php?p=646086&postcount=13](http://forum.xbmc.org/showpost.php?p=646086&postcount=13)

---

### Post by ggeldenhuys on 2010-11-17
You patch file needs to start an the first "Index" line, remove all the other lines above it. eg:

```
Index: linux-2.6/include/linux/sched.h
===================================================================
--- linux-2.6.orig/include/linux/sched.h
...snip.

```

You also need to have the source code of kernel 2.6.37-rc2

Then follow the instructions as show in the following URL:
  [http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)

This all worked fine for me, I'm using Ubuntu 10.04.1 (64-bit). I compiled the kernel (took an hour, but I forgot to enable concurrency for my quad core cpu).

I managed to install and reboot with the new custom kernel. The only problem I now have, is that my X11 starts in a "vesa" safemode of 1280x1014 mode, instead of using the fglrx or radeon drivers and at 1440x900.

So now I'm a bit stuck and don't know a solution to fixing the graphics driver issue. To get my system back to normal graphics I have to boot one of the Ubuntu kernels again. So I can't really test this patch. :-( It looks very impressive though, and yes I do tax my CPUs often with many code compilation etc..

---

### Post by a-user on 2010-11-17
ggeldenhuys:
if you want to see how the effect is you don't need the patch. look at this:
> 
I modiefied Lennart's
script a bit to achieve that.

Addition to my .bashrc.

if [ "$PS1" ] ; then
        mkdir -m 0700 -p /cgroup/cpu/$$
        echo 1 > /cgroup/cpu/$$/notify_on_release
        echo $$ > /cgroup/cpu/$$/tasks
fi

I created one file /bin/rmcgroup to clean up the cgroup.

#!/bin/bash
rmdir /cgroup/cpu/$1

And did following to mount cgroup and setup empty group notification.

mount -t cgroup -o cpu none /cgroup/cpu
echo "/bin/rmcgroup" > /cgroup/cpu/release_agent

And it works fine. Upon ssh to my box, a cpu cgroup is automatically
created and upon exiting the shell, this group is automatically destroyed.

So API/interface for automatically reclaiming the cgroup once it is empty 
seems to be pretty simple and works.

for common "desktop" users it even should work a bit better than the patch above. but this does not mean, that the above patch does not have its usefullness. it will come some time to stable.

---

