---
title: "Can't Find &quot;40-permissions.rules&quot; File"
date: 2010-02-17
forum: General Help
---

### Post by Ibn Ar-Rashid on 2010-02-17
Hi, I was trying to enable link2 graphics mode to work in my virtual console and followed the this tutorial: [http://ubuntuforums.org/showthread.php?t=453667](http://ubuntuforums.org/showthread.php?t=453667). 

I am pretty new to Ubuntu and am currently using version 9.10, I don't know if the file has been removed in later versions, but I can't find the  "40-permissions.rules" that's supposed to be located under /etc/udev/rules.d/. 

I need to change the permissions for the virtual console and gpm so links2 works in graphics mode, if there's some other way to make the change permanently, notification is appreciated.



- - - - -
Currently Using: Dual-Boot Windows 7/Ubuntu 9.10, 
Dual-Boot Windows XP/Arch Linux.

---

### Post by dcstar on 2010-02-17
> **Ibn Ar-Rashid said:**
> Hi, I was trying to enable link2 graphics mode to work in my virtual console and followed the this tutorial: [http://ubuntuforums.org/showthread.php?t=453667](http://ubuntuforums.org/showthread.php?t=453667). 

I am pretty new to Ubuntu and am currently using version 9.10, I don't know if the file has been removed in later versions, but I can't find the  "40-permissions.rules" that's supposed to be located under /etc/udev/rules.d/. 
........


Old tutorials are worse than useless because 9.10 radically changed the whole X system config because it uses the latest Gnome release.

There may be an equivalent file somewhere but you won't find it in an old HOWTO.

---

### Post by Ibn Ar-Rashid on 2010-02-18
Thanx for the information, I will ask in the forums for a brief explanation of how to go about doing that with the changes having been done to version 9.10. Hopefully, I can find an alternative route soon.

---

### Post by nolanjurgens on 2010-05-19
I got this working in Lucid by just adding my account to the video group.
```
sudo usermod -a -G video yourusername
```

Then ran Links2 with:
```
links2 -g
```

---

