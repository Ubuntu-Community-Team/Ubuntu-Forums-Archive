---
title: "Nvidia -stop X Server"
date: 2006-04-27
forum: General Help
---

### Post by BobSock on 2006-04-27
I downloaded the Nvidia drivers and run the command ```
kdesu sh /home/*user*/Desktop/NVIDIA-Linux-x86-1.0-8756-pkg1.run
```
I have a GeForce 6200 PCI-E.
It then gives me a message about X Server is running and needs to be disabled. Do I need to run that command under text mode? How do I stop X?

---

### Post by bluevoodoo1 on 2006-04-27
ctrl + alt + f1

(might have to log in... I can't recall)

then...
sudo /etc/init.d/gdm stop

if you're running KDE, should be kdm (I think) instead of gdm.

---

### Post by BobSock on 2006-04-27
I did ctrl + alt + f1 and got to text mode. then signed in and entered 'kdesu sh /home/user/Desktop/NVIDIA-Linux-x86-1.0-8756-pkg1.run' and I got ```
kdesu: cannot connect to X Server
```. Why would it want X servre shutdown if you need to connect to it, oxymoron. I'm sure I'm doing something wrong...:confused:

---

### Post by BobSock on 2006-04-28
Has anyone been able to get NVIDIA 3D drivers installed without this problem?

---

### Post by Sutekh on 2006-05-02
kdesu is for launhing graphical programs in KDE.  Because you stopped the graphical environment, kdesu can't work anymore.

For running anything as root in Ubuntu, and by Ubuntu I don't mean GNOME I mean Ubuntu, use sudo
```
sudo sh /home/user/Desktop/NVIDIA-Linux-x86-1.0-8756-pkg1.run
```

(Also posted in your newer thread)

---

