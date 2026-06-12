---
title: "Getting fglrx configured"
date: 2006-06-01
forum: General Help
---

### Post by cobbweb on 2006-06-01
Hey, I followed these instructions, 

 [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

To get my desktop running in 3d and also configured with this line 

dpk - reconfigure xserver-xorg 

 but after that I typed 

fglrxinfo and got

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


Which is not what I want. As in these instructions: 
[http://www.ubuntuforums.org/showthread.php?t=131253](http://www.ubuntuforums.org/showthread.php?t=131253)

 it says if mesa shows up you did somthing wrong. My computer says i have everything installed, but it doesn't seem to work. Do you have any idea why??? Its beccomeing quite agrivating because I can'tdo the 3D desktop and also it makes it so I can't play Americas Army. Anyway, any suggesions or help will well wanted. Thanks 

 Mahalo, 

 Cobbweb

---

### Post by Watcher on 2006-06-01
I'm also having this problem ... If I find a solution, I'll let you know

---

### Post by Galban on 2006-06-01
[QUOTE=Watcher]I'm also having this problem ... If I find a solution, I'll let you know[/QUOTE]

Me too, Mesa in place of Ati = No Acceleration. I´d been trying everthing. It seems to be a conflict betwin xorg-driver-fglrx and the restricted-modules about some libraries, glibc ones I think. Any ways, for sure, so far, Its seem to be imposible. ](*,)

---

### Post by Watcher on 2006-06-01
Ok, I think I may have a solution ... (it solved the problem on my pc).

You have to see if there is anything listed in  /etc/default/linux-restricted-modules-common ... Probably there is something like this in there:

DISABLED_MODULES="fglrx"

If so, remove the fglrx, reboot and see if that worked.

---

### Post by Galban on 2006-06-01
[QUOTE=Watcher]Ok, I think I may have a solution ... (it solved the problem on my pc).

You have to see if there is anything listed in  /etc/default/linux-restricted-modules-common ... Probably there is something like this in there:

DISABLED_MODULES="fglrx"

If so, remove the fglrx, reboot and see if that worked.[/QUOTE]

You know what, that makes sence, I tooked out ¨fglrx¨ from that black list, but I´ m not going to reboot now cause I´m downloading the Dapper DVD iso right now. I will let you know if that worked or not. Thanks:)

---

### Post by Rackerz on 2006-06-01
Are you trying to get the 8.25.8 drivers running? If so I know I post that made it pretty simple, more simple infact than that wiki page above.

---

### Post by seth0x2b on 2006-06-01
Try this.
[http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue](http://ubuntuforums.org/showthread.php?t=143283&highlight=mesa+issue)

Cheers

---

### Post by VFiend on 2006-06-01
[QUOTE=][/QUOTE]
I also had the "Xlib: extension "XFree86-DRI" missing on display ":0.0"." problem.
It's telling you that the DRI extension isn't enabled - all you have to do is edit /etc/X11/xorg.conf and add the line "load "dri"" in "Section "Module""

For example, the section should look something like this:
Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "dbe"
  load "v4l"
  load "dri"
EndSection

---

### Post by Watcher on 2006-06-02
[QUOTE=Galban]You know what, that makes sence, I tooked out ¨fglrx¨ from that black list, but I´ m not going to reboot now cause I´m downloading the Dapper DVD iso right now. I will let you know if that worked or not. Thanks:)[/QUOTE]Did it? Just curious to know :) (would be the first solution I posted on this forum that would work for somebody else beside me 8) )

---

