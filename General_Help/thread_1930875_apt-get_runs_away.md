---
title: "apt-get runs away"
date: 2012-02-24
forum: General Help
---

### Post by sea_dawg on 2012-02-24
Hello,

I'm having problems with apt-get running away. CUP use is near maxed out no matter what I have started / running.  

With nothing running htop reports 100% on one CPU and 18% - 57% on the other, with the CUP running @ 100% changing back and forth.

htop lists the CPU hog as              apt-get -qq -y- update

I did not start apg-get. This has been going on for a few days. Exiting all running programs has no effect.  Letting it run for an hour or more in the hopes apt-get will finish it's business had not helped.  A full reboot will settle things down for a while, but it starts again.

I've tried educating myself with the apg-get man page and learned what the -q and -y switches are.  I still need to know what it is trying to update, how it started and how to get control.


Is there anyway to find out what apt-get is updating?  Is there anyway to get this under control?

Please see attached image

Intel P4, 4 g RAM installed
Maverick with all updates
Dual boot with Win XP, Ubuntu is on it's own HDD

Thank you

---

### Post by roelforg on 2012-02-24
First:
Chase and catch apt-get and put it on a leash.
Second:
It's normal, it tries to process as fast as possible, that costs CPU (also, it does a lot of compression = CPU eater).

---

### Post by sea_dawg on 2012-02-24
I can't leash it, the dog ran off with her leash!

All is quiet now, maybe after 3 days of this apt-get has finally finished it's task?  

Time will tell.

---

### Post by roelforg on 2012-02-24
> **sea_dawg said:**
> I can't leash it, the dog ran off with her leash!

All is quiet now, maybe after 3 days of this apt-get has finally finished it's task?  

Time will tell.
You didn't say that it's been doing this for 3DAYS (!).
Tell me what it's last output line it.

---

### Post by sea_dawg on 2012-02-24
roelforg,

Apologies for the slow reply.  I had to run off to work. I left the machine on while I was gone.  It seems to finally have sorted itself out and settled down.

When I said it had gone on for 3 days, that was not continuous 24 X 7.  Rather it was the hours I was was using it in the evenings.  

Out of curiosity, what was the last line you were asking about in your previous post?

Ray

---

### Post by roelforg on 2012-02-25
> **sea_dawg said:**
> roelforg,

Apologies for the slow reply.  I had to run off to work. I left the machine on while I was gone.  It seems to finally have sorted itself out and settled down.

When I said it had gone on for 3 days, that was not continuous 24 X 7.  Rather it was the hours I was was using it in the evenings.  

Out of curiosity, what was the last line you were asking about in your previous post?

Ray
I was referring to the last line apt-get prints on the console.
Also, depending on how much (dependency-)packages the package you're trying to install needs, apt-get may take a long time to process them.

For instance, when installing links2 mine prints:
```

root@ubuntu:~# apt-get install links2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-12 linux-headers-3.0.0-12-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdirectfb-1.2-9 libsvga1 libsysfs2 libts-0.0-0 tsconf
The following NEW packages will be installed:
  libdirectfb-1.2-9 libsvga1 libsysfs2 libts-0.0-0 links2 tsconf
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,142 kB of archives.
After this operation, 6,414 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libsysfs2 i386 2.1.0+repack-1 [23.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric/main tsconf all 1.0-9 [6,830 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libts-0.0-0 i386 1.0-9 [23.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdirectfb-1.2-9 i386 1.2.10.0-4ubuntu3 [755 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe libsvga1 i386 1:1.4.3-31 [306 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ oneiric/universe links2 i386 2.3~pre1-1build1 [2,028 kB]
Fetched 3,142 kB in 5s (614 kB/s)   
Selecting previously deselected package libsysfs2.
(Reading database ... 112153 files and directories currently installed.)
Unpacking libsysfs2 (from .../libsysfs2_2.1.0+repack-1_i386.deb) ...
Selecting previously deselected package tsconf.
Unpacking tsconf (from .../archives/tsconf_1.0-9_all.deb) ...
Selecting previously deselected package libts-0.0-0.
Unpacking libts-0.0-0 (from .../libts-0.0-0_1.0-9_i386.deb) ...
Selecting previously deselected package libdirectfb-1.2-9.
Unpacking libdirectfb-1.2-9 (from .../libdirectfb-1.2-9_1.2.10.0-4ubuntu3_i386.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-31_i386.deb) ...
Selecting previously deselected package links2.
Unpacking links2 (from .../links2_2.3~pre1-1build1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up libsysfs2 (2.1.0+repack-1) ...
Setting up tsconf (1.0-9) ...
Setting up libts-0.0-0 (1.0-9) ...
Setting up libdirectfb-1.2-9 (1.2.10.0-4ubuntu3) ...
Setting up libsvga1 (1:1.4.3-31) ...
Setting up links2 (2.3~pre1-1build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
root@ubuntu:~# 

```
The output tells me what stage/operation apt-get is working on.
My output is from a finished one, it could hang on a setting up section or on a "Processing triggers for " section (usually the case, man-db can take like forever).

---

### Post by sea_dawg on 2012-02-25
roelforg,

More information please.  apt-get is up to it's tricks again.  It's been grinding away for about 3 hrs now.

Your previous asked for the output from apt-get.

How do I do this if was started without my action?

Notes on this morning's run away:
- I did not start it.  Some process or application started it
- Internet activity is very low, I don't think apt-get is downloading anything
- I suspect this may be web browser related.  I left the PC on overnight, it was quiet when I went to bed and quiet when I first looked at it this AM.  Then I fired up my browser and a short time later apt-get went wild.


Thank you,
Ray

---

### Post by HiImTye on 2012-02-25
> **sea_dawg said:**
> Your previous asked for the output from apt-get.

How do I do this if was started without my action?
use the log file viewer, the full log is at /var/log/apt/term.log while a condensed version with only what is updated and a status is in /var/log/apt/history.log

---

### Post by sea_dawg on 2012-02-25
I'm going to need quite a bit of help with this.  

1 - I have no idea what the log files are telling me
2 - Log file viewer reports it can't open term.log because I don't have permission.  Yet it seems to open the file?

I left to do some errands and returned to find apt-get still running, it has now been nearly 8 hrs.  This can't be normal?

---

### Post by sea_dawg on 2012-02-25
roelforg, HiImTye,

Thank you for trying to help.  I'm travelling without internet until the 4th.  I'll resume trying to solve this this when I get back.

It's now almost 12 hrs that apt-get has been running today

---

### Post by roelforg on 2012-02-26
> **sea_dawg said:**
> roelforg, HiImTye,

Thank you for trying to help.  I'm travelling without internet until the 4th.  I'll resume trying to solve this this when I get back.

It's now almost 12 hrs that apt-get has been running today
Would you please post the output that apt-get gives?

---

### Post by sea_dawg on 2012-03-04
I'm back and looking into the problem again.  I started up the PC to check email and some time later found apt-get running away again.  It is a bit different this time, please see the attached screen shots.

htop reports a number of instances root where the command column entry is > /usr/sbin/console-kit-daemon --no-daemon

System Monitor's process tab shows nearly every entry as > poll_schedule_timeout in the Waiting Channel column

A full shutdown and restart has temporarily cleared up> /usr/sbin/console-kit-daemon --no-daemon however > poll_schedule_timeout remains.

---

