---
title: "lucid boot error, open /dev/null failed"
date: 2010-05-11
forum: General Help
---

### Post by aniruddha on 2010-05-11
Hello all,

I have been having this problem for quite some time now. After selecting my os in grub, my screen turns black and I get the following error message:

udevd-work [332] open /dev/null failed no such file or directory

There seem to be a few threads with similar problems. However, I am unable to find a working solution. Any help?

I'm running 64bit Lucid on a Lenovo Ideapad Y530, 2.6.32-22 kernel. I performed a clean install from livecd. I've attached my /etc/fstab as well. Many thanks...

Many thanks.

---

### Post by aniruddha on 2010-05-12
anyone?

---

### Post by aniruddha on 2010-05-14
no one huh? Oh well...

---

### Post by ahendriks on 2010-05-17
I have the same problem here. I have an acer PC (no laptop) and have this message since a few days now...

---

### Post by _0R10N on 2010-05-17
I'm almost sure that I had that message a weeks ago. Despite the message, your system boots fine?

For me, the solution was to update the grub list. I wasn't booting with the last kernel I had installed.

```
upate-grub
```

---

### Post by drs305 on 2010-05-17
Here is a bug report that perhaps applies to your situation. There is speculation but no solid answers. If it applies, subscribe to the bug report.

