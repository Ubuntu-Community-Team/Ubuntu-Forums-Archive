---
title: "ati - sluggish desktop performance"
date: 2006-02-26
forum: General Help
---

### Post by yet_another_newbie on 2006-02-26
I'm on a fairly new Ubuntu installation and I've noticed that desktop performance is rather slow. By slow I mean when moving large windows I can see trailing windows moving along with it as well as things like a slight delay on drawing things. For example switching tabs in Firefox or switching desktop windows. I do not have this problem on windows.

Some info about my current set up:

:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

I installed Breezy's included driver (8.16.20) hoping it would solve the problem. My graphics card is a 256MB ATI Radeon 9600 Pro. Has anybody else noticed this?

---

### Post by jakez on 2006-02-26
I installed mine ATI Radeon 9600 Pro via this howto: 
[http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation_through_APT](http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation_through_APT)
Note: to get it all work properly I had to put 'VideoOverlay on' (see the howto)
in the xorg-file
greetz

---

### Post by procras on 2006-02-26
Maybe try the newer flgrx version?[http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5582 (8.21.7)



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 2.0.5582 (8.21.7)

A 9600 should be nippy enough not to notice the things you have seen.
I also have a 9800 (another box) and there is no slowness there.
The open driver was also very good and didnt give a problem, you might want to try ati or radeon? aswell.

---

### Post by donar73 on 2006-02-26
Installing  a kernel that fits to your CPU, like linux-image-k7 or linux-image-686 could help to speed up things a bit.

---

