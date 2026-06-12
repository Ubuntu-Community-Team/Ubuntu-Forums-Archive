---
title: "Removing Grub Residue"
date: 2010-08-23
forum: General Help
---

### Post by corowakid on 2010-08-23
Hi all.

Boy, do I need some advice and help. I dual booted Ubuntu with Win XP, and decided to upgrade XP to Win7. Thought I knew how to do it, so excuse my dumbness.  Here's where I'm at:

I booted GParted, and deleted the /, /home and swap partitions, making unallocated space. I expanded Win XP partition and tried to re-boot, expecting only Windows to show. Instead, I got the Error 22 error when Grub was the first thing to load.

So, back to GParted, deleted the primary partition, created a new bootable partition, formatted it NTFS, and put the Win7 disk and rebooted. This time I got a Windows error "can't load NTLdr".

Rebooted the computer without the disk, and got the Error 22 again. So it seems (?) that I'm not able to change/remove or otherwise, the Grub boot file.

So the drive is currently useless, unless someone can tell me how to get the disk back to a bootable state where I can load Win7, after which I can create Ubuntu as a dual boot again.

Feel dumb as for how I got into this mess, and would appreciate any advice that people can offer. TIA for your help.

---

### Post by arubislander on 2010-08-23
Let's see if I understand what it is you are trying to achieve:

You started with XP and Ubuntu dual booting, and you want to end up with Win 7 and Ubuntu dual boot?

And the Win 7 CD you have.. is that an installation CD or an upgrade CD (and is there a difference?)

---

### Post by Gordonbp531 on 2010-08-23
Boot from the Windows 7 DVD. Do a Custom install. Delete ALL partitions, create one new one for Win 7 and format.
That should enable you to install Win 7.

Should you ever want to do this again, do it the other way round.
Boot into Windows and use this handy utility called [EasyBCD]("http://neosmart.net/dl.php?id=1") to restore the Windows MBR BEFORE you remove the Linux partitions. Works really well!

---

### Post by corowakid on 2010-08-23
> **arubislander said:**
> Let's see if I understand what it is you are trying to achieve:

You started with XP and Ubuntu dual booting, and you want to end up with Win 7 and Ubuntu dual boot?

And the Win 7 CD you have.. is that an installation CD or an upgrade CD (and is there a difference?)

I'm using the Win7 Update disk, which means I have to install my XP full version beforehand. I've tried the XP and also the prior Win98 full versions and have the same problem with both, altho the error shows a different Windows bootloader name. What I want to do is instal Windows7 and then Ubuntu 10.04. I did the original instals OK, using Windows first, then partitioning the disk and installing Ubuntu 8.04, and since updated later versions. But when it got to upgrading Windows, I knew it was a bigger problem than going into Windows via Grub and trying the Upgrade from there. That's when I used my great acumen (?!) and stuffed it up.

From this, any suggestions. And thanks for the prompt response.

---

### Post by arubislander on 2010-08-23
OK, thanks for the clarification.

You are correct in assuming you have to install XP first. You have an XP installation CD/DVD? If you do, you should be able to boot from it, even if your main hard drive will not boot. After all it is also possible to install Windows on a drive that is completely empty.

---

