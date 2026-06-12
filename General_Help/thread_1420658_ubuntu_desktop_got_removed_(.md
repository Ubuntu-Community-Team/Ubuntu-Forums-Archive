---
title: "ubuntu desktop got removed :("
date: 2010-03-03
forum: General Help
---

### Post by blackmuel on 2010-03-03
hey all i really need some help because im a noob and of corse messed somthing up! :P i marked evolution for complete removal after reading some posts saying that you can remove it without removing ubuntu-desktop but it also removed gnome-applets gnome-panel gnome-session indicator-applet indicator-applet-session indicator-message indicator-session and libedataserverui1.2-8. and now i can only login to xterm. iv tried to apt-get it all back but i only have wifi on my laptop and desktop and im not sure how to get it all downloaded. any help would be awesome!!!

---

### Post by oldfred on 2010-03-03
I copied this from somewhere as I did something similar and ended up with no desktop. From a liveCD chroot into your install and reinstall the desktop.

Of course you must first know what partition you want to mount, in this example I'm using sda1:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by blackmuel on 2010-03-03
OMG! thankz for the quick reply!!! im gonna try that in the morning and see if i can figure it out and ill post what i get! thanks!:D

---

### Post by blackmuel on 2010-03-05
ok so i tried that and it brought up unable to fetch (all my repos) then i tried to apt-cdrom add and that didnt work so im not really sure what to do because it doesnt seem like my repos are working eather.

---

### Post by sandyd on 2010-03-05
does wifi work on the livecd? if it does, you need to connect to your wifi network in order to download ubuntu-desktop.

---

### Post by blackmuel on 2010-03-05
yea it does connect so how would i install ubuntu desktop onto the partition that my ubuntu is installed on?

---

### Post by lyall on 2010-03-05
Recover a Damaged Desktop

at the log in screen select the Options and select Failsafe gnome
and click to Change Session

than you should be able to repair your desktop

see link [http://www.dharwadkar.com/weblog/ubuntu04]("http://www.dharwadkar.com/weblog/ubuntu04")

good luck and have fun learning

---

### Post by blackmuel on 2010-03-05
ok but i have ubuntu installed on another partition. couldnt i logon to that one and reinstall ubuntu-desktop on the other partition? like ill logon to the good partition and then connect to wifi then is there a way to install ubuntu desktop to the other? sorry for all the posts 
:P

---

### Post by sosaited on 2010-11-11
> **oldfred said:**
> I copied this from somewhere as I did something similar and ended up with no desktop. From a liveCD chroot into your install and reinstall the desktop.

Of course you must first know what partition you want to mount, in this example I'm using sda1:

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /mnt
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
apt-get update
apt-get upgrade
#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt

You saved my new and shiny 10.10 as well man. Thanks a lot.

I had messed up my system (Couldn't log in, kept returning to login screen after enter password) after I had removed some pulseaudio stuff (which also removed ubuntu-desktop) to try and fix the problem of not being able to record the sounds being played on the system like I can on 10.04. After I couldn't log back in, I tried searching for solutions and found yours and gave it a try and it worked perfectly and I installed ubuntu-desktop and other stuff while chrooted.

---

