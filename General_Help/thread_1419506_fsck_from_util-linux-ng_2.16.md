---
title: "fsck from util-linux-ng 2.16"
date: 2010-03-01
forum: General Help
---

### Post by Vevmesteren on 2010-03-01
The setup, a quadcore processor, four GB of ram and a lot of free hard drive space. 

I am not sure what was updated on my Ubuntu box yesterday, as a matter of fact, I don't think there even was an update. 

But when I try to boot up Karmic (64bit) today things stop at:
```

fsck from util-linux-ng 2.16
/dev/sda5 : clean, 164345/6291456 files, 1533006/25143725 blocks

```

I booted the live CD ran the same fcsk and all was fine, the scan goes through, tells me all is clean. 

Help? I am Ubuntuless and clueless? What is going on? 
I am seeing that I am not the only one having this issue (people have been having it since last year) but I have not found any solution (except reinstalling everything, which I do not really feel like doing - unless I really really have too) there must be something. Is there another disk utility I can try from the LiveCD?

the machine as such does not freeze I can ctr-alt-delete myself into reboot but then the error comes again, both in recovery and full mode. I don't want to boot up XP, please tell me it ain't so. Please tell me I can salvage this installation.

The numbers before the slash vary from try to try...

thanks

---

### Post by mike2357 on 2010-03-02
Similar behavior for me, except that the fsck process aborted and exited to a shell prompt.  My configuration is a dual core processor with 4 GB of memory and a 230 GB hard drive.  I'm running Ubuntu 9.10, 64-bit version.  I could only advance to the regular login menu by pressing the escape key several times while fsck was running, before it exited to the shell prompt.  I could then update my backup files from the weekly one I did two days ago and reinstall Ubuntu.  Does anyone have any ideas as to the cause and how to rectify?  I won't be running fsck until I understand how to make this not happen.

Thanks much.

---

### Post by dert on 2010-03-26
Hey guys.  This bug zapped me too.  I was unable to find a fix for it so I just nuked my drive and started all over again.  Fortunately my drive is brand new and was only 4 hours old when it died with your exact same symptom.  I'm very new to linux so I was unable to fix it, even with all the great suggestions here.

Launchpad Bug Report 548601 filed to have this addressed.

Oh, in the meantime, do try to fix it with

```
sudo fsck -y /dev/sda[your partition number]
``` 

That may very well kill your installation too come to think of it, but since you're where I was...couldn't hurt!  (didn't do diddly for me unfortunately)

---

### Post by ImNotAGeekReally on 2010-09-30
I've just had a similar problem on Ubuntu Server 10.04 LTS.  When you're at that screen, the ESC button is your friend.  Press it as soon as you get to the screen, and it'll sail straight onto the login screen.

[http://www.webupd8.org/2009/05/how-to-change-periodic-disk-check-in.html](http://www.webupd8.org/2009/05/how-to-change-periodic-disk-check-in.html) - I'm thinking about disabling the disk consistency check (well, set it to check every 12 months or so).  Does anyone know any drawbacks to this?  I'm using that machine as a Dev server, so it usually stays on all the time.

---

