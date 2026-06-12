---
title: "Boot Loader Help"
date: 2010-04-15
forum: General Help
---

### Post by wrighty43 on 2010-04-15
Hey

I was wondering if i could have some advice.  I am dual booting Windows 7 and ubuntu and i would like the computer to boot into windows, whilst only accessing the boot loader when a key is pressed in a small space of time before windows is loaded... I know this is possible as my PCs in my lab at my uni have this feature (using GRUB i think).. but i cant find any info on this...

Cheers

---

### Post by oldfred on 2010-04-15
Welcome to the forums.

The instructions are now different depending on whether you have grub legacy (0.97) or grub2 (1.97 or greater).

This is for grub2:
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

A gui way, has more working settings for old grub:
Startup manager (download in synaptic) will allow you to set boot default and the timeout even in lucid.

---

### Post by drs305 on 2010-04-15
Dual system computers provide a bit of a bother for setting it up the way you want. Unfortuately, when Grub2 finds a second Operating System, it doesn't allow the hidden timeout function to operate normally.

You can enable it again by altering the /etc/grub.d/30_os-prober file as described in section 6 of this post:
[http://ubuntuforums.org/showthread.php?t=1287602]("http://ubuntuforums.org/showthread.php?t=1287602")

Once you have made that change, the following sections of /etc/default/grub will hide the menu if set up properly:

> 
GRUB_DEFAULT=0   # Default OS. 0 is usually Ubuntu. Change to the Window menuentry. 
GRUB_HIDDEN_TIMEOUT=3  # How long a blank screen is displayed.
GRUB_HIDDEN_TIMEOUT_QUIET=false  # Will show a countdown timer
GRUB_TIMEOUT=5  # How long the menu, once displayed, will allow for a selection.


For more detailed information on each entry, refer to the links provided by *oldfred*.

Run "sudo update-grub" after making any changes.

---

### Post by wrighty43 on 2010-04-16
well i started messing with settings, i changed the 30_prober to 07_prober but that seemed to get rid of the windows 7 entry all together, changed it back and still windows 7 entry is missing.  So i reinstalled grub 2, still missing widnows 7 ... Help !!"!!

---

### Post by drs305 on 2010-04-16
> **wrighty43 said:**
> well i started messing with settings, i changed the 30_prober to 07_prober but that seemed to get rid of the windows 7 entry all together, changed it back and still windows 7 entry is missing.  So i reinstalled grub 2, still missing widnows 7 ... Help !!"!!

wrighty43,

It sounds like you mixed up different tweaks - there isn't a reason to change the name of 30_os-prober.

Have you run "sudo update-grub" after reinstalling G2? Sometimes Grub2 doesn't recognize the Windows OS until this command is run *after* the reinstall. And you don't have an entry for Windows, correct (and not a link that doesn't work)?

Did you uninstall G2 completely and then reinstall, or just reinstall? 

This post (#12) shows how to completely remove Grub2 and then reinstall it. It will remove all existing Grub2 config files and replace them with the defaults. This would be the best way to ensure you are working with a full set of **correct** G2 files:
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12]("http://ubuntuforums.org/showpost.php?p=9107370&postcount=12")

---

### Post by wrighty43 on 2010-04-16
cheers for the help, managed to fix it, i re-installed the windows 7 boot loader, then re-i nstalled grub and it works fine now :D

---

