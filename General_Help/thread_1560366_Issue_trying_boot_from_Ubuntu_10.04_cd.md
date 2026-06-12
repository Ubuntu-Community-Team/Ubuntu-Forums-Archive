---
title: "Issue trying boot from Ubuntu 10.04 cd"
date: 2010-08-24
forum: General Help
---

### Post by doktarZues on 2010-08-24
I just built a new rig and was going to give 10.04 64-bit a go.  At no point can I get to any menus.  When I boot from the CD, it gets to the Ubuntu screen with the flashing 5 dots for a minute or so and then dumps me to a command prompt with with text and an apparently very trimmed down version of linux.  :

[B][I](initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error.

Can not mount /dev/loop0 (cdrom/casperfilesystem.squashfs) on //filesystem.squashfs.

[/I][/B]

I put in a windows XP cd just to see if there was something inherently wrong with the system--it booted to the partition disk utility just fine.  I then put the 10.04 32-bit cd in and it came up fine, then I put the 64-bit cd in a different pc and it booted to the menu.  So all of the CDs are good.. the computer appears to good with XP and 10.04 32-bit, just not with the 64-bit. 

I'm screwing around with my bios currently to hopefully unsnag some type of a hw configuration that the 64-bit doesn't like but I'm getting really frustrated.  Hopefully someone has ran into this and has some guidance.  Thanks in advance !

icore3 processor
MB GIGABYTE GA-P55-USB3 LGA1156 R

---

### Post by MilesTails on 2010-08-25
Have you tried verifying that you have a good download and write of the cd?

---

### Post by doktarZues on 2010-08-26
> **MilesTails said:**
> Have you tried verifying that you have a good download and write of the cd?

You are the man..indeed the md5sum was off for the .iso I first downloaded.  I downloaded it again and the md5sum matched up.  I opened this thread as the cd was booting anticipating that a good md5 should fix the issue and it's loading ubuntu64 as I speak.  

Such a simple yet critical detail I overlooked..Thanks a bunch!

If you're ever in Brevard County, FL area (soon to be known as the formerly space coast), I owe you a beer!!

EDIT: what's wild is the same CD works in a different PC.

---

