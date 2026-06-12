---
title: "Lucid won't boot if unused drive is unplugged"
date: 2010-05-04
forum: General Help
---

### Post by solitaire on 2010-05-04
I've a weird problem with my fresh install of 10.04

I've a main drive and an additional internal drive (to be used externally for future backups).

If i unplug the additional drive the system will not boot (drops to a grub box saying unplugged drive is slow to respond)

As far as i can tell the unplugged drive is not used and it not even mounted on my system. It's not listed in "fstab"

Is there anywhere else i can look to see what's accessing the drive? 
Or how to remove the drive from the system?

I'd hate to have to wipe the main system and reinstall it again.

---

### Post by Crio on 2010-05-04
If the drive was in the system  during install it should be in fstab, I think.

If it is in fstab but could not be mounted during boot, the boot would hang waiting for user input. Press S to skip the mount (there should be prompt, but it sometimes seems to be absent). 

Afterwards edit your fstab. (By the way, fstab now refers to disks by UUID, you can find corresponding UUID by typing
sudo blkid
in your terminal.

---

### Post by solitaire on 2010-05-04
I just double checked and as I said the drive is not listed in "fstab".

---

### Post by thecapsaicinkid on 2010-05-04
I expect your drives are getting assigned different UUIDs when one is plugged/unplugged. I have the same problem but in reverse, when I plug in a CD-ROM drive it can't find my boot drive.

---

### Post by solitaire on 2010-05-04
possibly!

might have to use /dev/sda# instead of UUID's in fstab...

just need to double check how to do it!!

---

### Post by thecapsaicinkid on 2010-05-04
When it does fail to boot (with the extra drive attached) it drops me to a very cut down shell. The problem is I can't access the blockid program to read the new UUIDs and write them into grub's menu.lst (I guess that's the correct solution?)

Why does plugging an extra drive in cause UUIDs to get re-assigned anyway??!

---

### Post by solitaire on 2010-05-04
UUID's should only change if the drive partition has changed.
Plugging in or taking out a drive should NOT alter a UUID.

Their must be a bug somewhere. 

A missing drive that's not required during boot should not stop Grub from running, unless for some reason, it's being referenced somewhere in Grub!

---

### Post by solitaire on 2010-05-04
i'm gonna try an experiment.
Boot up as normal.
remove the offending drive physically while the system is running.
Run the Update-grub command.
and reboot.
See if that makes any difference with the drive removed...

---

### Post by solitaire on 2010-05-04
*update*
I removed the offending drive while the machine was running.
ran update-grub
rebooted
System starts normally!

Looks fixed.

---

### Post by thecapsaicinkid on 2010-05-05
Can you run update-grub command from the shell presented to you when it doesn't boot?

---

