---
title: "Ubuntu &amp; Windows 7 Hibernation Problem"
date: 2012-02-23
forum: General Help
---

### Post by TheAJGman on 2012-02-23
When I close the lid to my laptop in windows it will sleep but when it comes time to hibernate it will wake up, manual hibernation will just black out the screen for a few seconds. Same thing happens with Ubuntu 11.10. I'm on acer aspire 7741G. it didnt use to do this.

---

### Post by Ms. Daisy on 2012-02-24
> **TheAJGman said:**
>  it didnt use to do this.
...before what? What did you change right before this started happening?

---

### Post by TheAJGman on 2012-02-24
nothing that i can think of

---

### Post by TheAJGman on 2012-02-25
ubuntu will hibernate now. no clue why. now its just windows

---

### Post by dna_gene on 2012-06-22
It has taken me 6 months to sort this:
run powercfg -energy and try to do windows hibernate (don't shut the lid but rather use the option from the start menu so you KNOW that it was going to hibernate)

My problems: hibredsleep failed. Sleep worked (mostly after video driver updated).

But to hibernate needed fixing all the errors from the powercfg command - see other help pages. Had to update tv card usb driver.

However it would still not hibernate:KS.

Last steps were: check the partitions on the hard disk - is there a weany one for windows just before your windows partition - this needs the boot flag ticked. DO NOT use the partition manager in windows to do this - it borked:mad: my whole hard disk and took most of an evening to fix using testdisk (yes finding the partition table the hard way)...

then it would still not boot.

I was booting with GRUB and there were two options to boot the dev/sda1 small windows boot partition or directly into windows 7 dev/sda2. 

Hibernate only works if windows is booted by the dev/sda1 partition with boot flag enabled.

i hope this helps someone because this is NOT obvious.

Good luck!!! all who venture here):P

---

