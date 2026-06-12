---
title: "32bit vga files in 64bit environment"
date: 2010-06-05
forum: General Help
---

### Post by Troy Barbas on 2010-06-05
Hi all,

I had installed playonlinux, but it tells me that I don't have 3d acceleration in my 64bit environment, but I do, I just that I believe it's 64bit libraries and I need to install the 32bit libraries.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3300 Graphics
OpenGL version string: 3.2.9756 Compatibility Profile Context[FONT=Verdana]

On playonlinux > settings > system has no information 

GLXinfos > no details

XOrg.conf
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

3Dtest > cannot run

System
System information:

Your system : GNU/Linux
Your kernel : Linux 2.6.32-22-generic
System language : en_AU.utf8
Your user login : fischer
Your computer's name : fischer-desktop
Your video card : 
Your distribution : Ubuntu
Your distribution version : 10.04
Wine version installed : wine-1.1.42
Wine version used by PlayOnLinux : wine-1.1.42

Question...how can I go about find this info? and how can I correctly install 32bit[/FONT] libraries?

---

