---
title: "how can i remove the sidebar from ubuntu"
date: 2011-04-21
forum: General Help
---

### Post by tunechi on 2011-04-21
hi, i am using Ubuntu Nebook Remix 
[IMG]http://bestopensource.info/wp-content/uploads/2010/11/Unity-Start-Menu.jpeg[/IMG]
^^^^^^
HOw can i remove it , i installed docky , and i only want to use it , thanks

---

### Post by bmathis on 2011-04-22
Install a different window manager (gnome, kde, xfce, fluxbox, etc...). Then when logging in, choose that window manager for your session.

---

### Post by tunechi on 2011-04-22
> **bmathis said:**
> Install a different window manager (gnome, kde, xfce, fluxbox, etc...). Then when logging in, choose that window manager for your session.

thanks for the help , but how can i do that ?

---

### Post by Naggobot on 2011-04-22
Open synaptic package manager and search for your preferred desktop environment / window manager. For example I have installed XFCE4 and there is a package XFCE4 (Meta package for XFCE4 environment) in Synaptic. 

After installing the package log out and from login screen (I assume there is such in Net Book remix) select session XFCE4. In 10.04 Gnome the session selection is in the bottom bar in the login screen. 

Alternatively I would guess

```
sudo apt-get install XFCE4
```might work. I am not command line wizard so I can not guarantee.

---

### Post by bmathis on 2011-04-22
> **tunechi said:**
> thanks for the help , but how can i do that ?

Search engines are your friends :) [https://help.ubuntu.com/community/MetaPackages]("https://help.ubuntu.com/community/MetaPackages")

If you want to install the default Ubuntu Gnome desktop then you would open a terminal and type
```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
for xfce
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

