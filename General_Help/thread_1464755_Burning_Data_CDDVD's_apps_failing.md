---
title: "Burning Data CD/DVD's apps failing"
date: 2010-04-28
forum: General Help
---

### Post by held7over on 2010-04-28
Ubuntu 9.10 Gnome  I am having a terrible time burning data dvds or cds. I am getting way too much stuff that needs backed up to DVD on my system. But one after another, different burning apps are not working on my system. Below I have listed 3 apps and the errors they are reporting. Does anyone have a suggestion? Is this just happening to me?  Thanks! 

**K3b** has always been my choice of burner. And while it still works to burn .iso images, our present version on Ubunut has a bug that keeps me from using it to burn data cds or dvds...since Ubuntu 9.04  (Which also ruins the blank DVD. The bug description here [http://bugs.kde.org/show_bug.cgi?id=204333](http://bugs.kde.org/show_bug.cgi?id=204333)  which says CdRecord doesn't have permission to access the cdrom device)

**Gnomebaker** now gives me this following error 3 seconds after hitting the burn button: 

Executing 'genisoimage -gui -V GnomeBaker data disk -A GnomeBaker -p lucky -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-lucky/gnomebaker-KK4LBV | builtin_dd of=/dev/sr1 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/sr1: "Current Write Speed" is 2.4x1352KBps.
:-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
:-( write failed: Input/output error
(This error does not ruin the blank DVD.)


**Nautilus's CD/DVD Creator**, when it starts burning or somewhere in the middle of the burn process, stops and announces:   Error while burning. An unknown error occurred. (Of course, at this point, my blank DVD is ruined.)

---

### Post by ajgreeny on 2010-04-28
Have you tried brasero?  Or is that what is used when you attempt to use the **Nautilus's CD/DVD Creator? ** I have never tried that so am unaware what is actually used to do the burning.

---

### Post by held7over on 2010-04-28
Brasero gives me the same error as Nautilus's CD/DVD Creator (Error while burning. An unknown error occurred.) except it waits until after the checksum calculating is over......so maybe they are related.

---

### Post by Leppie on 2010-04-28
is the checksum of the burned dvd the same of as the checksum of the source files?
in other words, have you checked if the files on the dvd are usable when brasero has finished?

---

### Post by held7over on 2010-04-28
The raw data is good. But on that premise, I have switched to other data to burn to cd or dvd and had the same errors.

There aren't any files burned onto the DVD when brasero errors out. I can eject the DVD, and then insert it, and it shows up on my desktop as a blank DVD. If I double click on it, Nautilus's CD/DVD Creator pops up and wants to know what files I want to burn to it...


Now, in the process of trying the other apps, which most of the time just error out in the burn, I have seen a couple error out after the burn in the finishing phase....and those did have files on them, I just didn't know whether to believe they were OK or not. But that was far and few between!

---

### Post by trig on 2010-04-28
Is your burner a samsung writescribe? Mine has similas issues.

---

### Post by held7over on 2010-04-28
trig.  It has been a long time since I installed my burner. It has worked perfectly for years, up to now. I confess, I forgot what brand and model it is. On Mandriva, I know exactly were to go pull up the hardware parts in the Harddrake GUI. But on Ubuntu, I am at a loss as to where this is at. Would you mind telling me what app or command does this?

---

### Post by mc4man on 2010-04-28
> command does this? 
```
sudo lshw -C disk
```

The only gui burning app in linux I'd consider is k3b ( but I don't - imgburn in wine, no comparison

---

### Post by held7over on 2010-04-28
I guess I should emphasize my burner has no problem burning .iso files using K3b, so it seems to me to be unlikely there would be anything physically wrong with my burner.

---

### Post by held7over on 2010-04-28
trig:  I used the dmesg command and dug through all the stuff before I discovered mc4man' suggestion, which by the way was a pretty neat command! (I'm putting it in my cheatsheet notes.)

 I have a **NEC DVD_RW ND-2500A** burner.

---

### Post by held7over on 2010-04-28
I am hoping ubuntu 10.04 will have K3b version 1.69 in which I think the K3b bug is fixed.

---

### Post by mc4man on 2010-04-29
> I am hoping ubuntu 10.04 will have K3b version 1.69 in which..
checking on my lucid install it has 1.91 - so hopefully you're ok (a bit of a jump

(if you still can't then the prog I mentioned will most likely work flawlessly.

---

### Post by held7over on 2010-04-29
k3b v1.91? WOW! That is more than I had hoped for!

---

### Post by held7over on 2010-05-08
mc4man.  10.04 looks great, but K3b now burns the entire data DVD, but in the final FLUSH of Cache, it stops and gives "write error". If I remount the dvd, the OS recognizes it as a burned dvd and opens it. I can see all the files. However, while the first half of the dvd.s data is readable, the last half of the files will not open. Ugh!

Are you having this problem with K3b?

Also, upon my first try, K3b wanted me to point it at a "burning" group. I pointed it at the "cdrom" group and clicked OK. It didn't ask me for a password, which seems strange, but it no longer complained about this issue.

I have never ran wine and it seems amazing to me that I would have to run a M$ program to just burn data dvd's on a linux machine! I guess I will first go back and retry the other linux burner progs and see if any of those are working now on 10.04.

Am I the only person this is happening with? If so, maybe my burner really is malfunctioning. This just blows me away.

---

