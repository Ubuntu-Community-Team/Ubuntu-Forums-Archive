---
title: "ubuntu 11.04 not booting with win 7"
date: 2011-04-29
forum: General Help
---

### Post by alanfwiliams on 2011-04-29
i downloaded Ubuntu 11.04 yesterday using the torrent download section, burnt the ISO onto a cd and started the installation process, i selected the install with windows button and did the usual, once installation was complete i clicked the restart button ejected the cd and hit enter to restart, but like many other users have said it froze

ok so after a manual reboot i expected to see grub, but nooooo it was back in windows the usual way. tried and tried over and over again changing boot partition and even completely removing my windows partition. but still no boot. got fed up installed win 7 again and tried running it on a VM to my surprise installation was success full and even rebooted without any problem, if it works on a VM why wont it work on my pc

this is my rig
Intel core 2 duo 2.93 ghz
4gigs of Ram
1gb ATI HD 4350 
wireless Dlink network card

can some one please help me out here

---

### Post by oopsie on 2011-04-29
Do you have multiple harddrives?

---

### Post by alanfwiliams on 2011-04-29
no just one drive windows on the first partion and ubuntu in the second

---

### Post by hhoyt on 2011-04-29
As I read this, the problem is it froze on install.
I'd be suspicious of the CD. Does the MD5 on torrent match your MD5 on CD ???

Ref: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Best of luck, Howard

---

### Post by alanfwiliams on 2011-04-29
no installed just fine its something wrong with the boot configuration. and the cd is fine i tried it with a VM and worked out fine.

---

### Post by girishzeus on 2011-04-29
hi alanfwiliams
You should try the Windows installer for Ubuntu  wubi 
Wubi is a windows software which automatically creates a dual boot system

here is the link to download wubi
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)


steps:
1. Download ubuntu 
2. download wubi
3. Install wubi from windows system
4. reboot

Thats it!  :)

---

### Post by alanfwiliams on 2011-05-02
hey girishzeus:D:D
thank you so much for the info i final installed it and works fine and now im typing this in ubuntu while the whole thing is being updated thank you so much
.......
thanks:D:D:D:D:D

---

