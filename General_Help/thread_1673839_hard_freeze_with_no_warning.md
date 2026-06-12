---
title: "hard freeze with no warning"
date: 2011-01-23
forum: General Help
---

### Post by wildbillnj1975 on 2011-01-23
I'm running 8.10 on a box that had been shelved for a while (blown capacitors on the mobo and I didn't have cash/time to replace & fix).  Now it has brand new mobo, CPU and memory.

Occasionally, without warning, the box freezes up hard, as though it has some kind of intermittent hardware issue.  I doubt it's any of the new components, but anything is possible.  When I say "freezes", I mean it goes into total catatonic mode - mouse pointer doesn't move, key presses have no effect, clock stops running, etc.

When the system freezes up like this, the only thing I can do is hit the reset button (it doesn't even respond to things like ctrl-alt-delete).

Where should I look for info that would help me diagnose the cause of the problem?  I've tried saving some log info by tracking the dmesg log in a local file, but nothing in it looks suspicious.

Oh, here are the specs:

Gigabyte M68MT-D3 motherboard (has nVidia video adapter built in, and also ethernet)
AMD Sempron 140 (2.7 GHz) CPU
1 GB of memory
(all new)

SATA DVD-RW (new)
Sabrent PCI IDE adapter (also new)
3 IDE drives, one of which is divided into /, /boot, /home and swap partitions.
1 "standard" internal 3.5" floppy drive

---

### Post by wildbillnj1975 on 2011-01-23
Here's the latest output from dmesg, which was almost immediately before the last crash.  I trimmed it down to comply with the forum limit - this is the latest portion.

---

### Post by wildbillnj1975 on 2011-01-24
Another symptom I've noticed: very high system load average - it's at ***9.31*** now.  Can't check output of *ps *because I can't start a terminal in Gnome. Dropped back to tty with ctrl-alt-F1, and I can't login - not coming back with a password prompt.  Can't get in via rlogin/telnet; I would set up ssh (for next time) but I don't see how it would be any different, if I can't start a new process.  If I could **get **a prompt, I doubt I would be able to run *ps *anyway.

---

### Post by wildbillnj1975 on 2011-01-26
More analysis...wish I weren't the only one replying on this thread.

So, now I'm tracking /var/log/kern.log, /var/log/Xorg.0.log, dmesg and ps.  I've run through this four times so far.  The system has been idle during this testing except for my logging scripts.

Shortest time up: 7 hours 12 minutes
Longest time up: 14 hours 55 minutes

Seems to be running out of memory, and very abruptly.  The scripts stop working (ostensibly when they can no longer spawn new subprocesses) long before the machine totally crashes.  However, the last time the scripts are able to run, memory usage is only about 40%-45% and no process is using more than 2%-3% of memory.  I was just able to view 3-hour-old logs via HTTP from another machine, that I was not able to view via *vi* or even *more* on the box, because the httpd process was already running.

I modified my scripts for kern.log and Xorg.0.log to just "tail" them rather than periodically checking them for new lines.  Hopefully that will capture messages that occur after the system hits no-new-process critical mass.

---

### Post by Rasputin69 on 2011-01-26
This happened to me after I updated the system.

I was told to reinstall and not use updates.

I did that and the system has not failed since.

---

### Post by pl@yer on 2011-01-26
Seems like it could be a buggy driver/module or wrong driver loaded for existing hardware.
Since you changed hardware, have you made sure you have the correct kernel and modules loaded?

If you changed video cards then I would run 
```

sudo dpkg-reconfigure xserver-xorg

```

Couldn't hurt to run memtest if you haven't already.

Some reading for you.
[http://arstechnica.com/civis/viewtopic.php?f=16&t=157629](http://arstechnica.com/civis/viewtopic.php?f=16&t=157629)

---

### Post by Jouke74 on 2011-01-26
This is Memtest material. Random crashes are often caused by memoery problems, or problems with the memory settings on the motherboard (BIOS). Start Memtest, if it shows errors or crashes also with this test, then it is likely a memory problem.

---

### Post by wildbillnj1975 on 2011-01-26
I ran memtest first; it went through two complete passes with no errors.
What's weird to me is that it happens after hours of idle time.  Literally nothing is going on with the machine, and then boom, no more memory.

I'll try the reconfigure thing and see what happens.

---

### Post by pl@yer on 2011-01-26
The way I understand it (from the googling I just did) is changes to the kernel might not work properly with some modules?

device_set_wakeup_enable can now sleep. 
If a module is coded to not release a spinlock on an irq before sleeping or the module called device_set_wakeup_enable() under spinlocks. 

[http://us.generation-nt.com/answer/2-6-37-rc1-patch-r8169-fix-sleeping-while-holding-spinlock-help-200899551.html](http://us.generation-nt.com/answer/2-6-37-rc1-patch-r8169-fix-sleeping-while-holding-spinlock-help-200899551.html)

What kind of NIC card do you have?
```

sudo lspci|grep net

```

---

### Post by wildbillnj1975 on 2011-01-26
Oh, I should have mentioned, I'm using the xforcevesa kernel boot option, because xorg doesn't like the video card - it doesn't let me set up a resolution greater than 800x600.  With xforcevesa, it has no problem with 1024x768.  So I don't know if reconfiguring xorg did anything useful or not.  We'll see.  I'm running it without xforcevesa now, after the reconfigure, and we'll see what happens.

I REALLY don't want to run at 800x600, and it's not just for asthetics - lots of things don't work right, e.g. Gnome windows and dialogs that are larger than 600 high and you can't get to all the stuff on the window.  Usually the Ok/Cancel buttons are at the bottom, and there have been cases where I just hit enter/escape and hoped for the best.

---

### Post by wildbillnj1975 on 2011-01-26
NIC:

00:08.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

It's built-in on the motherboard.
If you think it would make a difference, I can disable it in the BIOS and install an older Netgear NIC that was working fine for a long time before I replaced the mobo.

---

### Post by wildbillnj1975 on 2011-01-26
On that spinlock/irq isue, how would I even know if that's related to my problem?

We're kind of shotgun debugging here.  What I'd really like to do is to find a way to capture what's going on with the machine right when it blows up.

Hmm...just thought of something...the reason I'm tracking all those logs in a script is because they all get wiped when the machine reboots.  Next time around, I think I'll boot off a live CD first, and see what remnants are in /var/log that I wasn't able to capture due to not being able to start any new processes.

---

### Post by pl@yer on 2011-01-26
I don't know that the spinlock is part of the problem, just saw it in you dmesg output.

I think if it was me, I would use a live cd for a day first. If it locks up there, I would start trouble shooting/"swapping out" hardware.  
 
It is nicer to try one thing at a time, but the time between failures is quite high so I think shotgun is apropriate :)

---

### Post by wildbillnj1975 on 2011-01-27
Another day, another attempt...booted with 8.10 desktop live cd.  Nothing interesting in the logs from crash around 4am.  Load average was around 11.4 this time.  Should note that it's not memory - the gdm System Monitor widget was showing 21% in use by programs, 68% in use as cache.  Looks like cpu is thrashing on something.

Will let it run with the live cd and see what happens.  Also, if it does crash, I'll run something in the terminal window (e.g. uptime) and wait a while to see if it *ever* comes back.  What I've seen so far is that it goes into lalaland as soon as I hit <enter> but maybe it would eventually run.

---

### Post by pl@yer on 2011-01-27
If you suspect it is CPU. This command will give you top 3 CPU hogging processes.
```

ps -auxf | sort -nr -k 3 | head -3

```
I had run it like so on a system to find out what process was pinning the cpu.
```

ps -auxf --headers| head -1>./proc_cpu.txt;until [ 1 -eq 2 ]; do ps -auxf | sort -nr -k 3 | head -3>>./proc_cpu.txt;sleep 30;date>>./proc_cpu.txt;done

```

I still think I would use the live system to attempt to isolate it to hardware/software.

---

### Post by wildbillnj1975 on 2011-01-27
I wonder if there's any way to do that *without* looping and re-running ps...
The problem is, by the time the machine *starts* having the problem, it won't start any new processes, so the loop will come around to "ps" and it just won't do anything at all.

I have a tracking script now, that dumps all the output from ps -alef, but it doesn't reveal anything because it stops running.

Oh wait, that's "top".  Just can't really pipe it out to a log file, so I'll leave it running in an open terminal window.

BTW I've been running off the live cd for about 9 hours, and so far, nothing has happened.  If it hasn't crashed by the 24 hour mark, I'm going to assume all the hardware is fine, and go back to the main kernel and watch top for clues.

---

### Post by pl@yer on 2011-01-27
sound like a good plan.

---

### Post by wildbillnj1975 on 2011-01-29
Ok, gave up waiting for it to die with the live CD, so I rebooted back in my "normal" setup and ran "top" in a terminal window.  I wasn't able to check it *during* the "about to lockup" period, but I still gathered some interesting info.

I checked the box and it's all locked up.  Would have made a nice screenshot, if I could have taken one.  Here's what I could see in the top window that was frozen in time:

The load averages were 11.27, 9.63, 9.20.  So, it clearly wasn't instantaneous - it was in serious thrash mode for at least 15 minutes before it went flatline.

There were 191 processes, and the only one showing as "running" was top itself.

The good stuff is in the CPU and memory info.  Memory shows:

903992k total
896576k used (99.2%)
7416k free
160k buffers

I had previously thought memory usage wasn't high, but that was probably just because the monitoring tool couldn't capture it accurately.  But it does show essentially 1GB, backing up my memtest results that the memory is functioning OK.

CPU:
  0.6% us
  2.8% sy
  0.0% ni
  0.0% id
 93.6% wa
  0.8% hi
  2.2% si
  0.0% st

So, the CPU is 93.6% busy in IOWAIT.

Anybody know if there's a way to track which processes are in IOWAIT?  I know I can do "ps -aux |grep D" but once the problem starts happening, *ps* won't run anyway.  Is it possible to make *top* show only processes in ***D*** state?

---

### Post by wildbillnj1975 on 2011-01-30
So, in *top*, I have it sorted by process state, and the "D" processes are first in the list.  At the time when it froze, they are:

[LIST]
[*]krcupreemptd
[*]kswapd0
[*][COLOR="Silver"]chkmsg[/COLOR]
[*]cron
[*]polkit-read-auth*something-off-the-screen*
[*][COLOR="Silver"]mkdir[/COLOR]
[*][COLOR="Silver"]tail[/COLOR]
[*]scsi_eh_2
[*]kjournald
[*]hald
[*][COLOR="Silver"]gnome-terminal[/COLOR]
[*][COLOR="Silver"]iostat[/COLOR]
[/LIST]

I greyed-out the ones that are obviously not the culprits.  I need to check the cron and see what could be running that would be doing tail/mkdir - I think it's just one of my monitoring scripts (probably "chkmsg"), which didn't exist until after this problem started happening, so I doubt they're responsible for the problem.

I can try changing the filesystems from ext3 to ext2, which would avoid running kjournald, and see what happens.

Any other suggestions?
I wasn't able to catch it *while* it was starting to crash, so I couldn't flip to the other window with *iostat* to see which disk was busy in IO.

---

### Post by Jouke74 on 2011-01-31
Hmm. Maybe your harddisk is broken? It won't be used when running the live CD and it is related to the errors you indicated in yourt previous post.

---

### Post by pl@yer on 2011-01-31
% memory usage is almost useless for linux/unix systems since they tend to use all RAM available for disk and device caching. Paging is what I would look at for memory load. I like using nmon to show page faults. 

What about looking for errors in the previous dmesg logs.

```

zcat /var/log/dmesg.*.gz |grep -i error

```

iotop is nice for showing io intensive processes. Have you fsck on the drive while in live mode?

---

### Post by wildbillnj1975 on 2011-02-02
I have to wonder if there is something wrong with the disk, because after the last crash (Sunday) it won't boot, and it doesn't find ANY partitions on that drive.  gparted can't see any partitions, neither can testdisk.  Now I'm looking for ways to re-create the partition table without losing the data, in hopes of recovering the stuff on that disk.

---

### Post by pl@yer on 2011-02-02
I have had good luck recovering data with dd. Never tried recreating partitions or anything on the damaged drive (I prefer not to try writing to it at all).
 What I have done in the past was to have a disk larger than the total size of the damaged drive (or use skip and count). Then using dd make and image of the disk. 
(if hda was the bad disk and sdb1 is the a big partition on the new disk.)
```

# dd if=/dev/hda conv=sync,noerror of=/dev/sdb1/hdaimg.iso

```
then you can mount the image as a loop back device.
```

# mkdir /mnt/imgloop
# mount -o loop /mnt/sdb1/hdaimg.iso /mnt/imgloop
# ls /mnt/imgloop

```
At this point you should be able to copy data out of the image.

---

