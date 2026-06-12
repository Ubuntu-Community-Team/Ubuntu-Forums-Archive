---
title: "Cant enter gui ?"
date: 2006-06-15
forum: General Help
---

### Post by darkowl on 2006-06-15
Hello !

I have installed ubuntu 6.06 and when i boot i get the console and then login there (dont know why do i get console ?) and then i tryed startx but it doesnt work...

How can i get into graphic mode ?

---

### Post by taurus on 2006-06-15
Maybe you installed the server version instead of the desktop version.  At the prompt, type
```

sudo apt-get install ubuntu-desktop
(to install Gnome window manager...)
sudo apt-get install kubuntu-desktop
(to install KDE window manager...)

```

---

### Post by ayoli on 2006-06-15
or maybe yur xorg is misconfigured, do you have any errors when enter startx command ?
if errors say file not found you may install desktop packages as said above.
if errors are X errors maybe you ave to reconfigure it with:
sudo dpkg-reconfigure -phigh xserver-xorg
hope that  helps.

---

### Post by darkowl on 2006-06-15
[QUOTE=taurus]Maybe you installed the server version instead of the desktop version.  At the prompt, type
```

sudo apt-get install ubuntu-desktop
(to install Gnome window manager...)
sudo apt-get install kubuntu-desktop
(to install KDE window manager...)

```[/QUOTE]

desktop version cant install...
It says: server is for installation on hdd...
I cant fix my internet in console so i cant download anything...

I have the desktop version and server:
desktop version has install on desktop but it doesnt work, and server doesnt have gui... What is wrong with this distro ?!?

---

### Post by eth on 2006-06-15
Nothing wrong, Server distro come with no gui (400MB) while probably your Desktop version (2.6GB) is experiencing troubles with some ATI video chipset...am I wrong?

---

### Post by darkowl on 2006-06-16
No i dont have any problem with desktop version, i can enter gui but when i click on an icon install nothong happens...

---

### Post by givré on 2006-06-16
Try the alternate cd, it seems that there is some problem with the new graphic installer.
Or wait few weeks to have the new desktop CD, it should be upgrade.
[https://wiki.ubuntu.com/DapperPointReleaseProcess](https://wiki.ubuntu.com/DapperPointReleaseProcess)

---

### Post by darkowl on 2006-06-16
im downloading alternate cd so ill try.

But i got a new idea... would it work if i download 5.0 version of ubuntu and make upgrade ?

---

### Post by givré on 2006-06-16
It will work perfectly if it is do just after the install. But an upgrading means a lot of think to download and to install, so in fact 2 installation. Try before the alternate, it should be ok

---

### Post by darkowl on 2006-06-16
hello from ubuntu...I downloaded alternate cd and i installed it... its working perfect...

---

