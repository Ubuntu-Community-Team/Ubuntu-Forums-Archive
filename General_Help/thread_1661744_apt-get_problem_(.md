---
title: "apt-get problem :("
date: 2011-01-07
forum: General Help
---

### Post by xChetaNx on 2011-01-07
Sorry if i posted this thread in wrong section.. 
i am having problem with ubuntu 10.10
when i am trying to install any software from apt-get command i get a error
i searched this forum and i saw in thread that 
after updating apt-get we can use software
i am currentlly using an Offline computer and i want to know that is there any way to update apt-get manually/offline :(

after 2 week i am having my Exam on Linux so i have to install an Linux OS Asap



please reply

---

### Post by dino99 on 2011-01-07
welcome,

some general help:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

scroll down about apt-offline

---

### Post by xChetaNx on 2011-01-07
dude
as i told in my post that when i use apt-get command i get error 

i got this error while installing apt-offline

```

E: Unable to locate package apt-offline

```

same error with other application

```

E: Unable to locate package phpmyadmin

```

---

### Post by oldos2er on 2011-01-07
If you have access to a different machine with internet, try Keryx. [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by cmoraes on 2011-01-07
You need to be online, if you want to use apt-get to install software.  Since your machine is offline, you can try downloading the packages (.deb files) from a computer that is online, and installing them on your machine using gdebi.

---

### Post by Krytarik on 2011-01-07
The guide obviously isn't correct regarding the initial install of "apt-offline" as a starting point, ironically=D>:
> sudo apt-get install apt-offlineLike cmoraes said, if you want to easyly install some few packages, you can download them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them with Gdebi.
This way of course gets complicated if the desired packages depends on other packages which aren't installed already.

To install packages following the guide, just download install the package "apt-offline" in the above-mentioned way and then proceed following the guide. Note that the package taken as example for the commands is called "abuse". Replace it with the name of the package you want to install.

EDIT: For the command of the first step this one should be sufficient for you, as example:
```
 sudo apt-offline set phpmyadmin-offline.sig --install-packages phpmyadmin
```You may include more than one package name, just at the end of the command.

---

### Post by xChetaNx on 2011-01-07
can u give me the List and direct links of the packages and where i should paste those packages
and how to install them 
ryt now i am using Dial connection on windows XP so i can directlly download and install those item now

or is there any software which can allow me to enter in ubuntu on Windows Desktop
coz last i was testing the ubuntu CD from Virtual box and in the CD ubuntu live mode i can use internet and the apt-get update was also working ...
i don't think that i can access to my installed ubuntu from Virtual Boxx

is there any other software so please mention that software also

---

### Post by Krytarik on 2011-01-07
> **xChetaNx said:**
> can u give me the List and direct links of the packages and where i should paste those packages
and how to install them 
ryt now i am using Dial connection on windows XP so i can directlly download and install those item now
procedure described in my previous post, [http://packages.ubuntu.com/maverick/apt-offline](http://packages.ubuntu.com/maverick/apt-offline)
> **xChetaNx said:**
> or is there any software which can allow me to enter in ubuntu on Windows Desktop
coz last i was testing the ubuntu CD from Virtual box and in the CD ubuntu live mode i can use internet and the apt-get update was also working ...
i don't think that i can access to my installed ubuntu from Virtual Boxx

is there any other software so please mention that software also
You may try to "chroot" into your installed version of Ubuntu from Virtual Box, I don't know if that works:

#Get internet connection going on live CD.
#I will use sda5 for the install partition (use whatever is yours) 
```
sudo fdisk -l
``` (lower case L)
will tell you your sda#
```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``````
apt-get install WHATEVER_YOU_WANT
``````
exit
``````

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```EDIT: What do you want to install exactly?

---

### Post by oldos2er on 2011-01-08
If you check out the software I recommended (Keryx), it handles dependencies for you.

---

