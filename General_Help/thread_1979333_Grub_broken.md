---
title: "Grub broken"
date: 2012-05-13
forum: General Help
---

### Post by aquascrotum on 2012-05-13
Tried upgrading from 11.10 to 12.04 - broke the computer (seperate thread in Upgrades sub forum).

I resorted to a clean install - PC dual boots Vista and Ubuntu.  I have a seperate home partition.

I used GParted to format the Ubuntu OS partition and swap space.  i then selected the cleared partition to reinstall ubuntu (reverting to 11.10), when prompted I made sure it was pointing to that partition for /.  Also redirected /home to the home partition.

install went OK, however now grub is broken.  Have tried going in in a live CD to run update-grub, but I'm getting an error "grub-probe: error: cannot find a device for / (is /dev mounted).

I'm out of my depth at this stage.  I need to get this functioning until such times as I can get a Win 7 disc ordered - have had enough at this stage.

---

### Post by kc1di on 2012-05-13
I would try Boot Repair Here:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by aquascrotum on 2012-05-13
Thank you.  Solved that part of this mess.

Now for broken wifi and getting to the bottom of why 12.04 turns this machine into a brick!

---

