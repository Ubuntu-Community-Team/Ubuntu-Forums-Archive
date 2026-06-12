---
title: "pc rebooted during Upgrade, now can't log in??"
date: 2009-09-06
forum: General Help
---

### Post by sunseeker888 on 2009-09-06
Hi Guys


The bloody PC rebooted during an update now, I can't logged, the computer freezes after password is typed.

Recovery version does not work too, can't repaired broken packages too :(

Anyway googling around , I found only way is to use a LiveCD

here's the link

[http://ubuntuforums.org/archive/index.php/t-422523.html](http://ubuntuforums.org/archive/index.php/t-422523.html)


firstly....the originally howto can be found in tips and tutorials threat....i just forward this guide as i realized that this kind of guide doesn't exist in this section but it is really important . . .
especially to those cases..
if you are running an upgrade and you forgot to connect your laptop to power supply then when synaptic doesn't finish install software yet to your system...(after finished download)

or

your install software with command dpkg -i and that particular software doesn't have enough dependency then for sudden there will be broken software noticed by update manager ...for almost the time you can remove or reinstall it again using synaptic but how about when that particular broken installation broke your system and freeze your system

or

you shutdown your system and forgot that your software installation still running...

***for those all kind of situation or other situation that make you can't log on after restart even using 'safemode' ....so you need livecd to repair it...

put you livecd in and restart...then just lo on to livecd....

then open terminal

type

sudo mkdir /mnt/repair

sudo mount /dev/?d?? /mnt/repair

*noted that ?d? mean part of your ubuntu root partition....it might be sda1...or hdb1 or sdb or whatever...depend where you install your ubuntu....

sudo chroot /mnt/repair su

sudo apt-get update
sudo apt-get upgrade
sudo aptitude upgrade
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get upgrade


exit
sudo reboot



**************************************************************************



The above should have solved my problem but by doing sudo apt-get


I kept getting  ""unable to resolve host "



So basically the above did not work, as it was unable to reolve host in with LIVECD

---

### Post by Linteg on 2009-09-06
First, ensure that you can have access to internet from the live cd, try browsing with firefox. If that works then follow the guide and do these additional steps **after** you have mounted /mnt/repair but **before** you chroot.
```

sudo mount --bind /dev /mnt/repair/dev
sudo mount -t proc none /mnt/repair/proc
sudo mount -t sysfs none /mnt/repair/sys
sudo cp /etc/resolv.conf /mnt/repair/etc/resolv.conf

```
this will ensure that you'll have a more complete chroot environment, especially copying resolv.conf is important for internet access.

---

### Post by sunseeker888 on 2009-09-16
> **Linteg said:**
> First, ensure that you can have access to internet from the live cd, try browsing with firefox. If that works then follow the guide and do these additional steps **after** you have mounted /mnt/repair but **before** you chroot.
```

sudo mount --bind /dev /mnt/repair/dev
sudo mount -t proc none /mnt/repair/proc
sudo mount -t sysfs none /mnt/repair/sys
sudo cp /etc/resolv.conf /mnt/repair/etc/resolv.conf

```
this will ensure that you'll have a more complete chroot environment, especially copying resolv.conf is important for internet access.






Thanks, got it working now, sorry for the late reply

---

