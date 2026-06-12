---
title: "Virtual Box Install"
date: 2011-09-27
forum: General Help
---

### Post by OldManRiver on 2011-09-27
All,

Trying to get WinXP installed under Virtual Box on 2 desktops and a laptop.

Keep running into problems.  Wrote it up on VBox forum at:

[https://forums.virtualbox.org/viewtopic.php?f=7&t=44765&p=202378#p202378](https://forums.virtualbox.org/viewtopic.php?f=7&t=44765&p=202378#p202378)

but not getting any help.

Please let me know if you have encountered the aborts after the WinXP formats, especially how you got around them.

Thanks!

OMR

---

### Post by collisionystm on 2011-09-27
Still sounds like a potential .iso problem. 

Try alcohol 120% to copy your disks.

---

### Post by OldManRiver on 2011-09-27
All,

Been reading and it appears the recommended Virtue Box version for Ubuntu is VBox OSE.  I think I just installed via synaptic, so not sure what version I have.

Also when the session abort happens, the session containers, where the min, max, close buttons are disappear, so no sessions are movable, and then 4-6 Untitled Sessions appear in the panel status bar.

I can not execute the "Alt"+"Ctl"+"BckSpc" to restart XWin, so have to reboot each time to clear this.

I saw the comment about my .iso, but if you read the link to the VBox forum, you would know I have done this several times before with only the ability to actually boot my CD image, as change.  I even have 6 different XP sources and .iso's to pick from and all are acting the same.

Thanks!

OMR

---

### Post by collisionystm on 2011-09-27
Don't use Virtualbox OSE anymore. It really isn't supported much. Grab the official from their website. It is much better. [https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by Habitual on 2011-09-27
4.1.x from [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox) runs WinTendoXP just fine.

YMMV on Ubuntu.

NOTE: grab [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)
while you're there.

HTH.

---

### Post by OldManRiver on 2011-09-28
All,

All the re-gens of .iso imanges have failed.  I tried changing the default RAM to 1GB and the disk space out to 80GB but no change.  Need a way to debug this, as the .iso image works on any machine in "boot from power up" mode.

Still scratching my head.

Thanks!

OMR

---

### Post by coldraven on 2011-09-28
You can add VirtualBox to your repositories and you will always get the latest version.
I have vers. 4.1.2 r73507 at the moment.
This is the line in my Synaptic Software Sources list.
```
http://download.virtualbox.org/virtualbox/debian maverick contrib 
```
I did not get any errors installing XP from an OEM restore disc.

---

### Post by OldManRiver on 2011-10-19
All,

Wondering if I need a new "factory" disk to make this work?  Also since XP is discontinued, how do I now get a disk?

OMR

---

### Post by KingYaba on 2011-10-19
> **OldManRiver said:**
> All,

Wondering if I need a new "factory" disk to make this work?  Also since XP is discontinued, how do I now get a disk?

OMR

I know Amazon still sells Windows XP, if you're interested, but that's a high price to pay just to use Win XP in Virtualbox. If you're a college student then you may be in luck since student discounts lob the price off by a lot. Anyway, if you're buying Windows why not consider Win7? Unless your computer isn't compatible.

---

### Post by OldManRiver on 2011-11-17
> **Habitual said:**
> 4.1.x from [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#vbox) runs WinTendoXP just fine.


HTH,

What is WinTendoXP?

All,

Seems the problem is computer specific for the following reasons:
[LIST]
[*]Tried with CD burnt with Magic ISO - failed,
[*]Tried with CD burnt with Nero - failed,
[*]Tried with CD burnt with Roxio - failed,
[*]Changed VBox from 4.1 to 3.2 - all 3 above failed,
[*]Loaded CD burnt with Roxio to my main UBox PC - installed,
[*]Loaded CD burnt with Nero to my main UBox PC - installed,
[*]Loaded CD burnt with Magic ISO to my main UBox PC - installed,
[/LIST]

Target machine that is failing is a Gateway 819GM Desktop.  Wondering is Gateway, like Dell needs a "keyed" XP copy?

Got to be something like that keeping me out.

Thanks!

OMR

---

### Post by CharlesA on 2011-11-17
I presume it is slang for Windows XP. :roll:

If you've got an ISO already, you can just mount the iso in VBox and install from that.

If you are using the recovery cd, I don't think it will install as they check the hardware before installing IIRC.

---

### Post by OldManRiver on 2011-12-07
All,

Tested 3 different copies of the XP .iso on my main U-Box and all installs went in fine, so know it is not the .iso image or the CD media.

Final analysis is; it is something peculiar to the Gateway PC that is keeping the XP from loading.  Not sure what but open to feedback on this.

Have not seen any inputs or ideas on this so guess the sucky Gateway box will not be able to run WinXP after all.  Would like it to, of course, but my friend has another WinXP box, all full of Viruses and the nasties, but that can be cleaned up in time, just wanted him to have a "No Nasties" box that would do his XP stuff.

Thanks for all the help and if you have an answer on this, will leave this thread open for a while, so others can add.

Thanks!

OMR

---

### Post by holycow131415 on 2011-12-07
How much ram does your computer have? From looking at [http://support.gateway.com/s/PC/R/4986/4986sp3.shtml](http://support.gateway.com/s/PC/R/4986/4986sp3.shtml) , default is 512mb, which is hardly enough to run a virtual machine efficiently. It can be up to 4 gbs, which is nice.

Anyway, try to replicate this video tutorial. [http://www.youtube.com/watch?v=BwZzGhZy9lM](http://www.youtube.com/watch?v=BwZzGhZy9lM)

It is an older verison of VB, but it is basically the same.

---

### Post by OldManRiver on 2012-04-02
All,

Closing this thread as "SOLVED", because found it was machine BIOS blocking the install, so quit knocking my brains out!

Cheers!

OMR

---

