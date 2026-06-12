---
title: "How to install an ATi Driver?"
date: 2006-04-14
forum: General Help
---

### Post by amished on 2006-04-14
I recently installed Ubuntu on my desktop, with an ATi Radeon 9600 pro (old, I know, I'll probably update it fairly soon), but I'm not sure of 2 things:

1) Which driver to get to have the most up to date drivers out there, with a mainly gaming purpose, and

2) How to install said drivers?

Thank you for the help,
amished

---

### Post by dermotti on 2006-04-14
**sudo apt-get xorg-driver-fglrx**

---

### Post by amished on 2006-04-14
```

amished@amish:~$ sudo apt-get xorg-driver-fglrx
E: Invalid operation xorg-driver-fglrx
```

Why is this an invalid operation?  ](*,) 

thanks for the help,
amished

---

### Post by gerbman on 2006-04-14
[QUOTE=amished]```

amished@amish:~$ sudo apt-get xorg-driver-fglrx
E: Invalid operation xorg-driver-fglrx
```

Why is this an invalid operation?  ](*,) 

thanks for the help,
amished[/QUOTE]
[This]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") is pretty much the standard guide for getting the ATI drivers working. The reason your above command failed is because it is incorrect. It should be ```
sudo apt-get install xorg-driver-fglrx
```Follow the guide and you should be good to go.

---

### Post by amished on 2006-04-14
Ok, most of it made sense, and I configured a lot of it.  But near the end of the first part of the howto, it says to confirm that it works, but here's my output:

```
amished@amish:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Which is much different from the
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

that they show that I should get.  What, if anything, did I do wrong?  More specifcally, what does that extension missing on display mean?

thanks again for all the help! 
amished

---

### Post by gerbman on 2006-04-14
[QUOTE=amished]Ok, most of it made sense, and I configured a lot of it.  But near the end of the first part of the howto, it says to confirm that it works, but here's my output:

```
amished@amish:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Which is much different from the
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

that they show that I should get.  What, if anything, did I do wrong?  More specifcally, what does that extension missing on display mean?

thanks again for all the help! 
amished[/QUOTE]The output you're getting indicates that the fglrx driver isn't being used. "Mesa" is what the system uses by default, and isn't accelerated. Did you run the ```
sudo dpkg-reconfigure xserver-xorg
```step and select the "fglrx" driver, as mentioned?

---

### Post by amished on 2006-04-18
Ahh, got it!  When selecting the drivers, and ati was already selected, I didn't scroll down to select fglrx, which I didn't know was there until I started messing around with it more..

Thanks guys for all your help!
amished

---

