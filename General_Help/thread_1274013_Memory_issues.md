---
title: "Memory issues"
date: 2009-09-24
forum: General Help
---

### Post by gatordude on 2009-09-24
OK,

I have installed 9.04 on a pc for the 3rd time. (first was a dual boot, then I got rid of windows, then on a Ubuntu only setup my hard drive crashed and I replaced it so I am on my 3rd attempt). I also have it running on a Dell laptop and I am having the same issue...

My problem is that when my PC has been running for a while (from 1 to more days) my memory is allocated for programs that are not running anymore. ( used in memory cache) and my machine is dreadfully slow and I have to reboot. (is a P4 3G machine with 2G of memory). It is happening to me on each machine I have Ubuntu installed on and I am curious as to why it is happening? Is it a bug or is it the way I close and open programs?

I am very new Linux and  to the technical jargon so please be nice. I am more than capable of following instructions and reading (well at least enough to get into trouble sometimes)

Could somebody please advise me to get this cleared up?

Cheers

---

### Post by mikewhatever on 2009-09-24
Can you explain how you know it is a memory problem?
Can you post the output of **free -m** command.

---

### Post by gatordude on 2009-09-24
Well, as I use my pc when I have multiple programs running I can see where my memory is allocated for different programs in the system monitor. When I close programs I can see where memory is dropped or added as I run programs. When my pc starts to slow down I check the system monitor and the memory is either in use by programs or used as cache for programs (programs that I am no longer currently using). After a good day of web surfing or after a few days of it my memory is either in use by programs or being used as cache for programs. Like right now after a reboot and running a web browser and running a few programs (Picassa, doc viewer, file manager were open but have been closed) my memory is 14% used by programs and 33% used as cache. The more I use my machine the more my memory is allocated for cache and when it gets to the point when my memory is allocated for cache (say 70%) my system is slow and I have to reboot and the problem is fixed until the next time.

I am not trying to run a lot of programs at one time. Just the normal amount... Firefox, doc viewer, either music or video player. Just the normal everyday type of stuff

---

### Post by gatordude on 2009-09-24
gator@gator:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013        928       1085          0         67        553
-/+ buffers/cache:        307       1706
Swap:         3223          0       3223
gator@gator:~$ 



Sorry I forgot to add this.

---

### Post by blackened on 2009-09-24
What you're describing sounds like normal behavior. Keep in mind the axiom that unused RAM is wasted RAM.

Most modern operating systems use free RAM to cache frequently accessed files so the system does not have to constantly retrieve them from the harddisk. This can sometimes give the illusion that all of your RAM is being used, but the cached data can easily make way for more pressing operations when necessary.

The best indicator of what I'm talking about is, as mikewhatever suggested: free -m.

```
trevor@zealotry:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       **1610**        **394**          0        105        875
-/+ buffers/cache:        **629**       **1375**
Swap:         1906         13       1892

```
I seemingly have ~390M free, but once you account for cached/buffered data, I really have 1.4Gb available to the OS and 600M being actively used.

Make sense?

---

### Post by gatordude on 2009-09-24
Thank you. That does make sense but when my system slows down again what can I do to search out the culprit?

---

### Post by mikewhatever on 2009-09-24
Blackended is right. Cache is useful for speeding things up, as long as it doesn't get out of control. Have you tweaked the value of swappiness? What's the output of **cat /proc/sys/vm/swappiness**?

---

### Post by gatordude on 2009-09-24
gator@gator:~$ cat /proc/sys/vm/swappiness
60
gator@gator:~$ 






And no I have not. Can you explain what that is?

---

