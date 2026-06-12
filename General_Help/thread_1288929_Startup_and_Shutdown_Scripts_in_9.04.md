---
title: "Startup and Shutdown Scripts in 9.04"
date: 2009-10-11
forum: General Help
---

### Post by TiredBird on 2009-10-11
I have a couple of synchronizing scripts that I want to run automatically at startup, shutdown and reboot. 

I was no expert at it, and I think its probably good that we have a new way to go, but I had at least figured out a few things about juggling scripts in System V. 

In the new system I have no clue and can't seem to find any documentation that I can understand. 

Can someone help me please and walk me through what I need to do. 

The scripts are written and run fine from the command line. 

I just need to get them to run automatically. 

Please help if you can.

---

### Post by lensman3 on 2009-10-12
Add the scripts as a line in the file "/etc/rc.local".  This file is the last thing that is run as the system runs through run-level two.

I have two lines in rc.local that are:

/sbin/ifconfig eth1 txqueuelen 100
/sbin/ifconfig eth0 txqueuelen 100

Then reduce the queue lengths on my Ethernet cards so that response is faster.  The default queue length is 1000, so 1000 packets have to dump before the 1001 packet is queued. I want faster response and a smaller queue does it. 

As the SYS5 (pronounced "sys five") systems come up, they pass through various run-levels. If your system has a file /etc/inittab, then these are the run-levels and what they stand for (look  at the file).  Level-1 is single user, used for OS repair.  Level-2 is the first time that the OS switches to multi-user(no network) and Level-3 is full multi-user(with network) (but text based consoles-no GUI).  Run level-5 starts the GUI.  

The run-level scripts live in a directory called /etc/init.d,  but the run-level link to these scripts using "ln -s" from a series of directories named "/etc/rc1.d, /etc/rc0.d, /etc/rc2.d, /etc/rc3.d and so on.  The number determines the run-level.  So certain scripts can be "ln -s"ed to the scripts. The "ln -s" are called soft links. The program that does  all this is "/sbin/init" and it is ALWAYS process 1---the first process on a multi process system.  Do a "ps ax" to prove it. Because of the "ln -s", then it is easy to delete a link without deleting the shell-script.  When "ln -s" link is executed, it points to the real file. (MS windows has no similar file link ability like Linux/Unix).

