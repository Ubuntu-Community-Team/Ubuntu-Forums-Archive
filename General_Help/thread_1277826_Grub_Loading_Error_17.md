---
title: "Grub Loading Error 17"
date: 2009-09-28
forum: General Help
---

### Post by Matt0757 on 2009-09-28
Recently, while dual booting with Windows XP, I deleted two partitioned drives in order to allot a smaller portion of my hard drive to Ubuntu. The 55GB, over one fourth of the space on my hard drive, of allotted space was unnecessary; it was too much for the functions carried out on Ubuntu.
I unpartitioned the drives containing Ubuntu, deleting the registry and other files, and merged them together to form Drive G.
I restarted the computer to find Grub Loading Error 17. I have read other posts and find my situation slightly different due to the fact that I am out of a Windows ME CD. The OS was preinstalled. 
Any Advice?

---

### Post by dametalone on 2009-09-28
download a full version of XP off of torrents.  


Shoot yourself for using windows ME in the first place?

---

### Post by oldfred on 2009-09-28
When you edited partitions you renumbered them. Newer versions of the grub menu use UUID for Ubuntu so it will boot as long as the partition is the same, but any entry using root (hdx,y) will have to be redone in menu.lst and possibly in fstab to get partitions to mount correctly in Ubuntu.
Are you booting windows or Ubuntu? Use a liveCD to give us:
fdisk -l
blkid -L
/boot/grub/menu.lst

Or you can do all this in one script with some additional info that helps solve which partitions are bootable.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
creates results.txt in the same directory, post with code tags as it will be long.

---

### Post by Matt0757 on 2009-09-28
I meant XP, not ME

---

