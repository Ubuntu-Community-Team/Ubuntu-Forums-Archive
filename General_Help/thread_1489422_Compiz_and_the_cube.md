---
title: "Compiz and the cube"
date: 2010-05-21
forum: General Help
---

### Post by Abu el Leban on 2010-05-21
Hi All,

Rather new to Ubuntu, and for the last 2 month or so I have being unable to get the cube to function, and I have no idea what so ever why.

When I try to mark extras in looks  ( SYSTEM/SETTINGS/LOOKS) I am able to mark extras but when i reboot my system the mark in extras is gone!!!!!! maybe the problem is to be found there?

Don't know if is a nvidia problem or compiz problem. Tried to check on Forlong if my craphics is able to run compiz, and all were OK,  look like this

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

[COLOR=Red]And when I am checking nvidia it looks like this[/COLOR]

lars@lars-desktop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: NV43 [GeForce 6600 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
       resources: irq:16 memory:de000000-deffffff memory:c0000000-cfffffff(prefetchable) memory:dd000000-ddffffff memory:dfee0000-dfefffff(prefetchable)

Are there anyone how knows what to do.

---

### Post by Angel Joaniquet on 2010-05-21
Do you have the 3D accelerator enabled?
type this in the comand line:

$ glxinfo | grep 'direct rendering'

it shold give this:

direct rendering: Yes

if not check if you have the nVidia property drivers, at System --> Administration --> Hardware controlers and install the latest one.

I hpe you succed in the cube, is pretty awsome.

---

### Post by Abu el Leban on 2010-05-21
> **Angel Joaniquet said:**
> Do you have the 3D accelerator enabled?
type this in the comand line:

$ glxinfo | grep 'direct rendering'

it shold give this:

direct rendering: Yes

if not check if you have the nVidia property drivers, at System --> Administration --> Hardware controlers and install the latest one.

I hpe you succed in the cube, is pretty awsome.

lars@lars-desktop:~$ glxinfo | grep 'direct rendering
> glxinfo | grep 'direct rendering'
>

that its and I do not get any yes ,  damn

and we I go to check the driver, its states " this driver is activeted, but not in use at the moment"??

---

### Post by Angel Joaniquet on 2010-05-21
> **Abu el Leban said:**
> and we I go to check the driver, its states " this driver is activeted, but not in use at the moment"??

Try to activate one version older

---

### Post by Abu el Leban on 2010-05-21
removed nvidia driver, but when I go to  sys/ad/hard there are no to pick from?

I know, that there were 3 the first time I had to make my choise, but now there are none.:confused:

---

### Post by Abu el Leban on 2010-05-21
and I can see that this is not the only problem.

When i go to sys/adm/nvidia  X server settings I get this one

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

How do I run nvidia-xconfig as root????,

---

### Post by Angel Joaniquet on 2010-05-21
try typing 
$ sudo su
you will be the root till you exit,don't freak out if while typing the password nothing apears, it is normal 

$ sudo nvidia-xconfig

---

### Post by Abu el Leban on 2010-05-21
lars@lars-desktop:~$ glxinfo | grep 'direct rendering'
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".
Xlib:  extension "GLX" missing on display ":1.0".

and still nothing different when I do

root@lars-desktop:/home/lars# nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

root@lars-desktop:/home/lars# 

then when i go to sys/set/look for extra effect, visuels effect could not be activeded.

and how do I restart the xserver ?

---

### Post by Angel Joaniquet on 2010-05-21
> **Abu el Leban said:**
> and how do I restart the xserver ?
For the xserver search it in google, 
I'm running out of ideas,sorry

---

