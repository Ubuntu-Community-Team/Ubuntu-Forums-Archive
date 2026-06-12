---
title: "unable to run eve online and other issues"
date: 2011-05-02
forum: General Help
---

### Post by niroshido on 2011-05-02
Firstly, i am using VMware player, on it i have dedicated 40gb of my hdd and 1gb of my ram for Ubuntu 10.04. 

i installed eve-online using WINE 1.2 and followed some instructions from a thread of eve online forums [http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1315540](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1315540)

> to avoid some random crashes launch eve with the command: 
	wine explorer /desktop=EVE1,1920x1200 "C:\Program Files\CCP\EVE\eve.exe"
this emulates a desktop in wine.
replace 1920x1200 with the resolution of your monitor :)

i changed the res to 800x600 and attempted to load eve, the splash window loads up and then nothing, the splash window dissapears and i am left with the background of the WINE UI (in which case i cannot close the wine window either)

i then attempted to find out my graphics card and i cannot find it using
$ lspci
$ lspci -v
$ lspci -v | less

commands on a thread, or did i? 
> 00:0f.0 VGA compatible controller: VMware SVGA II Adapter
        Subsystem: VMware SVGA II Adapter
        Flags: medium devsel, IRQ 9
        I/O ports at 10d0 [size=16]
        Memory at d0000000 (32-bit, non-prefetchable) [size=128M]
        Memory at d8000000 (32-bit, non-prefetchable) [size=8M]
        [virtual] Expansion ROM at 40000000 [disabled] [size=32K]


i then tried to hardware drivers, in which case there are none shown from system>administration>hardware drivers. I then attempted to change my screen resolution or modify my display settings in which case i got 
> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?
> You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.


at this time i will say my graphics card is a geforce 8600GTS 256mb

assistance in helping me getting this to work is appreciated, let me know if i am missing information which will help resolve the problem, but be warned, if u require the info, u are litterally going to need to spell out to me what info and how to get it, as i am not used to commands

thanks in advance

---

### Post by niroshido on 2011-05-08
i am still looking for a solution to this btw

---

