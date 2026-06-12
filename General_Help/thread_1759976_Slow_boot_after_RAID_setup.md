---
title: "Slow boot after RAID setup"
date: 2011-05-16
forum: General Help
---

### Post by root45 on 2011-05-16
I've just finished setting up a RAID 1 on my system. Everything seems to be okay, but I have a very slow boot time. It takes about three minutes between the time I select Ubuntu from GRUB and the time I get to the login screen.

I found this really neat program called bootchart which graphically displays your boot process.

[This is my first boot]("http://i.imgur.com/GhaYt.png") (after installing bootchart). I'm not an expert at reading these, but it appears there are two things holding up the boot, cdrom_id and md_0_resync. I tried unplugging my CD drive SATA cable, and [this is the new boot image.]("http://i.imgur.com/FUCwg.png")

It's faster, but it still takes about a minute, which seems pretty slow on this system. The md0 RAID device is my main filesystem. Is it true that it needs to get resynced on each boot?

I'm not sure how to diagnose my CD drive issue. The model is a NEC ND-3550A DVD RW drive. I should also note that there's a quick error message at startup about the CD rom. It's too quick for me to read it, just one line on a black screen saying "error: cdrom something something".

I'm not sure what other information to include. Thanks for any help.

---

### Post by lithopsian on 2011-05-17
Looks fine to me.  With the SATA cable disconnected!  You say it takes a minute to the login, but I only see 20 seconds.

I don't know what is going on in that first chart.  What happened for the first minute?  Is it trying to boot from the CD drive?  Shouldn't be since bootchart is already started.  Weird.

Are you sure there is something wrong with the resync process?  Isn't that normal?  I don't know because I don't have RAID.  Aren't you still logged in after 20 seconds even though that process keeps going?

---

### Post by root45 on 2011-05-17
Right, well 20 seconds is what boot chart says, but from GRUB menu to login screen it's more like 50 or 55 seconds. I imagine there are some things bootchart doesn't measure at the start and end of the boot process, but I could be wrong about that. I'm really not sure.

The resync issue is resolved. I just didn't realize how long it would take to resync my drives after the initial setup. But now it's finished, so that doesn't even appear in new bootcharts.

As for the CD-ROM issue, it seems that several people have this issue, although it's by no means common. I noticed you posted here,

[http://ubuntuforums.org/showthread.php?p=10828785#post10828785](http://ubuntuforums.org/showthread.php?p=10828785#post10828785)

which seems to be very similar. These two threads have a similar problem, but are much older

[http://ubuntuforums.org/showthread.php?t=459615](http://ubuntuforums.org/showthread.php?t=459615)

[http://www.linuxquestions.org/questions/linux-hardware-18/boot-hangs-uniform-cd-rom-driver-revision-3-20-a-570922/](http://www.linuxquestions.org/questions/linux-hardware-18/boot-hangs-uniform-cd-rom-driver-revision-3-20-a-570922/)

I also have an error in my dmesg saying

sr0: CDROM (ioctl) error, command: Xdread, Read track info 52...
which came up in these threads

[http://ubuntuforums.org/showthread.php?t=485597](http://ubuntuforums.org/showthread.php?t=485597)

[http://ubuntuforums.org/showthread.php?t=1523547](http://ubuntuforums.org/showthread.php?t=1523547)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/544952)

which are about not being able to decrypt DVDs. That's another issue I'm having that might be related.

Unfortunately, NO one seems to know the answer to the problem. People either gave up entirely, or it went away when they did a system upgrade. I don't suppose you have any ideas on what to do?

---

### Post by lithopsian on 2011-05-17
> **root45 said:**
> Right, well 20 seconds is what boot chart says, but from GRUB menu to login screen it's more like 50 or 55 seconds. I imagine there are some things bootchart doesn't measure at the start and end of the boot process, but I could be wrong about that. I'm really not sure.
bootchart should start no more than a second or two after Grub decides to boot Ubuntu.  Anything major is a problem.  bootchart finishes at a rather arbitrary time which can be before or after the login screen.  This is after the last bootscript finishes.  The login screen is spawned by a boot script several steps earlier but often the remaining boot scripts will complete before it appears.  Desktop autostart scripts may continue to run for a long time after that, starting userspace apps.  Sometimes bootchart will decide something is seriously wrong and finish anyway so it doesn't last forever.

On your bootchart, unless something serious is wrong with your login process, the point where the login screen appears is at about 20s on the chart.  Look at the job called gdm-simple-greeter, that is your login and it should either throw a dialog almost instantly or automatically log you in in a fraction of a second, unless you have configured a delay.

---

### Post by root45 on 2011-05-17
Well in that case I guess I'm just confused. [Here's my most recent boot.]("http://i.imgur.com/VG0fS.png")

Bootchart says it took 120 seconds, but I timed it with a stopwatch from the moment I left the GRUB menu to the moment the login screen appeared. It took 3 minutes and 3 seconds. So there's certainly some sort of discrepancy.

This time the things that seemed to hold it up were not only cdrom_id, but also ata_id and blkid. I don't know what those are, really, but I'd like to figure out why it's taking so long.

---

### Post by lithopsian on 2011-05-18
I think your bootchart program gave up after 2 minutes   I don't see your desktop starting at all within that time, presumably another minute later.

Still, that is seriously messed up.  Your hardware is not getting detected right.  bootchart is not the place to diagnose this.  You know that udev is hanging forever detecting your devices, so you need to work on that.  Also, what is it doing for the first 55s?  Maybe dmesg will give you some clues about that.

---

