---
title: "top Command and Apache 2 Questions"
date: 2009-08-16
forum: General Help
---

### Post by fred!head on 2009-08-16
First, I'm a newbie to Ubuntu and servers so, if I ask a howler, laugh and enjoy yourself but also consider helping if you know the answer.

I'm running LAMP: Ubuntu Hardy Heron, Apache 2, MySQL 5+, PHP 5+. I have an app that publishes pages to remote servers using FTP.

The problem is that sometimes the FTP process causes the Apache2 process to consume 99% of server memory indefinitely. When I kill the process, using an ID from running the top command, the server comes back and I find the file has been deposited on the remote server correctly. So the FTP process worked but something after that step hangs Apache.

My question, when I run the top command, I see the process ID and Apache2 as the process. Is there any way to see exactly what happened with Apache2, ideally at that moment but also the steps before? Obviously I'd like to figure out what happens on the Apache side (the way top shows the server) and what I can do within my application to prevent that result.

Thanks for any ideas on how to debug this.

---

### Post by VipX1 on 2009-08-16
I work with XP but at home it's Linux/Ubuntu all the time. In work we use PExplorer to research the sort of problem you have, see what .dll's the program uses. I searched and found this post for an equivalent program for Ubuntu.
[http://ubuntuforums.org/showthread.php?t=810274&highlight=process+explorer](http://ubuntuforums.org/showthread.php?t=810274&highlight=process+explorer) 
I hope that helps.

---

### Post by fred!head on 2009-08-16
That's the right direction, thank you. I had to install htop and strace. Could not install or run ptrace.

However, it only traces after I specify the thread to trace and by then it has sucked 100% of memory. I need the data that happens before the memory runs out. Really when the process is created either at that moment or through a history of process threads.

I also get a set of errors when I type s in htop:

[INDENT]Trace of process 22501 - /usr/sbin/apache2 -k start
attach: ptrace(PTRACE_ATTACH, ...): Operation not permitted[/INDENT]

Any ideas what this means? The first message is what makes me think I need the full history, that the s command only starts the trace rather than displays the history of that process. The second message is simply inscrutable.

I appreciate your help. If these messages mean anything, and you have the time, I'd appreciate a little more enlightenment. Thank you!

---

### Post by wojox on 2009-08-16
Have you looked in /var/log/apache2/error.log ?

---

### Post by Sycron on 2009-08-16
> **fred!head said:**
> I also get a set of errors when I type s in htop:

[INDENT]Trace of process 22501 - /usr/sbin/apache2 -k start
attach: ptrace(PTRACE_ATTACH, ...): Operation not permitted[/INDENT]Run it with sudo.

---

### Post by fred!head on 2009-08-16
wojox, I looked in the Apache error log but only see unrelated misc lines of data from this morning:

Usage: file [-bcikLhnNrsvz0] [-e test] [-f namefile] [-F separator] [-m magicfiles] file...
       file -C -m magicfiles
Try `file --help' for more information.

Sycron, when I run s through htop I don't appear able to use sudo. When I quit htop and run sudo strace -p pid then I get no data.

I'm getting frustrated, I guess. What I want is to be able trace in real time what a specific process is doing (worst case) and what a process has done from inception up to now and then real time. Are there any unix tools that do that?

Thanks for your patience.

---

