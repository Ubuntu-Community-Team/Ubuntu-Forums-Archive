---
title: "Trying to install FreeNX on 9.04, Gtk-WARNING **: cannot open display:"
date: 2009-12-10
forum: General Help
---

### Post by MKVCrazy on 2009-12-10
I'm trying to follow this [tutorial]("https://help.ubuntu.com/community/FreeNX#Installing%20the%20FreeNX%20server%20on%20older%20Ubuntu%20Versions") on installing FreeNX Server on my Ubuntu Server 9.04 64-Bit. I am following the part where it says "Installation for older Ubuntu versions" because it's separated in 9.10 and older Ubuntu versions.

So I enter the very first command as said in the tutorial which is the following:
```
gksudo gedit /etc/apt/sources.list
```AND I get this error:
```
root@XXXXX:~# gedit /etc/apt/sources.list

(gedit:3826): Gtk-WARNING **: cannot open display: 
root@XXXXX:~#
```

I didn't have GUI yet so I had to use nano (terminal based text editor) So my command becomes

```
sudo nano /etc/apt/sources.list
```

[SIZE=4]**EDIT:** [/SIZE][SIZE=4][COLOR=Blue]**Problem's been solved!**[/COLOR][/SIZE] :D

---