One more slight of hand.  The scripts start with S01xxx and go to S99xxx in each runlevel.  The leading S means "start", and when the machine boots the "S" files are executed  There are also a set of names that begin with "K01xxx" and go to "K99xxx". These scripts are the "Kill" scripts that are run during shutdown.  "/sbin/init" as it executes theses files from 00 to 99 and ALWAYS in order sends a "start" during boot and a "stop" during shutdown.  (Sorry I can't remember if the K files are executed from 00 to 99 or from 99 to 00).

Generally speaking, all scripts have executed by the time Run-level 3 is complete.  So the scripts at Run-level 3 are the same as run-level 5.  

Hope this helps a little..............

---

### Post by TiredBird on 2009-10-12
> **lensman3 said:**
> Add the scripts as a line in the file "/etc/rc.local".  This file is the last thing that is run as the system runs through run-level two...
I've done that and it executes fine at startup but how do I get it to do the same thing on shutdown?

---

### Post by TiredBird on 2009-10-12
Still looking for answers. I'm sure this is an easy one for someone. At least point me to the right post.

Thanks in advance for your help.

---

### Post by lswb on 2009-10-12
Here is a link explaining how to implement an rc.shutdown script.

[http://lwasserm.freeshell.org/ubuntu/rcshutdown.shtml](http://lwasserm.freeshell.org/ubuntu/rcshutdown.shtml)

---

### Post by TiredBird on 2009-10-12
> **lswb said:**
> Here is a link explaining how to implement an rc.shutdown script.

[http://lwasserm.freeshell.org/ubuntu/rcshutdown.shtml](http://lwasserm.freeshell.org/ubuntu/rcshutdown.shtml)

Thanks, I followed the link, created and installed the necessary files and it 'seems' to work. 

What I am wondering about though, is that this appears to be the same thing I would have done with System V but I thought 9.04 was now using something different.

I have since downloaded and installed 'sysv-rc-conf' and find that it too works as I would have expected. What gives?

I said above that it 'seems' to work. I'm not really sure because I now have another problem. 

The scripts use 'ssh' and 'unison' to do the synchronization. Those had worked fine without any special permissions, ie: 'sudo'. But run level scripts run as 'root' so the passwords and key files I was using no longer work.

Any suggestions?

---

### Post by lswb on 2009-10-12
So far the newer upstart init system is used to start vt/ttys and little else. Most services still use the sysv style init scripts. You can take a look at /etc/event.d to see what the upstart scripts look like, from there the rc-default script is also started, which kind of chains into the sysv style init sequence. Since most services are still packaged with sysv style initscripts, this compatiblility is really necessary. The alternative would be to write upstart style event scripts for everything and who wants to do that? :)

I'm not sure about the proper way to handle your ssh/unison password problem. Perhaps you can set up a low-priveledge user for this purpose and su to that user to run the scripts. Possibly you could set the user and server up with keys so that a password is not required.

---

### Post by TiredBird on 2009-10-13
> **lswb said:**
> ...Perhaps you can set up a low-priveledge user for this purpose and su to that user to run the scripts...
Again, thanks for your help. Your suggestion of a low privilege user seems to be what I need.
My systems only have one real user, that's me. I do everything under one login except when I 'sudo' something that needs root privileges.

Is there I way I can change the user to being me at the beginning of the startup and shutdown scripts? I know how to go up to root from my normal login but I don't know how to go down from root.

I do already have keys established among my various systems so that no passwords are necessary when I am logged in under my usual name. I ssh to my other systems and retain the same user name and privileges.

That is in fact the crux of my problem (I believe). The startup and shutdown scripts run as root, so when they ssh to another system, they look for keys for 'root' and don't find them. I also get messages about connecting to that host for the first time, (because root has never before made that connection). I don't really want 'root' to ssh around in my systems. My systems are connected to the internet and that looks like a potential security problem.

I think it would solve my problem if I knew how to make the scripts run as me instead of as root. They work fine from the command line. I don't use 'sudo' when I execute them and there is nothing contained in them that needs elevation of the user. I have changed a number of file permissions to make sure that everything functions without superuser privileges.

Can you tell me what I need to do?

---

### Post by lswb on 2009-10-13
I have seen this idea used for various purposes but have never tried to implement it myself. I know that it is used by many server programs and daemons. (Look at the usernames in /etc/passwd with a login shell of /bin/false)

I would think that for your purposes, you could just su to the username doing the backups. 

When running as root, you can change to any user without a password, and log into that user's home directory with this line:

su -l username

or su -l username -c command to run "command" immediately after logging in. "command" could be a script. Maybe this can get you started with what you want to do.

---

### Post by TiredBird on 2009-10-13
> **lswb said:**
> ...When running as root, you can change to any user without a password, and log into that user's home directory with this line:

su -l username

...Maybe this can get you started with what you want to do.

Again thanks. That may indeed be what I need. I'm going to do some experiments with that and see if it works. It looks like it might. I'll post my results in any event and hopefully put a 'SOLVED' to the thread. 

Thanks again for your help.

---

### Post by TiredBird on 2009-10-13
> **lswb said:**
> ...or su -l username -c command to run "command" immediately after logging in. "command" could be a script. Maybe this can get you started with what you want to do.

I needed this version of the command in order to make it work. Or at least I think it works now.

What I did to test it was to modify the 'rc.local' file, the one in /etc/. (I'm going to do the same to the 'rc.shutdown' file as well.) 

I had added two scripts I wanted to run at startup and shutdown. I put these two script invocations in quotes, (necessary because they had spaces in them), and preceded them with 'su -l myusername -c '. 

Then I executed that file with sudo in front so it would attempt to run with root privileges. That worked.

I said 'or at least I think it works' because I think that the startup and shutdown scripts will now perform properly, but can't be sure because I can't see their terminal output. 

On the other hand, I'll bet their terminal output does get captured someplace, I just don't know where to look for it. 

Could you please offer one more tip so I can check that too?

---

### Post by TiredBird on 2009-10-13
Anyway it looks like its working so I'm going to put a 'SOLVED' on this thread. Thanks to 'lswb' for all the help.

---

### Post by lswb on 2009-10-14
Glad you could get it to work. I'm not sure I followed your description in post #11 where you used both sudo and su.

To see the output of your scripts or commands, you can redirect the output to a file, i.e. "script >>logfile" or more likely, you would want "script >>logfile 2>&1" which will also redirect error messages to the file. Or you could do the redirection within the scripts.

---

### Post by TiredBird on 2009-10-14
> **lswb said:**
> ...I'm not sure I followed your description in post #11 where you used both sudo and su...
I had two scripts that I wanted to run, both at startup and shutdown. I had those scripts entered as commands in rc.local and rc.shutdown, (the versions in /etc/). 

I added the 'su -l username -c ' to the beginning of each of those commands. Then to test whether or not my scripts would run with the correct privileges, I executed the rc.local and rc.shutdown scripts from the command line but preceded with 'sudo' in order to initially start them as root. 

Of course those scripts are really run from the System V mechanism which runs under root. By running the rc.? scripts with sudo, I was able to determine that the reduction in privileges and renaming of the user would actually take place. 

Does that make sense?

Anyway, I'm using it and it works. Thanks for the info on the log files. I'll add that so I have a record of what it does when it runs.

Thanks again.

---

### Post by lswb on 2009-10-14
Yes, that makes sense to me now. And your quite welcome, I learned a few things from this thread myself.

---

