---
title: "MIssing drives following upgrade"
date: 2010-10-19
forum: General Help
---

### Post by cogvos on 2010-10-19
Hi,

I have upgraded to 10.04 LTS from 9.something and have run into an odd problem. On boot I am told that 3 drives are not available. HD0 HD1 and SD8. Now I am guessing that something got confused during the upgrade due to the slightly odd way I boot linux, but have no idea how to fix it. There used to be a file in /etc but can't remember the name.

The way I boot is via the PC's bios, selecting the boot drive and then into grub, rather than straight into grub (there is a complex and frankly dull reason for this which I won't bore you with). As a result kernal upgrades think that root is on SD 1,7 when it is actually on SD 0,6. I'm not quite sure why this happens but it always has and is easy to fix by editing menu.lst. 

I am guessing that a similar thing happened when I upgraded but do not know what file I need to edit. Help?!

---

### Post by Rubi1200 on 2010-10-19
Hi,
please post the results of the boot-script linked at the bottom of my post.

The results will give us a better overview of your setup and make offering solutions easier.

Thanks.

---

### Post by cogvos on 2010-10-22
Many thanks for the reply. However please don't take the this in the wrong way. I am very reticent to download a script which needs to be installed via the super user. I am happy to post files etc but do not feel able to run this script.

---

### Post by matt_symes on 2010-10-22
Hi

Maybe your /etc/fstab file has been corrupted. I can understand you being reticent about running a script, but the script is safe.

Anyway post the results of 

1. sudo fdisk -l  
2. sudo blkid
3. cat /etc/fstab

This will give us a starting point for support

Kind regards

---

