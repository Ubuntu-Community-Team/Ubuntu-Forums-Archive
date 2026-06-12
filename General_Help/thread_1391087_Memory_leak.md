---
title: "Memory leak"
date: 2010-01-26
forum: General Help
---

### Post by LordVeovis on 2010-01-26
My computer seems to fill it's ram rather quickly (15 min to 1 hr before it attempts to use swapspace and ram is maxed out) and I cant always see what is using up the memory.  I am not sure what to do to start troubleshooting this, help much appreciated.

---

### Post by t4thfavor on 2010-01-26
execute free -m, and see if you have alot allocated to cache.

```

            total       used       free     shared    buffers     cached
Mem:          3710       1425       2285          0        199        517
-/+ buffers/cache:        708       3002
Swap:         4690          0       4690

```


This says im using about 700MB for cache, this is good, because unused ram is wasted ram in the Linux world.

Under Windows XP this would just sit unused, with Vista they added the prefetcher that's why people thought Vista was such a mem hog.

I think your memory usage is normal.

---

### Post by LordVeovis on 2010-01-26
Well it is starting to happen right now.  If I just boot my computer and start a web browser I will use up about 300mb to 400mb if playing video's.  All I have open now is my browser, a few tabs and system monitor.

```
             total       used       free     shared    buffers     cached
Mem:           997        922         75          0         35        294
-/+ buffers/cache:        592        405
Swap:            0          0          0

```

and xorg is using 65mb of ram right now (not normal) and I have unaccounted for memory, right now not much, but i have had periods of 200 - 300 mb unaccounted for (at least by system monitor showing all processes for all users)

---

### Post by LordVeovis on 2010-01-26
I have about 150MB unaccounted for right now.

---

### Post by t4thfavor on 2010-01-26
Firefox is heavy, this machine has been on for a few days, and heres my top M

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1972 chance    20   0  923m 162m  38m R    5  4.4  75:11.36 firefox            
 1188 root      20   0  788m  89m  13m S    0  2.4  18:23.83 Xorg               
 2730 chance    20   0  742m  46m  23m S    0  1.3   3:13.98 evolution          
 1651 chance    20   0  269m  33m  12m R    0  0.9   2:18.35 ubuntuone-clien    
 1645 chance    20   0  250m  33m 8988 S    1  0.9   2:41.65 compiz.real        
 1647 chance    20   0  477m  32m  19m S    0  0.9   0:11.98 nautilus           
 1747 chance    20   0  114m  27m 4488 S    1  0.7   2:12.61 ubuntuone-syncd    
 1646 chance    20   0  329m  23m  14m S    0  0.6   1:01.89 gnome-panel        
 2794 chance    20   0  323m  23m  13m S    0  0.6   0:13.30 gedit   



Though 65M is a bit much for xorg, You are using about 315MB for cache, that will not be evident in your system monitor, as mine says 700MB in use, and free -m says 1400 and change.

It's just cache, normal operation for your PC.


Oh, and you have no swap defined.
as from the free -m command.

---

### Post by ibuclaw on 2010-01-26
You are using 600MB, which is about right for a modern operating system. Not very good in comparison to other distributions that are purposely designed for being lightweight, but for the Gnome DE, not bad at all...

The rest is being used by cache, which is completely normal. This helps prevent commonly used data from being re-read from the hard disk, which is a slow and painful process if you are doing it persistently. ;)

---

### Post by LordVeovis on 2010-01-31
I don't think it is the Cache eating up ram, and off a fresh boot with a browser open I only use 300MB - 350MB, not 600.  With the same browser open, same pages, I will eventually hit my full 1gb of ram used without opening new apps.  Once this happens my computer slows to crap and I have to reboot... This is NOT normal as I have Linux installed (currently) on 5 different boxes, ranging from 8.10 - 10.04 Ubuntu and Kubuntu and have been using them for years and have NEVER had an issue like this.  My computer basically becomes completely unusable over time.

---

### Post by houseworkshy on 2010-01-31
I've got 470 in ram right now using just the browser and system monitor.  So it may be normal.  It does seem odd though that your ram actually fills up over time when you are not doing new things.  I don't know what might cause this.  A good diagnostic which shows slightly more than the system monitor is htop. It can be installed in any of the usual ways and is run from the terminal.  Try putting that in, looking at its' man pages, then using it to home in on the resource hog if any.
It may also be worth looking at firefox, it has some add ons which pre-load pages, do you have one of those installed?  Also worth checking your start up programs, could be some background process has been added.

