---
title: "Recovery Console and Hardware Raid"
date: 2010-03-13
forum: General Help
---

### Post by Hootnholler on 2010-03-13
Hi everyone, 

First time poster, please be gentle. :D

I have done what seems to be a well-documented problem.  I'm trying to understand from a high-level overview and maybe someone has come up with a graceful solution.  If nothing else, maybe some sympathy will make my day go better!

Overview: 
Ubuntu 9 server, Hardware RAID 1 (LSI on Dell PowerEdge 440), misconfigured fstab :eek:  Fortunately, the fstab error is pointing to a network share that I tried to configure with the .smbcredentials methodology.  The network drive is beyond my control, so have to try and diagnose/fix from the server itself.

Lessons Learned: 
After reviewing quite a few comments, it appears that starting from a Live CD would be my best option and trying to edit the fstab file from there.  Unfortunately, the RAID configuration is not recognized (fdisk -l and df -h).  Recovery console gives the ever dreaded 'read-only' error message when editing (vi, nano, pico, etc...).

After some more investigating, it seems that I need to break the RAID and then try from there.  I'm sure I can do this, but have never really tried before.  Is it as easy as removing the drives from the RAID controller and plugging into an available SATA port on the motherboard and configuring the BIOS?  Will I be able to plug the drives back into the RAID controller after a successful fstab edit and go from there?

Sorry if this sounds elementary, but really need to try and keep the data on these drives (Business Intelligence type thing).  Plus, trying to avoid a lengthy backup process.

Other options are to install the operating system again ('dirty install' by Windows parlance).  The information that is desired to not lose is a website and in the /var/www directory.  Is this a last ditch effort?

Thank you for any and all replies.  Please forgive any lapses in responses, since I will only be by this server again on Monday.

Hoot

---

