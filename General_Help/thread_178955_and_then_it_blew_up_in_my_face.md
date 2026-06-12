---
title: "and then it blew up in my face"
date: 2006-05-18
forum: General Help
---

### Post by Wr8EYilK8Y on 2006-05-18
None of my openGL applications work. I can't enable nvidia-glx-config. Why?

```

williamd@williamskubuntu:~$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
williamd@williamskubuntu:~$   

```

Here's the file:
```

Section "Device"
        Identifier      "NVIDIA Corporation NV40? [Unknown nVidia Card]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection


```

---

### Post by bluevoodoo1 on 2006-05-18
All that script does is change the Driver to "nvidia" which you already have.

I just ran that script myself and I get the same warning. My openGL apps work fine... so perhaps it is something else?

what is the output of...

```
glxinfo
```

---

### Post by Wr8EYilK8Y on 2006-05-19
I don't know. Now Kubuntu only boots a command line instead of a GUI

---

### Post by tseliot on 2006-05-19
[QUOTE=Your Name Is]I don't know. Now Kubuntu only boots a command line instead of a GUI[/QUOTE]
If you want  a quick fix you can try my script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

If you can only use the command line try this:

If you use Ubuntu Breezy 32bit type:
```
wget http://www.albertomilone.eu/ubuntu/nvidia/scripts/nvidia_script_8756_32_breezy
```

**OR** (DON'T use both of them!)
If you use Ubuntu Breezy 64bit type:
```
wget http://www.albertomilone.eu/ubuntu/nvidia/scripts/nvidia_script_8756_64_breezy
```


Then make the script executable:

```
sudo chmod +x nvidia_script*
```


5) Run the script:

```
sudo ./nvidia_script*
```

Then answer the questions (Select "**install**" )

---

### Post by Wr8EYilK8Y on 2006-05-19
Yes, I can only use the command line. I will try your suggestion when I get home. Would installing the drivers from the nvidia web site work? Nevermind. That's what you basically told me to do.

---

### Post by Wr8EYilK8Y on 2006-05-19
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

Currently checking status of GLX

And it is installed.

EDIT:
```

williamd@williamskubuntu:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
williamd@williamskubuntu:~$ glxinfo
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
williamd@williamskubuntu:~$                                

```

---

### Post by tseliot on 2006-05-20
[QUOTE=Your Name Is]```

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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

Currently checking status of GLX

And it is installed.

EDIT:
```

williamd@williamskubuntu:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
williamd@williamskubuntu:~$ glxinfo
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x57 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
williamd@williamskubuntu:~$                                

```[/QUOTE]
Why did you do a sudo nvidia-glx-config enable ???

Didn't you try my script?

---

### Post by Wr8EYilK8Y on 2006-05-20
Your script gave an error. Could not find some nvidia configuration.
I installed the drivers by hand (which your script did download before blowing up). Then I ran the command expecting it to lock the konsole (the one given by nvidia-glx-config enable) but it worked this time. OpenGL works again. Thank you.


How can I make a script to do this?
```

su (password)
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
sudo sh NVIDIAINSTALLER
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo nvidia-glx-config enable

```

---

### Post by tseliot on 2006-05-20
[QUOTE=Your Name Is]Your script gave an error. Could not find some nvidia configuration.
I installed the drivers by hand (which your script did download before blowing up). Then I ran the command expecting it to lock the konsole (the one given by nvidia-glx-config enable) but it worked this time. OpenGL works again. Thank you.


How can I make a script to do this?
```

su (password)
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
sudo sh NVIDIAINSTALLER
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo nvidia-glx-config enable

```[/QUOTE]
My script already does it. Instead of doing the export CC thing, my script makes a symbolic link to gcc-3.4 (which then is restored to 4.0).

I would really like to know what's the error your computer complained about (so as to improve my script)

---

### Post by Wr8EYilK8Y on 2006-05-22
It was a missing nvidia-config error, not sure what it was. I can't get it again (because the drivers and all are already installed). Next time I do, I'll drop you a PM, okay?

---

