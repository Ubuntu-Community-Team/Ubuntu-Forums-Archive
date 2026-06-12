---
title: "Grub problems (Reinstallation didn't work!)"
date: 2011-10-14
forum: General Help
---

### Post by coldcaption on 2011-10-14
So I ran Kubuntu off a flash drive (yes, I used unetbootin), liked it, installed it, awesome. There were no errors with the installation, but when I rebooted to greet my gorgeous KDE desktop, my previously-functioning grub install gave me "invalid arch independent ELF magic." ELF magic? That's some technology that you won't find on OEM software!
And I'm starting to think it is magic, because no number of grub reinstalls will make the problem go away. I used the 11.04 alternate installer's rescue mode to try fixing it first, then ran a shell on the Linux partition to run grub-install myself, which said it installed successfully. Update-grub and update-grub2 did nothing to help, either. I've googled around and looked at "solved" threads, but all the 'solved' threads I've found yet didn't seem to have a solution I could find or were above my general Linux knowledge, so I couldn't make use of them. Please, please help me! My laptop is new and I don't want to lose it to a hosed bootloader. Thank you!

Edit: [http://osdir.com/ml/help-grub-gnu/2011-08/msg00015.html](http://osdir.com/ml/help-grub-gnu/2011-08/msg00015.html) This is one that is above my Linux knowledge. How does one run the install against "all drives but no partitions?"

This machine is a ThinkPad X120e by the way, which has come up a few times in search results for this problem after installing Natty.

After going through the BIOS settings and seeing that it only goes to grub at all when set to legacy boot, I think it may be a conflict with the UEFI hardware. Is there a way to install grub specifically for EFI?

---

### Post by coldcaption on 2011-10-15
Thread seems to have fallen off the first page. I'll take nearly any solution that will at least make it function again. Does Microsoft make any bootable media to restore its bootloader?

---

### Post by Snader on 2011-10-28
It seems that we are experiencing a similar problem.
Source: [http://ubuntuforums.org/showthread.php?t=1870369](http://ubuntuforums.org/showthread.php?t=1870369)

To my knowledge, there is yet no easy solution for the "invalid arch independent ELF magic" error. However, you could try to circumvent the problem by installing an old version of Ubuntu, such as Ubuntu 10.10. It worked like magic on my machine and hopefully also on yours. Please let me know.

---

