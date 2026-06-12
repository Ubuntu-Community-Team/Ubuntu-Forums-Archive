---
title: "Device Driver Compile Error"
date: 2010-01-01
forum: General Help
---

### Post by Tiger2010 on 2010-01-01
Hi,
I am using ubuntu 9.10 and I just started with a sample device driver code (hello.c) as follows:

#define MODULE
#include <linux/module.h>

int init_module(void)
{
        printk("<1> Hello Alex!\n");
        return 0;
}

void clear_module(void)
{
        printk("<1> Goodbye!\n");
}

I have two questions:
(1) The following is my PATH using $echo $PATH command:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/src/linux-headers-2.6.31-16/include
After using gcc -c hello.c
I got the following message: 
hello.c:2:26: error: linux/module.h: No such file or directory
I thought I have already modified the path, why compiler still can't find it?

(2) After using gcc -I/usr/src/linux-headers-2.6.31-16/include -c hello.c
I have a full screen message as follows.  Can anyone help on this?

*********************************************************************************
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h: In function ‘cpumask_parse_user’:
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:960: error: ‘struct cpumask’ has no member named ‘bits’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h: In function ‘cpulist_scnprintf’:
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:975: error: ‘const struct cpumask’ has no member named ‘bits’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h: In function ‘cpulist_parse’:
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:989: error: ‘struct cpumask’ has no member named ‘bits’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1034: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alloc_cpumask_var’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1039: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘alloc_cpumask_var_node’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1045: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘zalloc_cpumask_var’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1051: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘zalloc_cpumask_var_node’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1073: error: expected ‘)’ before numeric constant
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1084: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1085: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1086: error: expected declaration specifiers or ‘...’ before ‘bool’
/usr/src/linux-headers-2.6.31-16/include/linux/cpumask.h:1087: error: expected declaration specifiers or ‘...’ before ‘bool’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/topology.h:33,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:7,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/smp.h:20: error: expected specifier-qualifier-list before ‘u16’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:7,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/topology.h:34:26: error: asm/topology.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:8,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/mmdebug.h:4:28: error: linux/autoconf.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:22,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:119: error: expected ‘)’ before ‘gfp_flags’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:214: error: expected ‘)’ before ‘flags’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:239: error: expected ‘)’ before ‘flags’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:256: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: In function ‘node_zonelist’:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:258: error: ‘flags’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:269: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:273: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:279: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: In function ‘alloc_pages_node’:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:286: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:286: error: too many arguments to function ‘node_zonelist’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:286: warning: return makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:289: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: In function ‘alloc_pages_exact_node’:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:294: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:294: error: too many arguments to function ‘node_zonelist’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:294: warning: return makes pointer from integer without a cast
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:314: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:315: error: expected ‘)’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:317: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:339: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘oom_killer_disabled’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: In function ‘oom_killer_disable’:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:343: error: ‘oom_killer_disabled’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:343: error: ‘true’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: In function ‘oom_killer_enable’:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:348: error: ‘oom_killer_disabled’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:348: error: ‘false’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:351: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gfp_allowed_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/gfp.h:353: error: expected ‘)’ before ‘mask’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:13,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:51: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h: In function ‘call_usermodehelper’:
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:78: error: ‘gfp_t’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:78: error: expected ‘;’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:80: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:80: error: too many arguments to function ‘call_usermodehelper_setup’
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h: In function ‘call_usermodehelper_keys’:
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:91: error: ‘gfp_t’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:91: error: expected ‘;’ before ‘gfp_mask’
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:93: error: ‘gfp_mask’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.31-16/include/linux/kmod.h:93: error: too many arguments to function ‘call_usermodehelper_setup’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:21,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:16,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h:31: error: expected specifier-qualifier-list before ‘mode_t’
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h:36: error: expected specifier-qualifier-list before ‘mode_t’
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h:69: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h:78: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h:167: error: expected declaration specifiers or ‘...’ before ‘mode_t’
/usr/src/linux-headers-2.6.31-16/include/linux/sysfs.h:254: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sysfs_init’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:24,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:16,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/kref.h:22: error: expected specifier-qualifier-list before ‘atomic_t’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:16,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘uevent_seqnum’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:77: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:85: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_add’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:88: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_init_and_add’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:95: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_create’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:96: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_create_and_add’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:99: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_rename’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:100: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kobject_move’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:105: error: expected declaration specifiers or ‘...’ before ‘gfp_t’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:129: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:162: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kset_register’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:164: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kset_create_and_add’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h: In function ‘to_kset’:
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:170: error: expected expression before ‘struct’
/usr/src/linux-headers-2.6.31-16/include/linux/kobject.h:170: warning: pointer/integer type mismatch in conditional expression
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:17,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/moduleparam.h: At top level:
/usr/src/linux-headers-2.6.31-16/include/linux/moduleparam.h:45: error: expected specifier-qualifier-list before ‘u16’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:18,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:176: error: expected declaration specifiers or ‘...’ before numeric constant
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:176: error: expected declaration specifiers or ‘...’ before numeric constant
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h: In function ‘__printf’:
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:176: error: expected declaration specifiers before ‘___mark_check_format’
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:186: error: storage class specified for parameter ‘__mark_empty_function’
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:189: error: storage class specified for parameter ‘marker_probe_cb’
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:196: error: storage class specified for parameter ‘marker_probe_register’
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:202: error: storage class specified for parameter ‘marker_probe_unregister’
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:207: error: storage class specified for parameter ‘marker_probe_unregister_private_data’
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:210: error: storage class specified for parameter ‘marker_get_private_data’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:42,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:27: error: expected specifier-qualifier-list before ‘wait_queue_head_t’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:25: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:74: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:79: error: storage class specified for parameter ‘wait_for_completion’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:80: error: storage class specified for parameter ‘wait_for_completion_interruptible’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:81: error: storage class specified for parameter ‘wait_for_completion_killable’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:83: error: storage class specified for parameter ‘wait_for_completion_timeout’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:85: error: storage class specified for parameter ‘wait_for_completion_interruptible_timeout’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:86: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘try_wait_for_completion’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:87: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘completion_done’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:89: error: storage class specified for parameter ‘complete’
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:90: error: storage class specified for parameter ‘complete_all’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:49: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:55: error: storage class specified for parameter ‘rcu_scheduler_active’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:18,
                 from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:64:2: error: #error "Unknown RCU implementation specified to kernel configuration"
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:202: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:207: error: storage class specified for parameter ‘wakeme_after_rcu’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:239: error: storage class specified for parameter ‘call_rcu’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:260: error: storage class specified for parameter ‘call_rcu_bh’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:263: error: storage class specified for parameter ‘synchronize_rcu’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:264: error: storage class specified for parameter ‘rcu_barrier’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:265: error: storage class specified for parameter ‘rcu_barrier_bh’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:266: error: storage class specified for parameter ‘rcu_barrier_sched’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:269: error: storage class specified for parameter ‘rcu_init’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:270: error: storage class specified for parameter ‘rcu_scheduler_starting’
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:271: error: storage class specified for parameter ‘rcu_needs_cpu’
In file included from /usr/src/linux-headers-2.6.31-16/include/linux/module.h:19,
                 from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:20: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:21: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:23: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:117: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:125: error: storage class specified for parameter ‘tracepoint_probe_register’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:131: error: storage class specified for parameter ‘tracepoint_probe_unregister’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:133: error: storage class specified for parameter ‘tracepoint_probe_register_noupdate’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:134: error: storage class specified for parameter ‘tracepoint_probe_unregister_noupdate’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:135: error: storage class specified for parameter ‘tracepoint_probe_update_all’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:137: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:142: error: storage class specified for parameter ‘tracepoint_iter_start’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:143: error: storage class specified for parameter ‘tracepoint_iter_next’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:144: error: storage class specified for parameter ‘tracepoint_iter_stop’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:145: error: storage class specified for parameter ‘tracepoint_iter_reset’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:147: error: storage class specified for parameter ‘tracepoint_get_iter_range’
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:155: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:20:23: error: asm/local.h: No such file or directory
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:22:24: error: asm/module.h: No such file or directory
In file included from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:34: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:40: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:46: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:50: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:48: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:58: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:67: error: storage class specified for parameter ‘init_module’
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:68: error: storage class specified for parameter ‘cleanup_module’
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:71: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:87: error: storage class specified for parameter ‘__this_module’
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:168: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:545: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:550: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:555: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:559: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_module_address’
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:564: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘is_module_text_address’
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:575: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:579: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:584: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:595: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:600: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
In file included from hello.c:2:
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:605: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:612: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:617: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:625: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:630: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:636: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:643: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:647: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:651: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:655: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:661: warning: empty declaration
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:679: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:686: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:691: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:696: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:714: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:720: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:166: error: declaration for parameter ‘search_exception_tables’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:87: error: parameter ‘__this_module’ has incomplete type
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:87: error: declaration for parameter ‘__this_module’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:80: error: declaration for parameter ‘trim_init_extable’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:79: error: declaration for parameter ‘sort_main_extable’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:77: error: declaration for parameter ‘sort_extable’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:74: error: declaration for parameter ‘search_extable’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:68: error: declaration for parameter ‘cleanup_module’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/module.h:67: error: declaration for parameter ‘init_module’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:146: error: declaration for parameter ‘tracepoint_get_iter_range’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:145: error: declaration for parameter ‘tracepoint_iter_reset’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:144: error: declaration for parameter ‘tracepoint_iter_stop’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:143: error: declaration for parameter ‘tracepoint_iter_next’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:142: error: declaration for parameter ‘tracepoint_iter_start’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:135: error: declaration for parameter ‘tracepoint_probe_update_all’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:134: error: declaration for parameter ‘tracepoint_probe_unregister_noupdate’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:133: error: declaration for parameter ‘tracepoint_probe_register_noupdate’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:131: error: declaration for parameter ‘tracepoint_probe_unregister’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/tracepoint.h:125: error: declaration for parameter ‘tracepoint_probe_register’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:271: error: declaration for parameter ‘rcu_needs_cpu’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:270: error: declaration for parameter ‘rcu_scheduler_starting’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:269: error: declaration for parameter ‘rcu_init’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:266: error: declaration for parameter ‘rcu_barrier_sched’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:265: error: declaration for parameter ‘rcu_barrier_bh’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:264: error: declaration for parameter ‘rcu_barrier’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:263: error: declaration for parameter ‘synchronize_rcu’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:259: error: declaration for parameter ‘call_rcu_bh’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:238: error: declaration for parameter ‘call_rcu’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:207: error: declaration for parameter ‘wakeme_after_rcu’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/rcupdate.h:55: error: declaration for parameter ‘rcu_scheduler_active’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:90: error: declaration for parameter ‘complete_all’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:89: error: declaration for parameter ‘complete’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:84: error: declaration for parameter ‘wait_for_completion_interruptible_timeout’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:82: error: declaration for parameter ‘wait_for_completion_timeout’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:81: error: declaration for parameter ‘wait_for_completion_killable’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:80: error: declaration for parameter ‘wait_for_completion_interruptible’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/completion.h:79: error: declaration for parameter ‘wait_for_completion’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:209: error: declaration for parameter ‘marker_get_private_data’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:206: error: declaration for parameter ‘marker_probe_unregister_private_data’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:201: error: declaration for parameter ‘marker_probe_unregister’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:195: error: declaration for parameter ‘marker_probe_register’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:188: error: declaration for parameter ‘marker_probe_cb’ but no such parameter
/usr/src/linux-headers-2.6.31-16/include/linux/marker.h:186: error: declaration for parameter ‘__mark_empty_function’ but no such parameter
hello.c:13: error: expected ‘{’ at end of input

---

### Post by dhillonv10 on 2010-01-01
This should help [1]

[1] [http://www.freesoftwaremagazine.com/articles/drivers_linux](http://www.freesoftwaremagazine.com/articles/drivers_linux)

---

### Post by crspybits on 2010-01-09
I'm a little confused about the process for building a device driver. On this site ([http://www.freesoftwaremagazine.com/articles/drivers_linux](http://www.freesoftwaremagazine.com/articles/drivers_linux)) it says you need to have a compiled kernel source-code-tree. However, on [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile), it says you only need the linux-headers packages.

Any help would be appreciated,
Thanks,
Chris.

---

