---
title: "Cant get my Nvidia driver to work properly"
date: 2006-03-02
forum: General Help
---

### Post by OCPJaguar on 2006-03-02
I just followed the starter guide and it was working yesterday this is my glxinfo

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```

If you need my xorg.conf ill post it
any help would be greatly appreciated

---

### Post by akiro.yamamoto on 2006-03-02
Check your xorg.conf file for something like this:
[CODE]Section "Device"
	Identifier	"NVIDIA Corporation NV15DDR [GeForce2 Ti]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection[CODE\]
Post that section here or list
What NVidia Card do you have and which driver did you try to install?

---

### Post by OCPJaguar on 2006-03-02
heres my xorg.conf device section
```
Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:5:0:0"
EndSection
```
the card is a pci-e 6800gt
I used the driver from the repo's

This is what i did
```
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

```

---

### Post by PsychoTrauma on 2006-03-02
Change the nv to nvidia then restart X.

---

### Post by OCPJaguar on 2006-03-02
That just stopped it from running the x server
said something about my xorg.conf wasnt set up properly 
so i had to change it back

---

### Post by akiro.yamamoto on 2006-03-02
Here:
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
Changing the nv to nvidia may not work. As far as I can tell it's missing the drivers.
Try method1 in that how-to.
"dpkg -reconfigure -phigh xserver-xorg" may help you reconfigure in case or an error.

---

### Post by akiro.yamamoto on 2006-03-02
I used method1 and it worked for me.
Ensure you have( Load "glx" )in the module section of your xorg.conf file.

---

### Post by PsychoTrauma on 2006-03-02
I would also like to add that sometimes you'll need to do the "sudo nvidia-glx-config enable" command a couple of times for it to except it. After you do the command you should see some text that tells you to restart your computer.

---

### Post by OCPJaguar on 2006-03-02
Thanks guys i followed that thread and it works great now
for some reason the drivers were there and installed i just couldnt use them 
anyway thanks for all the help and quick responses

---

### Post by akiro.yamamoto on 2006-03-02
Glad to help ;)

---

### Post by excelsior on 2006-03-03
I have the same problem, but when I do use the solution above my X crashes!
 my graphics card isn't "NVIDIA" is that a problem?

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

---

