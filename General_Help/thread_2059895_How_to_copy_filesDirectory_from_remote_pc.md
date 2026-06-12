---
title: "How to copy files/Directory from remote pc ?"
date: 2012-09-19
forum: General Help
---

### Post by honey_bee on 2012-09-19
hi,
   I have two question regarding to copy files or directory .

1- I want to copy files from my remote ubuntu computer to my local ubuntu pc.Normally
scp or may be rsync commands are used but I does not know how to use it?

2-In case of Directory and its sub directory  including files then how can i copy remotely using terminal ?

thanks
honey

---

### Post by jaithehulk on 2012-09-19
On windows server.. I use WinSCP... but I would really like to know the answer for this post..

---

### Post by Bucky Ball on 2012-09-19
Much easier if you're using static IP addresses. I use Fileszilla, BareFTP and Unison, the last one can sync directories across a network.

Recently I've started using Gigolo which mounts remote drives/partitions. Install ssh and open-ssh. Avoid Samba; you don't need it for Linux; there is plenty of great stuff around with GUI and use from terminal. ;)

[QUOTE=honey_bee]]Normally scp or may be rsync commands are used but I does not know how to use it?[/QUOTE]

There is a heap of info on how to use these available and a GUI for rsync.

---

### Post by honey_bee on 2012-09-19
dear I am using Ubuntu Linux not Windows operating system. In ubuntu i love to to use terminal .So please try to help me using command line to copy/dir.

thanks,
honey

---

### Post by Bucky Ball on 2012-09-19
> **honey_bee said:**
> dear I am using Ubuntu Linux not Windows operating system. In ubuntu i love to to use terminal .So please try to help me using command line to copy/dir.

thanks,
honey

Not sure who you're addressing. Please use user names for clarity. ;)

Totally aware you're using Linux and not Windows here.

---

### Post by laurenrodriguez1 on 2012-09-19
**Secure copy to copy files to/from a remote computer **

   Examples:-  
   
[INDENT] scp myfile [email]you@remote.machine.org[/email]:/userdisk/yourdir  [/INDENT]     Copy the file called ``myfile'' from the current directory to the directory called ``userdisk/yourdir'' belonging to the user ``you'' on the computer ``remote.machine.org''.  
   
[INDENT] scp "you@remote.machine.org:/userdisk/yourdir/*" ./   [/INDENT]     Copy all files from the directory called ``userdisk/yourdir'' belonging to the user ``you'' on the computer ``remote.machine.org'' to the current directory.

---

### Post by richardhwinter on 2012-09-19
Guess it depends what you want to achieve.
Do you have your remote PC accessible in your LAN?
Then you can copy just with any file explorer (I love Krusader for this task)
In case you want have a permanent backup done I recommend rsync. Have a look here: [http://wiki.ubuntu-forum.de/index.php/Rsync]("http://wiki.ubuntu-forum.de/index.php/Rsync")
You can create a simple backup script and run it automatically with cron (all of which is simply explained in the wiki.

---

### Post by kjohri on 2012-09-19
> 1- I want to copy files from my remote ubuntu computer to my local ubuntu pc.Normally
scp or may be rsync commands are used but I does not know how to use it?

2-In case of Directory and its sub directory including files then how can i copy remotely using terminal ?

1. rsync is a good command to copy files, locally as well as from remote host.

2. Using rsync, you can copy entire directory trees from remote host to local host and vice versa.

The following link gives the details about how to use rsync.

[http://www.softprayog.in/tutorials/rsync](http://www.softprayog.in/tutorials/rsync)

---

