---
title: "refresh rate stuck, GUI gone back to deafults"
date: 2010-05-25
forum: General Help
---

### Post by fireandspike on 2010-05-25
Hi

I restarted my pc yesterday to find that my refresh rate has changed to 60hz from 75hz and that my blue background colours for windows, buttons ,menu backgrounds etc. that I changed in system>preferences>appearance that I configured ages ago have been lost and have reverted back to grey and the default icons.

I changed nothing before this happened, installed nothing, changed no settings.

the preferences>display feature has now become completely non functional. The program displays but changing the resolution or refresh rate has no effect.  


I ran sudo dpkg-reconfigure xserver-xorg but nothing has changed.

here is my xorg.conf file.


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option "DynamicTwinView" "False"
	Option "FlatPanelProperties" "Scaling = Native"
	SubSection "Display"
                Depth           24
                Modes           "1280x1024_75"
        EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"9600XT"
	Driver	"ati"
	BusID           "PCI:1:0:0"
	Option        "BusType" "PCI"
        Option         "AGPMode" "1"
EndSection


The only changes I made since this problem started was to insert "1280x1024_75" to try to force it to 75hz but it does not work.

I can fix the appearance settings but its the refresh rates that I cant fix and its really bugging me as I can see scan lines on my monitor and its killing my eyes.

Any advice would be most welcome.

Thanks

---

### Post by fireandspike on 2010-05-27
Ok I fixed the problem. GNome display manager must be told to run at start up via system>administration>bootup manager

Gnome settings daemon must start on startup via > system>preferences>startup applications.

Having both these turned on solved my appearance and refresh rate problems.

---