---

### Post by egalvan on 2010-01-31
> **LordVeovis said:**
> ```
             total       used       free     shared    buffers     cached
Mem:           997        922         75          0         35        294
-/+ buffers/cache:        592        405
[COLOR="Red"]Swap:            0          0          0[/COLOR]

```


swap is either non-existent or not enabled

---

### Post by houseworkshy on 2010-01-31
If it is that swap is simply not enabled that's easy.  Try "man swapon" in the terminal and read up.  This page could be useful too.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

And, maybe, this

[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-swap-is-not-being-used-709485/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-swap-is-not-being-used-709485/)

---

### Post by egalvan on 2010-01-31
> **houseworkshy said:**
> If it is that** swap is simply not enabled** that's easy.  Try "man swapon" in the terminal and read up

[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-swap-is-not-being-used-709485/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-swap-is-not-being-used-709485/)

swap could exist but not be enabled due to bad enumeration.
Indeed, your second link shows a perfect example of this.
And makes good reading
(with one possible solution).


BTW, the changing UUID "problem" is not a "bug" as some folks like to blame...
Anytime a partition is created, it is given a UNIQUE ID.
UUID stands for Universally Unique IDentification.

Deleting and recreating swap is creating a new partition...
hence the new UUID.
Hence the enumeration "bug".

Making a note of the current UUID before making changes to the swap will let you replace the original UUID in the fstab,
easy fix if you make note of it.

---

### Post by philinux on 2010-01-31
> **LordVeovis said:**
> Well it is starting to happen right now.  If I just boot my computer and start a web browser I will use up about 300mb to 400mb if playing video's.  All I have open now is my browser, a few tabs and system monitor.

```
             total       used       free     shared    buffers     cached
Mem:           997        922         75          0         35        294
-/+ buffers/cache:        **[COLOR="Red"]592 [/COLOR]**       405
Swap:            0          0          0

```

and xorg is using 65mb of ram right now (not normal) and I have unaccounted for memory, right now not much, but i have had periods of 200 - 300 mb unaccounted for (at least by system monitor showing all processes for all users)

The above shows actual ram in use is 592 meg.
Linux uses empty ram to cache commonly used files for better performance

---

### Post by DaveAtFraud on 2010-01-31
Seeing X just suck up more and more memory here.  Had to log in from another box a couple of days ago because the UI stop responding (mouse moved but could not access gnome-panel to switch desktops).  When I got in from the other box, all 4GB of RAM and most of my 4GB of swap were in use since I usually just leave the machine running.  Waited to see if what I needed got swapped in and finally rebooted the box.

Here's what I see from repeated runs of "ps auxk vsz" (process status sorted on virtual memory used):

[FONT="Courier New"][dave@bend ~]# ps auxk vsz
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
...
root      1215  1.5 15.8 728612 641428 tty7    Ss+  Jan28  21:11 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-
...
root      1215  1.6 16.3 753112 663184 tty7    Ss+  Jan28  22:19 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-
...
root      1215  1.2 17.3 791884 704480 tty7    Rs+  Jan28  27:24 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-
...
root      1215  1.2 20.1 904160 816116 tty7    Ss+  Jan28  32:12 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-
...
root      1215  1.1 26.4 1162024 1072256 tty7  Ss+  Jan28  41:14 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-
...
root      1215  1.1 27.3 1198996 1111752 tty7  Ss+  Jan28  42:33 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-[/FONT]

The last two runs of ps are from last night and then this morning with no user activity and just whatever processes were running (firefox, thunderbird, a bunch of xterms, stuff in the panel, etc.).  Also swap usage went from none last night to:

[FONT="Courier New"]top - 08:59:41 up 2 days, 12:16,  9 users,  load average: 0.00, 0.02, 0.00
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.3%us,  0.3%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.3%us,  0.3%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4058708k total,  3988924k used,    69784k free,   365732k buffers
Swap:  4096564k total,     1532k used,  4095032k free,  1672160k cached[/FONT]

I've got 9.10 on a VMware box that I can leave alone so I'll see if I can find a minimal set of running processes that causes X to suck up all of the memory.

