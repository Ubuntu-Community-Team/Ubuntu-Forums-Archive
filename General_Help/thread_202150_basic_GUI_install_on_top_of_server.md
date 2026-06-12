---
title: "basic GUI install on top of server"
date: 2006-06-22
forum: General Help
---

### Post by grough on 2006-06-22
Is there a way to install an extremely basic desktop/gui on Ubuntu Server? For example, to use things like Synaptic and Nautilus, without having to install Open Office and all the other heavy stuff.

I tried installing the ubuntu-desktop package ontop of the server install, thinking that's all it was, but it came with all the extras.

Thanks,
G

---

### Post by K.Mandla on 2006-06-22
There are instructions for an exceptionally lightweight system here. ...

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

The idea there is actually for systems that have very low memory, but if I understand you right, you're after a very basic graphical interface.

Usually I do

```
sudo apt-get install x-window-system-core xfce4 xfce4-terminal thunar
```
on top of a server installation for a very slim (_very_ slim) profile desktop.

---

### Post by Kilz on 2006-06-22
You could also do 
```
sudo apt-get install xubuntu-desktop
```

---

### Post by K.Mandla on 2006-06-23
[QUOTE=Kilz]You could also do 
```
sudo apt-get install xubuntu-desktop
```[/QUOTE]
That will work too, but don't forget you'll get the GIMP, Abiword, Firefox, Thunderbird ... and a bunch of other things.

---