[https://bugs.launchpad.net/ubuntu/+bug/575333]("https://bugs.launchpad.net/ubuntu/+bug/575333")

Some of the things mentioned in the post (with my inputs on what you can try, not having any idea if they actually cause the problem):
ntfs partition: comment out the Windows listing in fstab
DVD: do you have a DVD in the tray during boot?
Swap: Is the swap UUID correct in fstab. Typing "free -m" would show if you have a working swap.

---

### Post by aniruddha on 2010-05-18
Nope, update-grub doesn't work. I have no dvd in the tray and commenting out windows doesn't seem to work. Thanks for the link to the bug report though. There doesn't seem to be any concrete suggestion as to how to deal with this problem though. It's just really strange.

---

### Post by leoh on 2010-05-25
Same thing over here on a Ubuntu 10.04 64 bits, on a Toshiba laptop.
I always get this error message. The message appears for about 30 seconds, and then it starts normally.

---

### Post by aniruddha on 2010-05-30
Sorry, but has anyone found a way around this?

---

### Post by brigdonnwr on 2010-06-04
Me too! Sometimes the computer fails to start, sometimes it starts normally but always with the 'dev/null failed: no such file or directory'

---

### Post by fabs0000 on 2010-06-11
Hi; 
I get it too, maybe one in four boots.
Not really a problem though, it only appeared for about 5 seconds. I'm curious to find out what is...

10.04 32bit
Thinkpad Dual Core

---

### Post by manolomanolo on 2010-07-15
Same problem here. Updating grub did not solve the problem.

Any suggestion, please? Thanks.

---

### Post by faargenwelsh on 2010-07-22
a new version of GRUB has been released today ; it seems to deal with this problem - or at least it worked in my case.

---

### Post by Elentir on 2010-09-04
I had the message today for the first time. Everything seemed to start normally after I had got the message. I have an Acer 64-bit as well (Acer Aspire X3200). I rebooted after making some changes in my Appearance Preferences.

---

### Post by kretyn on 2010-09-07
And I have the same problem.
I'm running Ubuntu 10.04 on HP Presario CQ60 (laptop) with laptop-mode on.

---

### Post by mpowrie on 2010-09-13
I have the same problem for a few months.

I'm running Ubuntu 64 bit 10.04 on a Dell desktop.
The problem for me started after the update manager automagically updated the kernel.

running 'update-grub' changed the line number that the error appeared on but the problem still exists.

---

### Post by candtalan on 2010-09-21
New install of 10.04.1 and get this error during boot, although otherwise it boots ok.

udevd-work [335]: open /dev/null failed: no such file or directory
 
The error message remains for a few seconds then is not seen. The number associated, [335] for example, is not always this same number.

---

### Post by eveningsky339 on 2010-09-23
Have had this problem since first install of Lucid on this ASUS x83v laptop.  It is no big deal except for the fact that it increases boot time and looks quirky.

From wikipedia:

> In [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") [operating systems]("http://en.wikipedia.org/wiki/Operating_system"), **/dev/null** or **the null device** is a [special file]("http://en.wikipedia.org/wiki/Special_file") that discards all data written to it (but reports that the write operation succeeded) and provides no data to any [process]("http://en.wikipedia.org/wiki/Process_%28computing%29") that reads from it (yielding [EOF]("http://en.wikipedia.org/wiki/End-of-file") immediately).[]("http://en.wikipedia.org/wiki//dev/null#cite_note-uxman-0")

So basically it's a "black hole" to conveniently discard unwanted output.  Supposedly a standard part of the Linux file system, so heaven only knows why it isn't there.  I'll have to check my Ubuntu installation later...

---

### Post by AfterCrash on 2010-10-22
I upgraded from 10.4 to 10.10 .  This is after a reformatted HD and clean install of 10.4. I am now receiving this error:

undevd-work [328] open /dev/nul failed: no such directory    :confused:

My computer will then continue to boot into Ubuntu. Just wanted to show that problem is continuing into 10.10  It wouldn't be a big deal, if it didn't slow my boot process down. One of the reasons I switched to Linux was because windows was slow booting.

---

### Post by chen0rama on 2010-10-24
same problem here, each time I get this error I'm out of the ubuntu skins too

---

### Post by sosaited on 2010-11-01
I got this error today when I enabled ACPI 2.0 in my Bios and reverted another ACPI related setting to a previous setting. Before that a change of an ACPI in bios had caused my Ubuntu 9.10 and 10.04 to connect to the Internet, but I couldn't browse. And XP failed to load at all.

---

### Post by gavin_attoe on 2010-12-31
Edit: I've had variations on this error at startup.  I'm not running a dual boot, just straight-up Ubuntu 10.04, upgraded from a previous version of Ubuntu installed about a year ago.

udevd-work[332]: opening directory /dev/null failed: no such file or directory

to

udevd-work[340]: opening directory /dev/null failed: no such file or directory

and now

udevd-work[349]: opening directory /dev/null failed: no such file or directory

There seem to be a lot of people with this bug, and there's a workaround listed with the bug issue [Bug #575333](https://bugs.launchpad.net/ubuntu/+bug/575333)

I'd still really like to know what causes it - seems to be trying to read from the DVD/CD Rom from what was said about the issue.

---

### Post by radec on 2011-01-13
i'm getting this error now as well. just did a fresh install of 10.10. pretty sure it happened right after added *discard* to */etc/fstab*. not sure if its related and its possible this error was showing before and I just didn't notice it because I hadn't rebooted that many times and it still boots up fine and well under 10seconds.

-rad

---

### Post by mlnease on 2011-02-21
'Reply to Thread' page has no link to 'SOLVED' that I can find.  Seems like it should have, to me.  BIG button, maybe?  I'm not too bright.  

I stopped having this problem when I unplugged my USB external hard drive and camera.

Hope this helps someone.

mike

---

### Post by drs305 on 2011-02-22
> **mlnease said:**
> 'Reply to Thread' page has no link to 'SOLVED' that I can find.  Seems like it should have, to me.  BIG button, maybe?  I'm not too bright.  


Only the original poster can mark a thread solved. It's done via the 'Thread Tools' link at the top right of the first post.

An individual who didn't initiate the thread could alter the title of his/her response by manually adding 'Solved' at the start of the individual post if desired, although it would not be reflected in the thread title.

---

### Post by mlnease on 2011-02-22
Of course, thanks--sorry for my misunderstanding.

---

### Post by drs305 on 2011-02-22
> **mlnease said:**
> Of course, thanks--sorry for my misunderstanding.

No harm in asking. We wish more users would use the "Solved" tag when the issue no longer requires help. It assists others looking for threads with a known solution and allows 'helpers' to concentrate on unresolved problems.

We don't advertise the 'SOLVED' link often enough, so we are happy to bring it to the attention of forumites when asked about it.  :-)

---

### Post by krige on 2011-03-16
I have the same problem under 10.10 64bit on an HP workstation.

* upate-grub didn't solve the problem;

* I don't have a DVD in the tray during boot;

* I don't have any USB external hard drive nor camera during boot;

* free -m  gives the following output:

```
             total       used       free     shared    buffers     cached
Mem:          2000       1349        651          0         54        578
-/+ buffers/cache:        716       1284
Swap:         5860          0       5860
```

---

### Post by krige on 2011-03-16
I have disabled the floppy disk, the serial and parallel ports in the bios (I never use either of them), and the error disappeared.

---

### Post by J@n on 2011-03-27
Kudos to krige:D

Had the same problem and it started to irritate me. I got the udevd-work error after switching from a normal HDD to an SSD (restoring an image).

Turned of serial and parallel in BIOS and presto....error disappeared.

Now my SSD is really showing what it's worth:cool:

Greetz,

J@n

EDIT: Darn....a cold boot resulted in re-appearing of the error. Should have tested that :(

---

### Post by mrnettles on 2011-04-28
I have this error too. Sometimes it appears, sometimes not.

What are serial and parallel ports? Do I need them? And if not, how do I turn them off?

---

### Post by glarrain on 2011-04-28
Damn, I have this issue as well. It won't let me boot at all!

Coincidentally, in my last session I updated some packages, but certainly not the kernel (although i had done it a few days ago). Probably that broke something...

> **mrnettles said:**
> What are serial and parallel ports? Do I need them? And if not, how do I turn them off?

Most probably, no, you won't need them. However, if USB is listed under serial, watch out. You can disable them in the BIOS conf. Depending on your harware, you will have to press a key just after you turn on the PC. Some brands have a dedicated button (e.g. ThinkPad's blue one). F8 or F10 might work.

Good luck

---

### Post by LordNodens on 2011-04-29
> **mrnettles said:**
> I have this error too. Sometimes it appears, sometimes not.

Same here. :mad:

udevd-work[XXX] open /dev/null failed: No such file or directory

---

### Post by porchrat on 2011-07-06
I also experience this. I have been ignoring since I installed Lucid but today I thought I had better look it up. No news on a solution or cause of the issue?

It isn't a big deal I suppose considering the system still boots OK.

---

### Post by Gingalone on 2011-09-12
I had the same boot message but my system booted regularly anyway.
But it was indeed an annoying message and I found that the file /dev/null was there (zero byte) and I changed the owner of that file from root to me and the message 'open /dev/null failed' disappeared at boot time.
It came on again after a while (say after a couple of weeks, maybe after a system update, I don't remember) and I entered chown again and again the rascal message again disappeared.
Ciao.

---

### Post by BentFX on 2011-11-05
> **Gingalone said:**
> I had the same boot message but my system booted regularly anyway.
But it was indeed an annoying message and I found that the file /dev/null was there (zero byte) and I changed the owner of that file from root to me and the message 'open /dev/null failed' disappeared at boot time.
It came on again after a while (say after a couple of weeks, maybe after a system update, I don't remember) and I entered chown again and again the rascal message again disappeared.
Ciao.

Hi Gingalone,

Understand that /dev/null is a dynamic file, meaning udev recreates it, owned by root, on every boot. Also understand that unless you have purposely changed your system to do something suid as you, no boot processes run as your user id.

For most of us, this udev-work error message seems to be a simple annoyance. Linux is "free" as in fredom, but my suggestion would be "careful what your poking at." :)

Back to the topic...

I get the error too. I get it about 1 boot in 5, and the system still seems to boot and operate properly.

Asus G50vt laptop
Ubuntu 9.04 64bit
Kernel 2.6.32-34-preempt though error was present in earlier kernels.
Harddisk is first boot device in bios
USB devices webcam, mouse, 3g modem are always present and still error is only intermittent.

It is highly annoying but the system seems to run fine.

---

### Post by BentFX on 2011-11-05
OK, I've had this issue for a long time, but since it didn't seem to be breaking anything I never pursued it.

Here's my take on what's happening, and how I think I fixed it.

It's udev-work that is popping the error, and if I'm correct it is udev that is responsible for creating /dev/null as a virtual node. If my terminology is correct that would sound like a race condition. One thread is trying to access the file/node before another thread has created it. Normally it works correctly, but sometimes, for whatever reason, things get out of sync and the node isn't ready when requested.

Here's where I messed up my trouble shooting, I deleted /dev/null and recreated it as a static node before I verified that it is actually a virtual node in a stock install.

Using a separate boot partition I've both deleted and created the node then booted into Ubuntu, and boot is fine either way. If /dev/null is missing it is automatically created on boot. If /dev/null exists Ubuntu seems to use it without any complaint.

With the static /dev/null in place I've warm-booted about a dozen times and cold-booted 7 times without any error message.

The thing is with /dev/null created as a static node it should always be ready, as long as the partition is read/write.

I just need someone to boot from a different partition/LiveCD and look at the Ubuntu /dev directory and see if the /dev/null node is there by default(static). My thinking is, that it isn't there by default(virtual). I manually recreated mine to be static before I verified this.

If you enjoy riding the ragged edge, and wish to recreate /dev/null as a static node do...

sudo rm -f /dev/null
sudo mknod /dev/null c 1 3
sudo chmod a+w /dev/null

Since it is an itermittent error, I can't yet claim that this is 'the' fix, but it certainly makes sense to me. At least with /dev/null created as a static node we know that it does exist.

---

### Post by drs305 on 2011-11-05
I haven't checked oneiric, but in my unmounted natty, maverick and lucid partitions */dev/null* exists as a "0 byte character device".

---

### Post by BentFX on 2011-11-06
Thanks drs305,

That's interesting. I don't know just what that means. I've rebooted plenty of times now and the error message hasn't reappeared, yet if the file was there to begin with it would appear I haven't changed anything???

I may I need to rollback my thinking. Two days ago I didn't care. That just might be the best course. :)

---

### Post by P . P . L . on 2011-12-25
Hi.

Add me to the list, i've been getting the same since i updated to 10.04lts

from 8.04lts with a clean install on the same hardware.

The numbers seem to change every boot i've seen [306 , 312, 336] so far, 

never had this with 8.04 it's more annoying then anything but it dose slow 

down boot time a bit.


udevd-work [306] open /dev/null failed no such file or directory

---

### Post by col48 on 2012-03-28
I've been seeing this for about six months (Lucid, various kernels as they have been released, dual boot with Hardy (8.04) but no Windows on the machine, ext3 HD - didn't see it at all initially)

Post #22 contains a link to a Launchpad thread on this (currently unresolved).

Looks like two distinct problems:
(1) some people see the message and then boot fails
(2) most see the message and then (perhaps after a delay) boot carries on normally.

This thread largely seems to be about (2), which is what I have been seeing.

As of about 3-4 weeks ago (kernel release 2-6-32.39?) I no longer see the message on every boot - about 30% miss it; boot time appears to be slightly faster when the message is missed.

I'm no expert, but the tale told by BentFX of a race between threads seems very plausible to me.  One thread has as one of its tasks making /dev/null recognised by the OS and the other (perhaps more than one) needs to use it but presumably gets around the non-availability by ignoring the write commands (surely it is output, not input, here).  Whichever wins the race there is no obstacle to a successful boot.

Perhaps *all* of the "cures" simply change the timings of the boot threads and thus avoid the problem rather than really cure it.  Perhaps the 30% of my boot-ups which avoid the message just have components waking up differently due to varying ambient conditions.  We are, after all, probably talking about milliseconds or microseconds of time difference deciding the outcome of the thread race.

Those who test these things before release (Canonical) may well have set-ups which tend to favour one particular outcome of the race because of all the things they are trying to check out in synchrony, and nobody can test all possible circumstances (otherwise we'd never need any updates on an Ubuntu release!).

---

