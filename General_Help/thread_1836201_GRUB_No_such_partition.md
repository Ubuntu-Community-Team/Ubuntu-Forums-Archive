---
title: "GRUB: No such partition"
date: 2011-08-30
forum: General Help
---

### Post by DanH42 on 2011-08-30
I installed Ubuntu 11.04 on my laptop a few days ago alongside a Windows 7 install. I used it for a while, installed some packages, etc, and everything worked fine. Yesterday, I installed a bunch of major updates (one of which I noticed was a linux update). When I rebooted the system after the update, I was greeted with
```
GRUB: No such partition
```
It then booted the GRUB recovery console. I looked around, and that looks like it's basically the message you get when you try "uninstalling" Ubuntu by simply deleting its partition. I didn't do that though, I in fact want to *keep* Ubuntu. The message pops up before GRUB lists OSes, so I can't even boot Windows.

I threw in the Ubuntu LiveCD, which I thankfully still had, fired up gparted, and confirmed that all the partitions were, in fact, still there. When I rebooted, GRUB worked fine, and I was able to boot normally.

Today, after a few hours of normal use and countless flawless reboots, I decided to update my ALSA drivers to support my (rather new) sound card. When the installation was complete, I rebooted, and was greeted with the same GRUB error as yesterday. I don't have the LiveCD with me right now, so I can't check to see if that does in fact solve the problem, or it was just a random coincidence.

What could be causing this problem? All the partitions are clearly there, even typing **[FONT="Courier New"]ls[/FONT]** in the GRUB recovery console lists them all (though it does list them all as MS-DOS, which is a little odd). Has anyone else encountered this error *without* deleting a partition?

---

