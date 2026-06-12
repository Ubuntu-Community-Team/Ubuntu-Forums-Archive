---
title: "Accidentally Installed Ubuntu on Extarnal/Data Recovery"
date: 2010-01-24
forum: General Help
---

### Post by mscholes on 2010-01-24
So here's the situation:
I was trying to install Ubuntu on of my 8gb thumb drives and have been troubleshooting doing so for a little while now.  So I've been telling the Ubuntu installer to use the entire volume to install the OS which means reformatting it.  However, during one iteration I inadvertently left my 300gb external HD plugged into the computer I was installing with and the installer defaulted to that drive instead of my thumb drive and I didn't notice.  I come back to find my 300gb external wiped clean and Linux OS files in its place.

My objective is to recover as much of this harddrive as I can and I've come across a few programs that I thought might work, but I'm new to the Linux world and not sure how they work and I want to make sure I don't do more damage by poking around with programs I don't understand.  Any suggestions for a fledgling techie in need?

---

### Post by mörgæs on 2010-01-25
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Linuxman. on 2010-01-25
I recommended to you Hireen Boot Cd to recovery the files.
You can download it from here : [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

*if you don't know create a bootable cd look here : [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by mscholes on 2010-01-25
Thanks for the tips guys.

It seems that Photorec was the program I was looking for.   I have been to the DataRecovery thread before and had already tried testdisk.  All it found was the partitions where Linux was installed and not the potentially lost files.  Now I'm running Photorec and its reporting recovered files.  My problem seemed to be that not only did I inadvertently format the drive, I also inadvertently installed Ubuntu on that drive.   Some of the files were overwritten when Ubuntu installed, but recovery tools that would let me browse through the rest of the erased data were only picking up the legitimate partitons created by the installer.  Looks like Photorec will just take all data it can find and copy it to a backup location, which should grab all the things I need.  I may be misusing these software still so any advice would still be appreciated.

---

