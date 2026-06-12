---
title: "Grub is acting up"
date: 2010-12-27
forum: General Help
---

### Post by buhmillion on 2010-12-27
I recently installed Windows 7 on a partition adjacent to an encrypted install of Ubuntu 10.10. When it finished installing, it overwrote grub, and I booted into a livecd to reinstall grub. However, I messed up and deleted all of the grub configuration files from the Ubuntu partition. When I run grub-install onto that partition, it does not write a grub.cfg file for some reason, and when it boots into it, it only gives a grub shell. 

Is there any way to do a complete clean install of grub onto a partition, with a menu and the os's listed?

---

### Post by Quackers on 2010-12-27
I think what you want is detailed here in the chroot section

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by buhmillion on 2010-12-27
> **Quackers said:**
> I think what you want is detailed here in the chroot section

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

I'll try it, thanks.

---

### Post by Quackers on 2010-12-27
You're welcome.
I would try the full chroot method from the live cd for 2 reasons.
The first is that purging and re-installing works best as everything is replaced. It is also necessary to use the apt-get method (in that guide) to install grub in these circumstances (not just grub-install).
Secondly, having used it many times myself, I know it works :-)

---

### Post by buhmillion on 2010-12-27
When I run the Chroot command, it gives me

chroot: failed to run command `/bin/bash': Exec format error


I have no idea what is causing that. Can anybody help me out, I've done everything in the guide up to 

sudo chroot /mnt/tmp

that's not working. I have the bash binary in both the running livecd and the installed system.

---

### Post by Quackers on 2010-12-27
Have you done all of these lines (after naming your individual Ubuntu partition?)
```
sudo mkdir /mnt/temp 
sudo mount /dev/sdXY /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  
sudo chroot /mnt/temp
```
including the 3rd one?
And you are in the live cd, right?

---

### Post by buhmillion on 2010-12-27
Yes, It's the last line that isn't running.

---

### Post by Quackers on 2010-12-27
You changed sdXY in the second command to sda5 (or whatever your root partition is)
Did you copy/paste all the commands?
I'm wondering if there is a space missing, particularly in the last command
sudo chroot /mnt/temp
there is a space between sudo and chroot and /mnt
yes?

---

### Post by buhmillion on 2010-12-27
> **Quackers said:**
> You changed sdXY in the second command to sda5 (or whatever your root partition is)
Did you copy/paste all the commands?
I'm wondering if there is a space missing, particularly in the last command
sudo chroot /mnt/temp
there is a space between sudo and chroot and /mnt
yes?

Yes, the spacing is correct, and i ran all of the lines above it, substituting my drive.

---

### Post by buhmillion on 2010-12-27
Would it matter if the Livecd is 32-bit and the install is 64 bit?

---

### Post by Quackers on 2010-12-27
What did you mean by this line earlier, please?
"I have the bash binary in both the running livecd and the installed system."

---

### Post by Quackers on 2010-12-27
> **buhmillion said:**
> Would it matter if the Livecd is 32-bit and the install is 64 bit?

I'm not sure, but I suspect it may do, yes.

---

### Post by buhmillion on 2010-12-27
I was finally able to chroot into the installed system, but another problem came up. 
(the chrooting problem was because of the architectures)

The problem I have now is that with grub on the MBR, and the grub files on an unencrypted partition along with the vmlinuz and the initramdisk, I don't know what to write into the grub.cfg for the root.

For example:



class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set f93d2a96-a0c0-430c-922f-14d5d64ff316
	linux	/vmlinuz-2.6.35-22-generic root=????? ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}

Is my entry for Ubuntu. Because the rest of the system is on a cryptsetup partition, (hd0,5), I don't know what to put for the root (where the question marks are). I tried putting in /dev/sda5 but then it started complaining that it couldn't find the init.

If anybody has a hard disk encrypted with cryptsetup LUKS, please post your menuentry in /boot/grub/grub.cfg so that I can see the format.

Any help is much appreciated.

---

### Post by buhmillion on 2010-12-27
BRAMPing the thread

---

