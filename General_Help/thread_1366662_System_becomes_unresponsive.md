---
title: "System becomes unresponsive"
date: 2009-12-28
forum: General Help
---

### Post by PH5 on 2009-12-28
Hey Everybody.  I've got a problem I can't figure out.  I'm running 64-bit Ubuntu 9.04 on an AMD Athlon 64 X2 5400+ with 2GB ram.  I've been having seemingly random problems where the machine stops responding to input.  I can move the mouse pointer and click on buttons, and they toggle, but the applications don't respond.  I can click on the applications menu, for example, and try to run new apps, but nothing happens.  Likewise, I try to reboot the machine from the menu, and nothing happens.  I've had this problem happen a couple of times a day, forcing me to do a hard reboot, or it may not do it at all for a week.

I have had the System Monitor open for the past few days to try to catch some indicator of what is going on.  I finally managed to catch sight of something odd on the Resource monitor.  It's a dual core CPU, and one of the cores stops competely when this happens.  It drops to zero percent and stays there.  If I wait long enough, sometimes the machine comes alive again, and the CPU resumes functioning.

It seems to me that something is blocking the CPU from running.  I've checked the temperatures and they are quite cool, so I don't think it is a heat issue.  I've checked some of the logs, but nothing is showing up that I have noticed.  However, I am still something of a linux noob and may not know where to look, though I have a lot of pc experience.

Does anybody have any ideas on how to track this down?  It's kinda hard since I can't make it do anything when it is acting up, and I can't reproduce the problem.  As far as I can tell, it isn't any specific application that I am running that is causing it, but I wouldn't rule it out yet.

Any help is appreciated!

Thanks,
PH

---

### Post by gsmanners on 2009-12-28
Sounds to me like the hard drive is having some issues. That's the typical behavior when a drive or drive interface is starting to go bad. It could be a bad file system, though. You could check it with fsck.

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by PH5 on 2009-12-28
I ran the test as you suggested, and both of my drives came up clean.  Other ideas?

---

### Post by gsmanners on 2009-12-29
If it isn't the hard drive, I really don't know. It could just be the drive gets a sudden spike of activity or it decides to park every now and then.

---

