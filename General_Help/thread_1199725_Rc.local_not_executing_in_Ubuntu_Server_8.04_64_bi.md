---
title: "Rc.local not executing in Ubuntu Server 8.04 64 bit"
date: 2009-06-29
forum: General Help
---

### Post by dragos2 on 2009-06-29
I am wondering why on a fresh install of ubuntu Server 8.04 64 bit when
adding some exports at the end of /etc/rc.local and then chmod a+x and reboot
the exports are not visible. Why is not rc.local executing ? It states that
'This script is executed at the end of each multiuser runlevel.' and
the runlevel is N 2.

$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

export JAVA_HOME=/usr/jdk1.6.0_14
export PATH=/usr/jdk1.6.0_14/bin:$PATH

exit 0

Any ideas where is the problem ?

---

### Post by kevdog on 2009-06-29
rc.local runs as root.  Are you trying to set a particular users path?

---

### Post by Brandon Williams on 2009-06-29
/etc/rc.local is a script that is executed and then exits. Changing environment variables there will not have any impact on the parent process's environment or the environment of any other child process started by that parent.

If you want those variables to be in the environment of all instances of bash, then you should put the exports into either /etc/profile or /etc/bash.bashrc. Putting them in /etc/profile will impact other POSIX shells, too, but putting them in /etc/bash.bashrc will not.

---

### Post by sedawk on 2009-06-29
To set the user environment edit ~/.bashrc

But remove the "exit 0" - otherwise when the shell
sources .bashrc it will log you out!

rc.local is for executing jobs once after startup.
You run a script that sets two variables which
only live as long as the script is executed and
it exists directly afterwards.

This is very similar to the following problem:
Imagine you created a shell script myscript.sh
and run it:
```

/home/user/myscript.sh
. /home/user/myscript.sh

```
The first command will run myscript (in a new temporary environment)
and not change your current working environment.
The second command will run inside your current environment
and change it. An "exit 0" at the end will close your current
environment.

---

### Post by dragos2 on 2009-06-29
Thanks for clarifications. I was using ~/.bashrc to set environment variables to be seen
in the whole system (using bash) but I think I will prefer /etc/profile instead.

I will have a service that will start a java program at startup and will depend upon that
export. What is a better approach(the service will start automatically):

1) export in /etc/profile and /etc/init.d/startjavaapp at the end of the system initialization
(will this guarantee that my java app will see the export from /etc/profile)

2) export in ~/.bashrc and /etc/init.d/startjavaapp

Which one is the correct/better variant ?

---

### Post by sedawk on 2009-06-29
Have a look at the other scripts in /etc/init.d

As fas as I can see the do the initialization of variables
like PATH themselves.

(Files like /etc/profile or /home/user/.bashrc are only for
 interactive shells. If you start a tool from an interactive
 shell everything is fine, but when starting from a 
 non-interactive shell they are not sourced (e.g. scripts
 running during startup or started by cron).
 What you can do is to source them manually but that is not
 the recommended way.
 There is some detailed documentation in the man page of bash,
 section INVOCATION)

---

