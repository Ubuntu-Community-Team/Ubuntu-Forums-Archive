---
title: "help with screen resolution"
date: 2009-12-24
forum: General Help
---

### Post by markbabc on 2009-12-24
ok so i am very very very new to ubuntu and linux in general. i am currently running ubuntu on my netbook and when i had windows on it i make the screen resolution bigger so that i could see all of the program that i am using and i like having the desktop space. i have looked around and apparently they easiest way to do this is to edit the xorg.conf file but in ubuntu 9.10 there is none and i have tried the methods that people say will get the file there but none are working for me and i was wondering if someone could either explain an easier way to do this or explain how i can make my own xorg.conf file.

---

### Post by labinnsw on 2009-12-25
I strongly doubt that you really don't have an xorg.conf file. Please type
```
gksu gedit /etc/X11/xorg.conf
```
in a terminal. (Applications >> Accessories >> Terminal)

My 9.10 has an xorg.conf file.

---

### Post by labinnsw on 2009-12-26
Sorry for doubting you. Looks like you are not the only one. I have posted my xorg.conf if you like to use it as a template to make yours.[ATTACH]141177[/ATTACH]
Just remove .txt extension.

---

### Post by blackened on 2009-12-26
xorg.conf is being obsoleted. Start here instead -> [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

Shout if you don't understand something. I suggest using xrandr.

---

### Post by markbabc on 2009-12-26
ok i got the xorg.conf file but now i have no idea how to edit it to my liking but i will keep on googleing and i checked out the xrandr thing at that link and i was trying to follow it but i got confused.i took a screen shot of what i was looking at [http://img134.imageshack.us/img134/7951/screenshotvj.png](http://img134.imageshack.us/img134/7951/screenshotvj.png) i am trying to add a new resolution to LVDS1 and i tried the commands that are on the webpage next to the terminal and it added the resolution to TV1.

---

### Post by labinnsw on 2009-12-26
To edit the xorg.conf file go to post # 23 [in this link]("http://ubuntuforums.org/showthread.php?t=1318677&page=4")

A simple xrandr tutorial is [here]("http://solutionz.yolasite.com/linux/add-a-new-screen-resolution-with-the-terminal-on-ubuntu-9-10")

---

### Post by markbabc on 2009-12-27
ok i followed the xrander one to the letter replaceing what they said to put in and i get this [http://img69.imageshack.us/img69/3916/screenshot2x.png](http://img69.imageshack.us/img69/3916/screenshot2x.png) its adding the resolution to TV 1 i want it to add to LVDS1 and its just not going

---

### Post by blackened on 2009-12-27
You haven't been very specific about the resolution you're going for, so I'm going to use a vanilla resolution and you can change it accordingly. Here is the basic chain of events you need to follow:

Get the modeline for the resolution you're after using the gtf command, changing the x,y, and refresh rate values for those appropriate to your system. I will use 800x600@60Hz for this example.

```
gtf 800 600 60
```

Next, create a new mode using the modeline you just generated.
```
xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```

Now, you've created a new mode called "800x600_60.00" with the appropriate modeline..

After that you must attach that new mode to the adapter you want to use it with, so you use the addmode option, referencing the modename and adapter designation (LVDS1 in your case) appropriately:
```
xrandr --addmode LVDS1 800x600_60.00
```

And that's it. You can switch to the new mode with
```
xrandr --output LVDS1 --mode 800x600_60.00
```

Hope this has been a little clearer than the links.

---

### Post by markbabc on 2009-12-30
ok i followed exactally what you said just changing the screen resolution to 1280x1024
this is what i get: (and yes haha my spelling sucks)

```
ghoulmaster@ghoulmaster-laptop:~$ xrander
No command 'xrander' found, did you mean:
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xrander: command not found
ghoulmaster@ghoulmaster-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       59.5*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
ghoulmaster@ghoulmaster-laptop:~$ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

ghoulmaster@ghoulmaster-laptop:~$ xrander --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
No command 'xrander' found, did you mean:
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xrander: command not found
ghoulmaster@ghoulmaster-laptop:~$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
ghoulmaster@ghoulmaster-laptop:~$ xrandr --addmode LVSD1 1280x1024_60.00
xrandr: cannot find output "LVSD1"
ghoulmaster@ghoulmaster-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       59.5*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x133)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz
ghoulmaster@ghoulmaster-laptop:~$ xrandr --addmode LVSD1 1280x1024_60.00
xrandr: cannot find output "LVSD1"
ghoulmaster@ghoulmaster-laptop:~$ xrandr --addmode LVDS1 1280x1024_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26
ghoulmaster@ghoulmaster-laptop:~$ xrandr --output LVDS1 --mode 1289x1024_60.00
xrandr: cannot find mode 1289x1024_60.00
ghoulmaster@ghoulmaster-laptop:~$ xrandr --output LVDS1 --mode 1280x1024_60.00
xrandr: cannot find mode 1280x1024_60.00
ghoulmaster@ghoulmaster-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       59.5*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x133)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz
ghoulmaster@ghoulmaster-laptop:~$ 

```

---

### Post by simonday99 on 2009-12-30
anyone help me to get the maximum resolution for my lcd 20" monitor.

---

### Post by blackened on 2009-12-30
> **markbabc said:**
> ok i followed exactally what you said just changing the screen resolution to 1280x1024
this is what i get: (and yes haha my spelling sucks)...

Tough to decipher all of that. Cut and paste from here to eliminate the typing mistakes. Post back with the output.

```
xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
```

```
xrandr --addmode LVDS1 1280x1024_60.00
```

```
xrandr --output LVDS1 --mode 1280x1024_60.00
```

---

### Post by blackened on 2009-12-30
> **simonday99 said:**
> anyone help me to get the maximum resolution for my lcd 20" monitor.

Gladly, please don't hijack threads though. Start a new thread with a title/first post that clearly describes your problem (please provide as much hardware information as possible) and we'll see what we can do.

---

### Post by markbabc on 2009-12-30
```
ghoulmaster@ghoulmaster-laptop:~$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

ghoulmaster@ghoulmaster-laptop:~$ xrandr --addmode LVDS1 1280x1024_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

ghoulmaster@ghoulmaster-laptop:~$ xrandr --output LVDS1 --mode 1280x1024_60.00
xrandr: cannot find mode 1280x1024_60.00

ghoulmaster@ghoulmaster-laptop:~$ 


```
i just had a thought maybe that resolution is to big for my screen and that might be what the error means but i really dont know

after that code i typed xrandr and it gave me this
```
ghoulmaster@ghoulmaster-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       59.5*+
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x11f)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz
```

---

### Post by blackened on 2009-12-31
> **markbabc said:**
> 
i just had a thought maybe that resolution is to big for my screen and that might be what the error means but i really dont know

This could be the case. You'll have to check your hardware specifications. It might also be that the driver you're using can't handle that resolution on your particular hardware. That's been the case on Windows for me with 1680x1050 on my eee through an external monitor. Ubuntu manages that resolution perfectly on the same hardware though.

---

### Post by markbabc on 2009-12-31
im using the same as you with an eee pc 900 16GB SSD with only 1GB of ram though, how would i find out the driver that im using or would i have to find the box that it came with?

---

### Post by blackened on 2010-01-01
1024x600 is the max native resolution for the EEE900. It can go higher with virtual resolutions that pan as you touch the screen edges, but I've only ever gotten those to work in Windows.

The method I've described above using xrandr works great for assigning unlisted resolutions to external monitors.

---

### Post by markbabc on 2010-01-03
> **blackened said:**
> 1024x600 is the max native resolution for the EEE900. It can go higher with virtual resolutions that pan as you touch the screen edges, but I've only ever gotten those to work in Windows.

The method I've described above using xrandr works great for assigning unlisted resolutions to external monitors.
yea thats what i meant when i said i got it bigger in windows but i guess i will keep looking for a way to do it in ubuntu

---

