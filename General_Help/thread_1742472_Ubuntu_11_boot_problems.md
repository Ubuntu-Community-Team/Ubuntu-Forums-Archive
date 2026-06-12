---
title: "Ubuntu 11 boot problems"
date: 2011-04-28
forum: General Help
---

### Post by dravirex on 2011-04-28
Ok I used to have Mint 9 when I saw that ubuntu 11 was coming out I tried a live cd of the beta but waited to install it until the full version came out.
After I installed it I restarted my computer and when I got to where the partition screen should be I get

error: symbol grub_xports not found
grub rescue >

The only way I can boot is into a live cd.
Please reply I cant do anything on my computer and am new to linux.

---

### Post by garvinrick4 on 2011-04-28
IN live Cd run in a terminal:
sudo fdisk -l (lower case L)
Now see which sda# is your linux install.
Lets say sda5 for this.(use your own)
```
sudo mount /dev/sda5 /mnt
```
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
```
sudo umount /mnt
```
Boot into Ubuntu install and:
```
sudo update-grub
```
##Here is a couple of links to bookmark so as to have around:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by garvinrick4 on 2011-04-28
If you have any more problems than previous post then post this bootscript as directed.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