### Post by mikewhatever on 2009-09-24
Read more on swappiness here [https://help.ubuntu.com/community/SwapFaq#Priority%20of%20swap%20containers](https://help.ubuntu.com/community/SwapFaq#Priority%20of%20swap%20containers).
I don't think there is a problem with cache, but keep watching it. Post the output of the following commands when you think the computer is getting slow.
free -m
ps aux

---

### Post by gatordude on 2009-09-24
Thanks for the info and I will post when my pc starts to drag.

Cheers and many thanks to you both

---

### Post by blackened on 2009-09-24
> **gatordude said:**
> Thank you. That does make sense but when my system slows down again what can I do to search out the culprit?

You have a few options. Free and ps aux are only going to give you a snapshot of what your usage was when you ran the command. top and htop (as well as gnome-system-monitor, gkrellm and conky, if set up) will let you monitor in realtime.

I personally prefer htop or gnome-system-monitor for the ease of sortability.

---

### Post by utnubuuser on 2009-09-24
Do you actually have to re-boot the computer, or does re-starting the xserver clear the cache? Ctrl+Alt+backspace.

PS  Check the last post on this link [http://ubuntuforums.org/showthread.php?t=533847]("http://http://ubuntuforums.org/showthread.php?t=533847") for clearing the cache.  Note there's a mention about Compiz slowing things down.

> sudo su, then > echo 3 > /proc/sys/vm/drop_caches

---

### Post by gatordude on 2009-09-24
Ok, it didnt take long tonight for it to choke on me. Here is the results from ps aux:
```

gator@gator:~$ ps aux 
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3084  1888 ?        Ss   01:31   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   01:31   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   01:31   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   01:31   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   01:31   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   01:31   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   01:31   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   01:31   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   01:31   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   01:31   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   01:31   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   01:31   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   01:31   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   01:31   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   01:31   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   01:31   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        S<   01:31   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   01:31   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   01:31   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   01:31   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   01:31   0:01 [ata/0]
root        22  0.0  0.0      0     0 ?        S<   01:31   0:00 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   01:31   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   01:31   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   01:31   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   01:31   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   01:31   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   01:31   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   01:31   0:00 [btdelconn]
root        30  0.0  0.0      0     0 ?        S    01:31   0:00 [pdflush]
root        31  0.0  0.0      0     0 ?        S    01:31   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S<   01:31   0:00 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   01:31   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   01:31   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   01:31   0:00 [ecryptfs-kthr]
root        38  0.0  0.0      0     0 ?        S<   01:31   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   01:31   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   01:31   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   01:31   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   01:31   0:01 [scsi_eh_4]
root        43  0.0  0.0      0     0 ?        S<   01:31   0:00 [scsi_eh_5]
root        44  0.0  0.0      0     0 ?        S<   01:31   0:00 [kstriped]
root        45  0.0  0.0      0     0 ?        S<   01:31   0:00 [kmpathd/0]
root        46  0.0  0.0      0     0 ?        S<   01:31   0:00 [kmpathd/1]
root        47  0.0  0.0      0     0 ?        S<   01:31   0:00 [kmpath_handle]
root        48  0.0  0.0      0     0 ?        S<   01:31   0:00 [ksnapd]
root        49  0.0  0.0      0     0 ?        S<   01:31   0:00 [kondemand/0]
root        50  0.0  0.0      0     0 ?        S<   01:31   0:00 [kondemand/1]
root        51  0.0  0.0      0     0 ?        S<   01:31   0:00 [krfcommd]
root       232  0.0  0.0      0     0 ?        S<   01:31   0:00 [scsi_eh_6]

```

And from free -m:
```

gator@gator:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013       1101        912          0         74        640
-/+ buffers/cache:        386       1627
Swap:         3223          0       3223
gator@gator:~$ 

```

I do have the gnome-system monitor running and I cant see how to output the data from it to post here.
Here is the output from Htop:
```

  1  [||||||||||||||||||||||                                                   27.4%]     Tasks: 167 total, 1 running
  2  [||||||||||||||||||                                                       21.4%]     Load average: 0.27 0.56 0.59 
  Mem[||||||||||||||||||||||||||||||||||||||||||||                        387/2013MB]     Uptime: 02:09:47
  Swp[                                                                      0/3223MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command                                                                                                           
 2767 root      20   0  407M 74492 13540 S 30.0  3.6 22:16.31 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7                                    
 6435 gator     20   0 31236 19352 13864 S  8.0  0.9  0:28.63 gnome-system-monitor
 3298 gator     20   0 22488 13388  8944 S  3.0  0.6  0:19.81 metacity
 6439 gator     20   0 34808 15336  9636 S  2.0  0.7  0:01.31 gnome-terminal
 6577 gator     20   0  2608  1348   964 R  1.0  0.1  0:00.32 htop
 6205 gator     20   0  243M 85016 29824 S  1.0  4.1  1:03.57 /usr/lib/firefox-3.0.14/firefox
 3299 gator     20   0 47624 31688 13948 S  0.0  1.5  0:13.46 gnome-panel
 3382 gator     20   0 16640  3012  1804 S  0.0  0.1  0:08.65 gnome-screensaver
    1 root      20   0  3084  1888   564 S  0.0  0.1  0:01.22 /sbin/init
  870 root      16  -4  2224   580   316 S  0.0  0.0  0:00.18 /sbin/udevd --daemon
 2230 root      20   0  1808   532   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty4
 2231 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty5
 2234 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty2
 2237 root      20   0  1808   532   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty3
 2238 root      20   0  1808   528   460 S  0.0  0.0  0:00.00 /sbin/getty 38400 tty6
 2310 root      20   0  2204  1080   556 S  0.0  0.1  0:00.00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 2355 syslog    20   0  2040   700   540 S  0.0  0.0  0:00.06 /sbin/syslogd -u syslog
 2378 root      20   0  1968   536   440 S  0.0  0.0  0:00.06 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 2380 klog      20   0  4376  3088   444 S  0.0  0.1  0:00.16 /sbin/klogd -P /var/run/klogd/kmsg
 2403 messageb  20   0  3124  1428   832 S  0.0  0.1  0:00.56 /bin/dbus-daemon --system
 2533 root      20   0 10600  1448   900 S  0.0  0.1  0:00.00 /usr/sbin/winbindd
 2555 root      20   0 10600  1200   652 S  0.0  0.1  0:00.00 /usr/sbin/winbindd
 2556 haldaemo  20   0  6676  4716  3920 S  0.0  0.2  0:00.74 /usr/sbin/hald
 2559 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.16 /usr/sbin/console-kit-daemon
 2560 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2561 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2562 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2563 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2564 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2565 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2566 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2568 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2569 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2570 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2571 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2572 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2573 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2574 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2575 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2576 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2577 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2578 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
 2579 root      20   0 17448  2628  1792 S  0.0  0.1  0:00.00 /usr/sbin/console-kit-daemon
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

```

Right now it seems to come and go.

---

### Post by blackened on 2009-09-24
The formatting will look much better if you surround the pasted info with CODE tags (the # in the toolbar of the advanced editor).

Did you already tweak the swappiness settings as mikewhatever suggested? That would probably be the best place to start.

---

### Post by mikewhatever on 2009-09-24
With 900MB of RAM being free, I don't see how that is a memory problem. The only resource hog in htop is this process (using 30% CPU):
```
 2767 root      20   0  407M 74492 13540 S 30.0  3.6 22:16.31 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7                                    
```

---

### Post by gatordude on 2009-09-24
OK Thanks for the info and suggestions. I will try and answer everything.

1. I dont have desktop effects running ([thats one of my problems I am having]("http://ubuntuforums.org/showthread.php?p=8002255#post8002255")) and I didnt install Compiz until last night.
2. I am not familiar with CODE tags ( I will give that a shot next time I post, sorry guys)
3. Yes I have to reboot, I tried to log off and then back on and that doesnt help (starting to sound like a  possible hardware issue) Is there a monitor tool that will show the temp of the processor and video card and hard drive??
4. I thought mikewhatever said he didnt think the swappiness was an issue but to keep an eye on it.
5. I am not sure what the process is that was running that mikewhatever said was the hog.

Thanks again for the help.

---

### Post by gatordude on 2010-03-21
OK,

So the machine I was running Ubuntu on has died and been replaced.

After getting the new machine loaded with all of the software I use I was having stability issues. (still have an issue with my external USB drives becoming unmounted but I am still looking into that issue)

The stability issue I had may have been a result of Fire Fox and or System Monitor (the monitor was loaded into the panel and running). The memory issue I thought I had may have actually been caused by this. I installed a new browser (Chrome) and removed the System monitor and I have been using (over using actually) as many applications at once and have not had an issue for over 8 hours.

Just wanted to post this if any body else is having similar issues.

---

