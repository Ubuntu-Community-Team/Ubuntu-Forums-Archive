---
title: "GRUB Help"
date: 2010-03-01
forum: General Help
---

### Post by SomeOne77 on 2010-03-01
Hi Guys.
I need you help to figure out why I cannot boot into my Kubuntu Install.

Long story short.  I needed to replace the hard drive where grub was installed initially... It was a dual boot with windows... With windows installed then kubuntu..

My MBR/Windows install was on /dev/sda
Kubuntu Root partition was on /dev/sdb

I have swapped the drives. So that the drive where Kubuntu is installed is the first drive.

/dev/sda1 is my root kubuntu install

and did the following in a live cd Env.

grub
root (hd0,0)
setup (hd0)
makeactive /dev/sda1

made the appropriate changes in /etc/fstab and in /boot/grub/menu.lst (changed hd1,0 to hd0,0)

I tested it with the failing drive still in it and it worked fine.

Now I have put the new drive in and it does not boot.  There must be something that I am missing ??

Now I reboot and i don't even see the grub menu at all.

Just sits there with a blinking cursor at the top of the screen

Any help would be very appreciated!

---

### Post by dabl on 2010-03-01
First check the BIOS hard drive settings, and make sure that they are in the sequence that you intend.

Another issue I've seen is that for a SATA drive you might need to set the SATA mode to "Legacy IDE", instead of "AHCI".  In most cases that I have seen, you only need it set to "Legacy IDE" to install Grub, and then you can set it back to AHCI mode for routine use.  YMMV, of course.

---

### Post by SomeOne77 on 2010-03-01
Hi,
I booted with a live CD and the drive are in the correct sequence.
Unless the LiveCD does not display it correctly.... But I doubt it.

Grub was installed without problems when i first install Kubuntu 7.10 about 2 years ago..


I am going to try a supergrub disk... Maybe that will help find the problem

Thanks for the tips

---

### Post by dabl on 2010-03-01
SATA drives, or IDE drives, or one of each?

---

### Post by SomeOne77 on 2010-03-01
All SATA drives.. The only IDE is the DVD Burner.

I just checked the BIOS drive order and they are fine.

---

### Post by dabl on 2010-03-01
I'd say you need to find the SATA "mode" setting, and make sure it is set to "Legacy IDE" or "IDE" for the moment, until you get Grub working correctly.

Also, did you set the "boot" flag on the partition that you are trying to install Grub on?  I'm not sure that Linux cares, but the BIOS might need it.

---

### Post by SomeOne77 on 2010-03-01
Well i was finally able to fix it by using SGD.

I booted it with the USB SGD.. Selected GNU/Linux, then fix GRUB and then choose my Kubuntu installed.

It then said "SGD Succeded".

I rebooted fine in my Kubuntu Install.

Thanks again for all the tips..

---

### Post by dabl on 2010-03-01
Great -- good old SGD!  :popcorn:

---

