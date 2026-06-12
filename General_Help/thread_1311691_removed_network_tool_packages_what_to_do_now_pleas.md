---
title: "removed network tool packages what to do now? please help"
date: 2009-11-02
forum: General Help
---

### Post by metalmaniac248 on 2009-11-02
ok my internet conection in ubuntu 9.10 randomlly stopped working (im using a wired conecttion)

stupidly i removed the "network-manager" and "net-tools" packages in the hope that reinstalling them would fix the problem however ofcourse once these were gone there was absolutely no way of reinstalling because i had no internet conection.

is my only option to do an frresh install, or is ther another way?


any help greatly appreciated.

---

### Post by P4man on 2009-11-02
LOL. Thats a funny mistake to make.
I guess you can download the packages from another computer or by using a livecd and use a usb stick to copy and install them again. 

There are a few programs to help you with that . I never tried any, but google suggested this:
[http://www.debian-administration.org/article/Offline_Package_Management_for_APT](http://www.debian-administration.org/article/Offline_Package_Management_for_APT)

Maybe someone has a better recommendation tho

---

### Post by alphaniner on 2009-11-02
Network-manager is just a GUI config tool, and net-tools doesn't *seem* to be necessary for networking devices to work.  You may be able to get things working through the terminal.  First off, what happens when you enter **sudo ethtool eth0**?

Edit: also, do you use DHCP or static IP?

---

### Post by dcstar on 2009-11-02
> **metalmaniac248 said:**
> ok my internet conection in ubuntu 9.10 randomlly stopped working (im using a wired conecttion)

stupidly i removed the "network-manager" and "net-tools" packages in the hope that reinstalling them would fix the problem however ofcourse once these were gone there was absolutely no way of reinstalling because i had no internet conection.

is my only option to do an frresh install, or is ther another way?


any help greatly appreciated.

Manually edit your /etc/network/interfaces file. Here is what is in mine (static ip):

```
auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
```

**ifconfig** will tell you the name of your network device.

---

### Post by lswb on 2009-11-02
If your wired internet connection is via a typical router setup these 2 lines entered in a terminal will normally connect:
```

sudo ifconfig eth0
sudo dhclient eth0

```

---

### Post by ndefontenay on 2009-11-02
try:
```
sudo apt-get install network-manager
```
from the terminal.

---

### Post by metalmaniac248 on 2009-11-03
Rite, i can't install network-manager coz I have no Internet conection, ifconfig doesn't work because it was uninstalled along with the other packages and editing interfaces didn't work

---

### Post by P4man on 2009-11-03
Have you tried offline apt yet?

Another trick might be to look in /var/cache/apt/archives
you never know...

---

### Post by lswb on 2009-11-03
You can reinstall from a live CD.

Main Menu/System/Administration/Synaptic. From Synaptic menu, Settings/Repositories/Ununtu Software, then check the box off for the CD. Close the dialog, hit the "reload" button once, then install your missing packages. 

After the network software is installed and running, remove the CD from the repository list the same way, reload again, and install any updated versions.

---

### Post by metalmaniac248 on 2009-11-04
yer its working again now thanks people

---

### Post by Earl-Grey on 2009-11-06
> **lswb said:**
> You can reinstall from a live CD.

Main Menu/System/Administration/Synaptic. From Synaptic menu, Settings/Repositories/Ununtu Software, then check the box off for the CD. Close the dialog, hit the "reload" button once, then install your missing packages. 

After the network software is installed and running, remove the CD from the repository list the same way, reload again, and install any updated versions.
[FONT=Verdana][COLOR=Gray]
Just wondering, is there any way of installing the Network Manager if you don't have a live CD and can't burn CD's with your computer?

I have the iso image and installed Ubuntu within Windows with a virtual drive. Is there a program that comes with Ubuntu that can mount the iso image that I have, so I can install the Network Manager from the virtual drive?

Any help would be great :KS[/COLOR][/FONT]

---

### Post by lubod on 2009-11-12
> **Earl-Grey said:**
> [FONT=Verdana][COLOR=Gray]
Just wondering, is there any way of installing the Network Manager if you don't have a live CD and can't burn CD's with your computer?

I have the iso image and installed Ubuntu within Windows with a virtual drive. Is there a program that comes with Ubuntu that can mount the iso image that I have, so I can install the Network Manager from the virtual drive?

Any help would be great :KS[/COLOR][/FONT]

Hope you got over this before, sorry if the problem is already resolved. :-)

If the ISO file is inside the host (in your case Windows) file system, the virtualisation software (e.g. VirtualBox or VMware) should have a preference to set the virtual CD the guest uses to read from the ISO as if it was a real physical CD.

If the ISO file is inside the guest (in your case Linux) file system, double click it and it mounts on the desktop, or use a separate program like gmountiso. When I installed it, it was just 1 package with no dependencies other than the base system packages like python, it installed all by itself on my system, so in theory you should be able to download the package gmountiso (insert i386 or amd64 flavor here).deb elsewhere and copy to linux for installation.

Neat article with gmountiso writeup, plus manual commands to do the same in comments.

[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

---

### Post by Earl-Grey on 2009-11-12
> **lubod said:**
> Hope you got over this before, sorry if the problem is already resolved. :-)

If the ISO file is inside the host (in your case Windows) file system, the virtualisation software (e.g. VirtualBox or VMware) should have a preference to set the virtual CD the guest uses to read from the ISO as if it was a real physical CD.

If the ISO file is inside the guest (in your case Linux) file system, double click it and it mounts on the desktop, or use a separate program like gmountiso. When I installed it, it was just 1 package with no dependencies other than the base system packages like python, it installed all by itself on my system, so in theory you should be able to download the package gmountiso (insert i386 or amd64 flavor here).deb elsewhere and copy to linux for installation.

Neat article with gmountiso writeup, plus manual commands to do the same in comments.

[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

I managed to get it sorted in the end, but thank you for the adivce. I didn't know you could do that with an iso file.

---

