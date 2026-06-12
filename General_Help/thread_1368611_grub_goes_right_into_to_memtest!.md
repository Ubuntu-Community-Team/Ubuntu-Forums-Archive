---
title: "grub goes right into to memtest!"
date: 2009-12-30
forum: General Help
---

### Post by mr clark25 on 2009-12-30
i was trying to install windows vista and somehow it deleted the partition that had my grub bootloader in it. i looked around for help in the forums (searching) and eventually found this (it was the first one i found that semmed to work): [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

now, when i press the power button, it goes right into memtest! (no "press esc to enter grub" or anything like that) i also tried changing my /etc/default/grub, too. i changed the following lines to look like this:

[I]GRUB_TIMEOUT=3
[/I]*#GRUB_HIDDEN_TIMEOUT=3*
[I]GRUB_HIDDEN_TIMEOUT_QUIET=false


in /etc/grub.d, the file names are all like they should be. (10_linux and 20_memtest86+)

i found this to: [http://ubuntuforums.org/showthread.php?t=1319202&highlight=boots+memtest](http://ubuntuforums.org/showthread.php?t=1319202&highlight=boots+memtest)

like that user, when i hold shift, i only have 2 options for memtest.

i ran into trouble with this:
[/I]sh:grub> linux /casper/vmlinuz root=/dev/sda6 rw

i tried chroot into my user from the live cd to run grub-update. it saud i had no /boot/grub/menu.lst i let it create one for me. i still get the same result :(

[I]i dont know what is wrong.:confused:
[/I]

---

### Post by Leppie on 2009-12-30
> **mr clark25 said:**
> i ran into trouble with this:
[/I]sh:grub> linux /casper/vmlinuz root=/dev/sda6 rw
this should be:
```
sh:grub> linux /boot/vmlinuz root=/dev/sda6 ro
```

> **mr clark25 said:**
> i tried chroot into my user from the live cd to run grub-update. it saud i had no /boot/grub/menu.lst i let it create one for me. i still get the same result :(
Karmic (9.10) normally ships with grub2.
try like this (assuming /dev/sda6 is your linux partition and you don't have a seperate /boot partition):
```
$sudo bash
$mkdir -p /mnt/temp/boot
$mount /dev/sda6 /mnt/temp/
$mount -o bind /proc /mnt/temp/proc
$mount -o bind /dev /mnt/temp/dev
$mount -o bind /dev/pts /mnt/temp/dev/pts
$mount -o bind /sys /mnt/temp/sys
$chroot /mnt/temp
$grub-install --recheck /dev/sda
$update-grub
$exit
```

---

### Post by mr clark25 on 2009-12-30
thanks for the response.

well, now i get a different result.
it loads grub like its supposed to. but then, it gives me ERROR 17.
cannot mount selected partition
press any key to continue...

so i press a key. then it gives me the option of selecting "chainload into GRUB 2" or "ubuntu 9.10, memtest86+"

both give the ERROR 17 mentioned above. any help?

---

### Post by mr clark25 on 2009-12-30
when i run 
grub-install --recheck /dev/sda
it looks like it thinks i have 3 hard drives, but i dont. at the end it gives me this:
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdc
(hd2)    /dev/sdh

i only have one hard drive. does that mean this is wrong? could that be the reson for the error17?

if this is the problem, how do i fix it?

---

### Post by presence1960 on 2009-12-30
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mr clark25 on 2009-12-30
nice script!
i attached the output to this post.

---

### Post by mr clark25 on 2009-12-30
i realized something when i went over that script (or the output)

it was running from the 1gb flash drive, and i had a 4gb hooked up also.

that might help a little.

---

### Post by presence1960 on 2009-12-30
you have major problems there. Your files loaded by GRUB are not all there. 
here are mine so you can compare:

```
=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-16-generic
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-16-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

```
without those you will never boot.

Also both your GRUBs are messed up. I see you got to 9.10 from a dist-upgrade. I know that leaves you with the ability to boot from Legacy GRUB (version 0.97) with the ability to chainload into GRUB2. But the problem is your entries to boot directly from legacy GRUB do not exist because those files are missing as evidenced above. Your chainload entry to GRUB2 is intact and indeed works but your GRUB2 is fouled up also as it has no entries to boot Ubuntu either It can't have them for the same reason GRUB 0.97 does not have them: they do not exist.

But the baffling part to me is all those files and GRUB entries are on that flash disk sdh. How in the world did they get there?

IMHO your system is all fouled up. I would attempt to back up my data from the Live CD to external media. Then partition the internal hard disk with[ gparted Live]("http://gparted.sourceforge.net/livecd.php"). Make the first partition NTFS for Vista and then leave the rest as unallocated. I would then boot the windows install DVD and install it onto that NTFS partition. Then I would do a clean install of 9.10 or 9.04 Ubuntu by booting the Live CD. If you want Ubuntu to use the rest of that unallocated space then choose "use the largest continuous free space" at the partitioner window of the Ubuntu Live CD. Or if you want to make storage partition(s)  then use gparted to create them prior to installing Ubuntu and choose the manual option at the partitioner window. if you are shaky I would use the unallocated space method and choose "use largest continuous free space" as Ubuntu will do the partitioning for you.

---

### Post by mr clark25 on 2009-12-31
i was messing around with the boot file and backed it up on that usb drive. that would explain all the files on it.

i might not have switched it back... does it look like they are all there on the usb (sdh)?

---

### Post by mr clark25 on 2009-12-31
it works now!!!!!!!!

i copied the old grub back, and ran those commands you mentioned earlier. (restored the old, glitched grub) now i can use my computer again!!!!

thanks for the help.

---

### Post by presence1960 on 2009-12-31
> **mr clark25 said:**
> it works now!!!!!!!!

i copied the old grub back, and ran those commands you mentioned earlier. (restored the old, glitched grub) now i can use my computer again!!!!

thanks for the help.

LOL you must have cut/pasted them rather than copy/pasted to that flash disk. That is the only explanation of how they were missing from your install but on the flash disk. Anyway without the script you may not have known what to do.

Glad you got it working! Enjoy Ubuntu

---

### Post by mr clark25 on 2009-12-31
you are right, i wouldn't have known what to do.

i was surprised that it worked at all (from the usb drive) because it had errors too. i had been using the grub from my 64bit installation to boot. then windows wiped my 64bit, and this happened. 

thanks for helping me get it working again.

---

