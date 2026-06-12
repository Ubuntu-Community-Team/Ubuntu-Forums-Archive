---
title: "¿¿ &quot;system does not support openGL&quot; ??"
date: 2011-07-13
forum: General Help
---

### Post by raptura on 2011-07-13
Hello fellow ubuntu users!

I have a minor problem that is more of an inconvenience than a system breaking bug. I am sorry if this is not the right thread for this, also. You see, I recently upgraded my ubuntu from 10.04 to 10.10 and then again to 11.04. After everything was said and done, one of my installed applications, FreeCAD would no longer load. A window would pop up saying that  "this system does not support openGL" or something like that. I was hoping somebody here could help me out.

The thing that really bugs me is that it (referring to FreeCAD) worked perfectly when I had 10.04 installed and along the way I guess I broke it.

I have a toshiba satellite a505 s6005 laptop. The output of lspci in my terminal is:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```If you guys can't help me out, its okay I guess, I still have FreeCAD working on a desktop I have at home, its just a little more convenient to have it portable on my laptop.

---

### Post by raptura on 2011-07-18
I am sorry if this is not allowed, but I am bumping this thread in hopes that I might get some help.

---

### Post by pqwoerituytrueiwoq on 2011-07-18
the recommended bump period on this forum is one a day
what does this give you
```
glxinfo | grep OpenGL
```

---

### Post by raptura on 2011-07-18
Sorry :(. Its just that I usually read forum threads, but I rarely post.

I had to install mesa-utils (I think) to get my terminal to display this 

"glxinfo | grep OpenGL" yields :

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

---

### Post by pqwoerituytrueiwoq on 2011-07-18
what about 
```
cat /etc/X11/xorg.conf
```if you cat file not found
```
sudo Xorg -configure
```then do it again

this is worth a shot
[http://ubuntuforums.org/showthread.php?t=434038&highlight=Xlib%3A+extension+GLX%26quot%3B+missing+%20on+display+%26quot%3B%3A0.0](http://ubuntuforums.org/showthread.php?t=434038&highlight=Xlib%3A+extension+GLX%26quot%3B+missing+%20on+display+%26quot%3B%3A0.0).

---

### Post by raptura on 2011-07-18
For the first one, I get that "No such file or directory," for the second, I get 

```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
```

I am not sure what that means.

---

### Post by raptura on 2011-09-24
[FONT=Times New Roman][SIZE=2]To whom it may concern,

If anyone reading is having a similar problem, the solution I found that helped was typing in the terminal [/SIZE][/FONT]

```
sudo update-alternatives --config gl_conf
```[FONT=Times New Roman][SIZE=2]

and then selecting a different configuration by typing a number then enter. Note: you will have to restart to see if anything has really changed.
[/SIZE][/FONT]

---

