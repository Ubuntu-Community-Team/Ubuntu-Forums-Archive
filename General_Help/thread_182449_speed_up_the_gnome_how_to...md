---
title: "speed up the gnome how to.."
date: 2006-05-26
forum: General Help
---

### Post by umen on 2006-05-26
Hello all 
im new to ubuntu . i installed ubuntu on p3 1000 whit 1 giga ram and every thing is great but the graphics are very slow , like runing windows 98 on 486 
i sure i can some how configure the system to act faster i dont need fency graphics 
only minimum. 
i change some config with hdparm and its looks like this : 
sudo hdparm /dev/hda

/dev/hda:
 multcount    = 16 (on)
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 58168/16/63, sectors = 58633344, start = 0


what else i can do to make the system faster ? 
thanks

---

### Post by Perfect Storm on 2006-05-26
Installing linux-686 and installing the graphic-card also do the trick.
"Bum" to disable/enable stuff.
Use epiphany-browser instead of firefox.
Compile your own kernel is a great thing to speed things up.

---

### Post by umen on 2006-05-26
Hello and tnx for the fast reply 
im newbee in the linux world . 
what do you mean by : 
1.Installing linux-686 and installing the graphic-card also do the trick.?
2."Bum" to disable/enable stuff.? 

and is there any good tutorials about compiling the kernal ? 
is there any ubuntu buildin tools for speeding things up? 
thanks

---

### Post by bluenova on 2006-05-26
I think that main thing with a fast system like that will be installing the proper graphic card drivers. Do a search on the forum with your graphics card like '[nvidia](http://ubuntuforums.org/showthread.php?t=75074)' etc.

---

### Post by Perfect Storm on 2006-05-26
heh, that link can really scare off newbies ;)

The easist if you have a Nvidia card - Open the terminal (Application tab ---> Accessories --->terminal) and write:
```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable

```

reboot.

Bum is a graphical runlevel editor. To install it make sure you have universe enable in your sourcelist.
```
sudo apt-get install bum
```

You can now find bum in System tab ---> Adminstration
or the faster way: write **gksudo bum** in the terminal.


Linux-686 - (kernel optimized for Pentium and up and it support 1G ram and up)

```
sudo apt-get install linux-686
```
reboot.

oh by the way linux is case sensitive, just in case.

---

### Post by umen on 2006-05-27
when i try to "make udo nvidia-glx-config enable "
im geting : 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

what do i need to here ?

---

### Post by Perfect Storm on 2006-05-27
```
sudo gedit /etc/X11/xorg.conf
```

Under Section "Device" change       Driver         "nv"  to Driver         "nvidia"


Save and exit.
reboot.

---

