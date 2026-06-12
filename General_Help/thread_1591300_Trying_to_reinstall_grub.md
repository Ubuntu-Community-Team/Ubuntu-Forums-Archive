---
title: "Trying to reinstall grub"
date: 2010-10-09
forum: General Help
---

### Post by Wakawakamush on 2010-10-09
Hi,

I reinstalled windows and now my grub is gone. On the officaLubuntu help page thing [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") and this one i found on howtogeek [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/"). Which on should i use? And how do discover if my ubuntu partion is hda(0,0) or hda(0,1)?

Sorry for the longness of the link, i dont know if it is the forum or my ipod, but i couldn't make a better hyperlink.

---

### Post by mvklingeren on 2010-10-09
Well, its easy - the hda(0,1) means

Use Disk 0- and the 1st partition on it! (the disk count is zero-based, and the partition is count-based, starts at 1)

if you can boot the live-cd, and then open a shell:

sudo fdisk -l /dev/sda  

or 

sudo fdisk -l /dev/hda

It shows you the partition numbers behind sda# / hda#, that tells you what partition number to use.

---

### Post by garvinrick4 on 2010-10-09
Put in Live Cd (install Cd) and choose Try Ubuntu. When it boots up. Open up a terminal and copy and paste:
```
sudo fdisk -l 
```(small L)
If your outcome shows your linux install is in sda5 for this: Use whatever yours is.
```
sudo mkdir /media/root
``````
sudo mount /dev/sda5 /media/root
``````
sudo grub-install --recheck --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
``````
sudo shutdown -r now
```Take out cd and let it boot into hard drive and choose Ubuntu and open a terminal and:
```
sudo update-grub
```Now will have grub2 and all installs in grub menu.

---

### Post by Wakawakamush on 2010-10-09
i tried what you said, but now i get this error: ```
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/media/root /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /media/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda

```how do i fix that?

---

### Post by Wakawakamush on 2010-10-09
sorry, i should learn to read the output. i saw stuff like "error" and "incorrect" so i thought that is was wrong...

---

