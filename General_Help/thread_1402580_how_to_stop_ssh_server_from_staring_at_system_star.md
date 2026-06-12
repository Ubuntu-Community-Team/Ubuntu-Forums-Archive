---
title: "how to stop ssh server from staring at system startup ?"
date: 2010-02-09
forum: General Help
---

### Post by mahela007 on 2010-02-09
I have just installed the ssh server package for Ubuntu. How can I stop it from running at system startup?

---

### Post by davidmb on 2010-02-09
Hi,

Haven't really tried it, but this should work:
1. Open a console.
2. Type the following:
[INDENT][FONT=Courier New]sudo update-rc.d -f ssh remove[/FONT]
[/INDENT]This won't remove the sshd software package, but it won't automatically start again.

After this, to start (alternatively "stop") sshd manually you can do the following from the command line:
[INDENT][FONT=Courier New]sudo invoke-rc.d ssh start
[/FONT][/INDENT]

---

### Post by mahela007 on 2010-02-10
Thanks.. I'll try that.

---

### Post by nierdillapozi on 2010-10-16
> **davidmb said:**
> Hi,

Haven't really tried it, but this should work:
1. Open a console.
2. Type the following:
[INDENT][FONT=Courier New]sudo update-rc.d -f ssh remove[/FONT]
[/INDENT]This won't remove the sshd software package, but it won't automatically start again.

After this, to start (alternatively "stop") sshd manually you can do the following from the command line:
[INDENT][FONT=Courier New]sudo invoke-rc.d ssh start
[/FONT][/INDENT]


For me it wasn't the solution, I found this one [[COLOR="DeepSkyBlue"]_here_[/COLOR]]("http://osdir.com/ml/ubuntu-users/2010-07/msg00467.html"):

In /etc/init/ssh.conf replace the line "start on filesystem"
with "#start on filesystem" if you only want to disable the automatic
start at boot time but still want to start it using "service ssh start"

That's all...

---

