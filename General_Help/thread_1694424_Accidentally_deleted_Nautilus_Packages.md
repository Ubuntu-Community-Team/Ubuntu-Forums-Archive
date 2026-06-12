---
title: "Accidentally deleted Nautilus Packages"
date: 2011-02-24
forum: General Help
---

### Post by ypeksen on 2011-02-24
Hello everyone,

I accidentally deleted several nautilus packages to free up some space. I did not know that nautilus packages should not be removed from the system. When I restarted ubuntu, login window appears and asks me to login. After I entered password, the screen blacks out and displays login window again and again.

My question is; which nautilus packages are installed in your system? Could you search for the "nautilus" packages in your Synaptic Package Manager? Please type only "nautilus" in the search box and search for it since I removed the packages by searching with "nautilus" only. (Packages with the green light nearby)

I can install packages from terminal with recovery mode. If you type the exact package names, i can download and install them.

By the way, any other idea is appreciated... Thanks..

---

### Post by wiggly81 on 2011-02-24
The list of packages when i type nautilus in synaptic package manager that are installed on my system are as follows...

nautilus
nautilus-share
nautilus-data
nautilus-sendto
libnautilus-extension1
nautilus-sendto-empathy
totem
gnome-icon-theme
ubuntuone-client-gnome
gnome-control-center
libgnomevfs2-common
libgnomevfs2-0
libgnomevfs2-extra
rhythmbox-plugins
brasero

---

### Post by ypeksen on 2011-02-24
Thank you wiggly81,

I will try the all. I hope it works..

---

### Post by ypeksen on 2011-02-24
Pfff.. did not work. I actually deleted the packages beginning with "nautilus".

Has anyone experienced with this problem before? Or do you have any idea i can try? I am sure this problem is related with nautilus packages.

---

### Post by wiggly81 on 2011-02-24
there are many nautilus packages avaliable maybe you had somthing installed that was a requirment of somthing else so i will put a screen shot of all avaliable packages.

some are duplicated as all i done was screen shots from top and from bottom but im sure you will see that



there was no duplicated actually 2 are missed off...

tracker-gui
libnautilus-burn4

---

### Post by thefasterblueone on 2011-02-24
What did you use to delete the packages?

Check your Synaptic Package Manager history, or check you log files, such as dpkg.log.

You can run these commands to help you search.

```
cat /var/log/dpkg.log | grep nautilus
```

```
dpkg --get-selections | grep nautilus
```

Goodluck.

---

### Post by ypeksen on 2011-02-24
I can not login to my account. It is getting into loop. blacks out and login window, blacks out and login window.. I used Synaptic Packet Manager.

---

### Post by thefasterblueone on 2011-02-24
Try rebooting and when and if you see grub screen, choose "recovery mode".

---

### Post by ypeksen on 2011-02-24
I am only able to fix problem from terminal with recovery mode.

> **ypeksen said:**
> Hello everyone,

I accidentally deleted several nautilus packages to free up some space. I did not know that nautilus packages should not be removed from the system. When I restarted ubuntu, login window appears and asks me to login. After I entered password, the screen blacks out and displays login window again and again.

My question is; which nautilus packages are installed in your system? Could you search for the "nautilus" packages in your Synaptic Package Manager? Please type only "nautilus" in the search box and search for it since I removed the packages by searching with "nautilus" only. (Packages with the green light nearby)

**I can install packages from terminal with recovery mode.** If you type the exact package names, i can download and install them.

By the way, any other idea is appreciated... Thanks..

Seems nobody had a problem like this.

---

### Post by gandaran on 2011-02-24
you also need to install [COLOR="DarkRed"]ubuntu-desktop[/COLOR], this package is removed when you remove nautilus, nautilus is a dependency of ubuntu-desktop, it will be installed along installing  ubuntu-desktop.

---

### Post by ypeksen on 2011-02-24
That is it. Thank you gandaran and thank you guys for your help.

---

