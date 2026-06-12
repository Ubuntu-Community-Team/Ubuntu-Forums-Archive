---
title: "Logging In To Ubuntu"
date: 2009-12-01
forum: General Help
---

### Post by black28 on 2009-12-01
hey guys, i am a new user with Linux. i got a free Desktop that was crashed and couldn't get XP to run on it so i decided to make it strictly Linux OS based PC. anyways. i tried Puppy, and wanted to give Ubuntu a try. so i downloaded and installed Ubuntu 8.4 via CD-ROM. this is the problem i have now. i don't know what to do.

I boot the PC up via HDD. and it goes through the Ubuntu checklists, and the asks for user. i put mine in and it asks for the psswrd. i put that in then it stays on the black screen with white text. and says:

"To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

(myusername)@ubuntu:~S "

what am i supposed to do at this screen? i can't get it to start up. please help. all is appreciated!

---

### Post by Spectre5 on 2009-12-01
What iso did you use to burn to the CD?  It sounds like maybe you installed a server iso as the server iso doesn't install a window manager/desktop.

---

### Post by black28 on 2009-12-01
come to think of it...when i downloaded the iso file, and changed bios to boot CD first it said Install Ubuntu Server, another option was install Frist HDD or something this one didnt work. it said failed so i used the Install Server Option. it had the partitioning and everything though. like creating usernames and passwords and formatting...

---

### Post by jbrown96 on 2009-12-01
try running ```
startx
``` once you login and report what happens. It would also be helpful to know your video card ```
lspci | grep VGA
``` will tell you what card you have.

---

### Post by akakingess on 2009-12-01
> **Spectre5 said:**
> What iso did you use to burn to the CD?  It sounds like maybe you installed a server iso as the server iso doesn't install a window manager/desktop.

+1, that sounds like what happened, I would recommend downloading the desktop version and starting over, also, when installing, I would consider your partitioning so in cases like this, you would save data and still be able to reinstall without losing anything (not that that is an issue right now), but when setting up you desktop edition, I would create 3 partitions, 1 / , that would be where the core of Ubuntu is installed and 30 GB should be more than sufficient, then create your SWAP partition, which should be about the size of the amount of RAM you have or even double that, and a third (hopefully the largest partition should be your /home partition, these will contain any documents, audio, pictures, etc. that you would use/save on your normal "Windows" type computer, but this way, even if at a later date you have to do a reinstall of the Ubuntu OS your files are safe on their own partition. All of these are just recommendations and feel free to contact me if it sounds like overload, as I would be happy to assist you.

---

### Post by fluffman86 on 2009-12-01
It's possible to convert your server to a desktop, but really, it'll be easier to just install the desktop version.  You just need the default option when downloading from ubuntu.com

---

### Post by jbrown96 on 2009-12-01
> **akakingess said:**
> +1, that sounds like what happened, I would recommend downloading the desktop version and starting over, also, when installing, I would consider your partitioning so in cases like this, you would save data and still be able to reinstall without losing anything (not that that is an issue right now), but when setting up you desktop edition, I would create 3 partitions, 1 / , that would be where the core of Ubuntu is installed and 30 GB should be more than sufficient, then create your SWAP partition, which should be about the size of the amount of RAM you have or even double that, and a third (hopefully the largest partition should be your /home partition, these will contain any documents, audio, pictures, etc. that you would use/save on your normal "Windows" type computer, but this way, even if at a later date you have to do a reinstall of the Ubuntu OS your files are safe on their own partition. All of these are just recommendations and feel free to contact me if it sounds like overload, as I would be happy to assist you.

+1 for a separate /home partition. I think 30GB for / is completely overboard. I've been using Ubuntu for several years, and I have never seen / use more than 7GB. I usually recommend 10GB to be safe.

---

### Post by nothingspecial on 2009-12-01
To get a working desktop 

```
sudo ifconfig eth0 up
```

```
sudo dhclient
```
```

sudo apt-get install gnome-core gdm network-manager-gnome x11-xserver-utils jockey-gtk gnome-utils
```

To get full ubuntu with all the bells and whistles replace the last command with ```
sudo apt-get install ubuntu-desktop
```

---

