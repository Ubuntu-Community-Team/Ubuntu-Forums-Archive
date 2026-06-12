---
title: "GRUB oddness"
date: 2010-01-22
forum: General Help
---

### Post by poldie on 2010-01-22
I installed grub yesterday, because I was following instructions on the net to building a usb key which booted into freedos. But although I followed the instructions carefully, it seems to have instead/additionally done something to the configuration of the grub which is installed as part of a regular ubuntu (9.10, 64 bit) install, because now i get a boot menu when i reboot my pc (without the usb key attached) and i have to press enter to continue.  Really i want to get rid of that, but i'm worried that if i just uninstall grub it'll remove not just this new install of it, but the one I want/need to boot my pc. Also, I'm not sure how to remove it anyway.

In case it helps, I was following the instructions here:

[http://raywoodcockslatest.blogspot.com/2009/08/trying-to-use-freedos-usb-drive-to.html](http://raywoodcockslatest.blogspot.com/2009/08/trying-to-use-freedos-usb-drive-to.html)

In the end I couldn't get it working because the instructions didn't work for me (I had no /media/disk to cd into), so i used unetbootin.

---

### Post by 00_Spykes on 2010-01-22
About Grub, as far as I know a bootloader install itself into a place called MBR, master boot record. I think it's the first few bytes of the first harddrive. Anyways, if I got your problem right is that you have an operating system on your hard drive, correct? 

You didn't have any bootloader (Grub for example) before (well you probably did but you never noticed)? 

Now you do have a bootloader, Grub, that works, but don't want it?

You can only have one bootloader per bootable device as far as I know, they overwrite eachother, but you can modify Grub for example to boot all your devices as you want.

---

### Post by poldie on 2010-01-22
> **00_Spykes said:**
> About Grub, as far as I know a bootloader install itself into a place called MBR, master boot record. I think it's the first few bytes of the first harddrive. Anyways, if I got your problem right is that you have an operating system on your hard drive, correct? 

You didn't have any bootloader (Grub for example) before (well you probably did but you never noticed)? 

Now you do have a bootloader, Grub, that works, but don't want it?

You can only have one bootloader per bootable device as far as I know, they overwrite eachother, but you can modify Grub for example to boot all your devices as you want.

No.

My hard drive was fine.  It included auto-booting into ubuntu when i turned the PC on, presumably via Grub. 

I was trying to make a bootable USB key. So I downloaded and ran grub from a terminal to make the usb key bootable.  But now, when i boot my pc, I see a grub boot menu.  I can boot into ubuntu ok, but I could before - that wasn't the problem.  I now want to remove the grub boot menu and continue to boot into ubuntu as before.

Why would using grub to make a usb key bootable affect my hard drive's booting up?  Am I lucky I didn't make a mess of my hd, and can still boot into ubuntu?

---

### Post by 00_Spykes on 2010-01-22
Ah! I'm sorry, I typoed massively there, I understood your problem but I failed to say that in my previous post.

I must admit I haven't checked out the USB HowTo, so I won't comment on that one. And no, Grub is separate from your partitions, so even if you would make a mess of your Grub installation it's fairly easy to repair and your partitions shouldn't be in danger. 

For example, if you have a spare drive where you want to install Windows on (why would you?), it will overwrite the MBR, but then you could just boot from your Ubuntu CD or whatever again and chroot in and re-install Grub, but that's off-topic. ;)

Not sure how Grub was configured as you had it, but check out the grub menu file, either /boot/grub/menu.lst or /boot/grub/grub.conf, and pay attention to which choice default is set to, and what the timeout is set to, not sure if you can set timeout to 0, but I suppose it can't hurt to set it to one second, not that long wait, eh? ;)

Good luck!

---

### Post by poldie on 2010-01-24
> **00_Spykes said:**
> Ah! I'm sorry, I typoed massively there, I understood your problem but I failed to say that in my previous post.

I must admit I haven't checked out the USB HowTo, so I won't comment on that one. And no, Grub is separate from your partitions, so even if you would make a mess of your Grub installation it's fairly easy to repair and your partitions shouldn't be in danger. 

For example, if you have a spare drive where you want to install Windows on (why would you?), it will overwrite the MBR, but then you could just boot from your Ubuntu CD or whatever again and chroot in and re-install Grub, but that's off-topic. ;)

Not sure how Grub was configured as you had it, but check out the grub menu file, either /boot/grub/menu.lst or /boot/grub/grub.conf, and pay attention to which choice default is set to, and what the timeout is set to, not sure if you can set timeout to 0, but I suppose it can't hurt to set it to one second, not that long wait, eh? ;)

Good luck!

Thanks, but magically the problem went away.  The most obvious explanation is that I didn't remove the usb key when I booted, but I definately did.  It's odd, but it's also not a problem now!  

Thanks anyway!

---

