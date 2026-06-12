---
title: "Tried booting from a USB on my friend's laptop and screwed something up...help?"
date: 2010-07-23
forum: General Help
---

### Post by losthighway on 2010-07-23
My friend has an HP laptop and wanted to try out Ubuntu (I already have it on my laptop) so I used the Startup Disk Creator to put it on a USB stick so he could see if it worked on his laptop. I plugged the USB in and restarted the computer, and it went to a screen that said syslinux blah blah blah (bunch of copyright stuff) then "kernel image cannot be found" and it says "vesamenu cannot be found" and under all that it has the word "Boot:" with a cursor next to it to enter something. I figured I may have created the USB drive wrong, so I unplugged it but now whenever he starts his laptop, the same screen comes up and we cannot get past it. It comes up even when the USB stick isn't plugged in. I went to the BIOS and looked at the startup options and the first option is the laptop's internal hard drive (which is running Windows 7), and whenever I try system recovery, it goes back to the same screen with the syslinux stuff and the cursor. What the hell happened? He can't do anything with his laptop now and I didn't even install anything. The boot order is correct...why is it not loading Windows 7? Any help would be appreciated, otherwise I'm gonna have to pay to have his laptop fixed since this was my doing...bleh.

---

### Post by nemilar on 2010-07-23
Did you create the USB key on his machine?  If so, is it possible that you accidentally told it to write to the hard disk rather than the USB key?

---

### Post by losthighway on 2010-07-23
Nope. I have Ubuntu 9.10 on my laptop and used it to create the USB. It said everything went successfully and "you should now be able to run Ubuntu from this USB device" etc. But it never loaded on my friend's computer. Now it just does that "syslinux blah blah blah kernel image not found" and "Boot" with a cursor next to it every time we start it up, even with the USB not plugged in. We cannot get past it. He's mad at me because he has files he needs on it, and we can't boot into Windows 7, which is what should be on the hard drive. And the hard drive is the first boot option, too. So I don't understand it. It's like the USB disabled his computer's ability to boot into Windows at all, and I didn't even install anything. If he has to do a clean install of Windows and lose his files, he'll kill me... :(

---

### Post by cbraxton on 2010-07-23
> **losthighway said:**
> If he has to do a clean install of Windows and lose his files, he'll kill me... :(

I have no idea what could have gone wrong, but unless the hard drive was wiped there is no reason for your friend to lose his files. You can boot up on a Linux CD and copy his data to a flash drive or external hard drive before reinstalling Windows. For that matter, a complete reinstallation may not be necessary if just the boot sector got damaged. (Not sure what options Windows 7 has for that since I have not used it, but with XP you could fix the boot sector from the installation CD and/or do a "repair" installation which would just fix the OS files without wiping anything out.)

---

### Post by C.S.Cameron on 2010-07-24
Google Windows 7 fix mbr.

---

### Post by linux18 on 2010-07-24
probably the widows mbr, just replace it with grub:
-create another usb - test it on your laptop first  
-boot the usb on his laptop
-open a terminal and type " sudo grub-install /dev/sda  && sudo update-grub "
-remove the usb and reboot the laptop
great news, if that works the laptop pretty much ready for dual booting with linux

---

### Post by amsterdamharu on 2010-07-24
vesamenu is syslinux, somehow you have installed syslinux on your friends laptop. I have no experience with startup disk creator but you either have a usb device plugged in or a cd/DVD in there because there is no way booting from usb would install syslinux on the local harddrive unless you or your friend did something you're not telling us.

I would do what Cameron suggested, use fix mbr for windows 7
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

To create a usb version of the liveCD I always use unetbootin, you can run that program in windows and point it to the iso. The program will then put all the needed files on the usb.

---

### Post by C.S.Cameron on 2010-07-24
Oops, Saved twice

---