I don't see this kind of problem on my CentOS 5.4 server.  I typically only reboot it when there's a new kernel and memory use with X running is stable.  I think the last time I rebooted it had been up for around 90 days.

Cheers,
Dave

---

### Post by LordVeovis on 2010-02-02
> **egalvan said:**
> swap is either non-existent or not enabled

I know swap is off, that is not the problem, the problem is the ram filling up over time with no new applications being launched.  This will lead to swap being filled (if enabled) and then the same issue of unresponsive state if left to complete it's course.  For now I have to ctrl-alt-bkspace or restart when this happens.

---

### Post by DaveAtFraud on 2010-02-02
Just restarted X since it had grown to over 2GB with about 100MB of swap used.  Certain apps were starting to get slugish.  After the restart X looked like:

[dave@bend ~]# ps aux | grep X
root     24569  6.1  1.2 138128 51964 tty7     Ss+  21:11   0:35 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-k6sZkg/database -nolisten tcp

That's right, it starts with a virtual size of about 138MB and eventually grows to over 2GB.

I guess I just have to restart X every few days.  Hey, this is just like Windoze with its therapeutic reboots.

Cheers,
Dave

---

### Post by t4thfavor on 2010-02-03
Now it's starting to sound like a mem leak. Nobody mentioned originally that X grew huge, and swap started getting filled. Those are key peices if information.

The OP's problem still looks very close to cache, perhaps leave your machine on for a long time, then post the free -m. If the cache number is low, and the used number is high, you may have a bug to hunt down.

And no, it's not like Windows, because when windows crashes the whole PC crashes, not just the gui.

---

### Post by EndingPop on 2010-02-03
I'm having a similar issue with Xorg growing in size from ~30 MiB to >3 GiB over the course of a day. Details at [this thread]("http://ubuntuforums.org/showthread.php?p=8768725")

---

### Post by DaveAtFraud on 2010-02-03
> **t4thfavor said:**
> Now it's starting to sound like a mem leak. Nobody mentioned originally that X grew huge, and swap started getting filled. Those are key peices if information.

The OP's problem still looks very close to cache, perhaps leave your machine on for a long time, then post the free -m. If the cache number is low, and the used number is high, you may have a bug to hunt down.

And no, it's not like Windows, because when windows crashes the whole PC crashes, not just the gui.
Just kidding with the comparison to Windoze. :D

I left the following running after the last restart of X:

[dave@bend ~]# while ( 1 )
while? date >> Xsize.log
while? ps aux | grep '/usr/bin/X' | grep -v grep  >> Xsize.log
while? echo " "  >> Xsize.log
while?  sleep 60
while? end

Last output is:

Wed Feb  3 16:13:45 MST 2010
root     24569  1.9 14.2 667036 579416 tty7    Ss+  Feb02  22:05 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-k6sZkg/database -nolisten tcp

Let me know if you'd like to see the file or need any other information. 

A quick glance at the file shows that the size of X stops growing once the system has been unused long enough for power management to shut down the display.  It's kind of odd that X didn't stop growing when I went to bed; only about an hour later after power management had shut down the display.  Also, It started growing again this morning as soon as I unlocked the screen and started using the system.

Cheers,
Dave

---

### Post by DaveAtFraud on 2010-02-06
This is strange.  By Thursday morning top and ps were reporting that X had again grown to about 2GB.  I wanted to try starting Ubuntu in text mode so that I could start X as a regular user from the command prompt rather than have it run as a server as user root.  I rebooted, missed the grub menu and so was left with Ubuntu running in graphical mode, again.  

The reboot seems to have sorted things out.  X seems to be behaving itself and there is only one oddity: ps and top disagree as to how much memory X is using.  ps says:

[FONT="Courier New"]root      1404  1.3  2.8 206356 116376 tty7    Ss+  Feb05  27:23 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-fAKfsE/database -nolisten tcp vt7[/FONT]

and top says:

```
[FONT="Courier New"]  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1404 root      20   0  472m 113m 7976 S    4  2.9  27:24.76 Xorg
[/FONT]
```

the 113MB and the 116376K are pretty close to the same but the 472MB VIRT and the 106356K VSS are no where near even close.

Cheers,
Dave

---

