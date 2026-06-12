---
title: "Screen resolution not showing all options"
date: 2011-08-13
forum: General Help
---

### Post by halon314 on 2011-08-13
I have yet to install Ubuntu on a machine that shows screen resolution options higher than 1024x768.  Is there a (GUI) way to turn on the missing options?  I'd rather not have to go into that while xorg.conf thing if I don't have to.  In other operating systems, I load it and set the resolution to what I want, they just show up.  Why is it so hard in Ubuntu (and most Linux's in general)?

---

### Post by CatKiller on 2011-08-13
> **halon314 said:**
>  Why is it so hard in Ubuntu (and most Linux's in general)?

Because your monitor is broken.

It's perfectly possible for monitors to advertise the resolutions that they are capable of. This is done through a mechanism called EDID. This means that everything works automatically with no need for configuration, and this is what happens in the majority of cases. Some monitors, like yours, don't do this, because the manufacturer is either cheap or incompetent.

In Windows you get around this failing by installing a "driver" which is really just registry entries of the information that should have been provided through EDID.

In Linux you can do something similar by putting that information in xorg.conf. If you tell us more about your hardware we might be able to help you through it.

---

### Post by halon314 on 2011-08-14
Thanks for the reply.  It's odd that Windows can work around that problem and Linux can't. I would think linux would make it easier to use older hardware. 

In my case, the on-board video is showing as an Intel 82865G Graphics Controller and the monitor is a Westinghouse - LCM-19w4.  Is it possible to manually configure Ubuntu to work with this combination of hardware?

---

### Post by realzippy on 2011-08-14
Open a terminal,type

```
xrandr -q
```
post output.

BTW,which ubuntu version?

---

### Post by halon314 on 2011-08-14
The output from  xrandr -q  is as follows:
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9

---

### Post by realzippy on 2011-08-14
run these commands:

```
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```
```
xrandr --addmode VGA1 1440x900_60.00
```
```
xrandr --output VGA1 --mode 1440x900_60.00
```

If it works,do nothing.
Post (then we make it permanent)..

---

### Post by CatKiller on 2011-08-14
> **halon314 said:**
> Thanks for the reply.  It's odd that Windows can work around that problem and Linux can't. I would think linux would make it easier to use older hardware. 


It's not a question of old hardware, it's a question of broken hardware. The EDID spec is 16 years old.

The workaround for Windows is just as ugly as the workaround with X, it's just that manufacturers are more likely to bother to do it for you with Windows because it would be suicide for them not to.

---

### Post by halon314 on 2011-08-14
FANTASIC!!  Now I have 1440x900!  Will this be persistent after a reboot?

---

### Post by Duncan Williams on 2011-08-14
have a read of this:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

He's pretty zippy, hey...

---

### Post by realzippy on 2011-08-14
@catkiller

Pleased to meet you ;-)
I also prefer xorg.conf hack to fix resolution.
..but for some reason the mods don't want this.
Few threads ago when I suggested to create xorg.conf bodhi zazen jumped in claiming that xorg.conf is "depreciated" giving this [link]("http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/").
zippy

---

### Post by realzippy on 2011-08-14
> **halon314 said:**
> FANTASIC!!  Now I have 1440x900!  Will this be persistent after a reboot?
No.
Do what duncan's link suggests:

```
gksudo gedit /etc/gdm/Init/Default
```

.
Watch out for

PATH=”/usr/bin:$PATH”
OLD_IFS=$IFS

and paste in your 3 working xrandr commands 

so it looks like:




```
.............
PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA1 1440x900_60.00
xrandr --output VGA1 --mode 1440x900_60.00

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
...........
```

close file saving changes.

---

### Post by realzippy on 2011-08-14
@Duncan Williams

> **Duncan Williams said:**
> have a read of this:
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

He's pretty zippy, hey...

..problem with your link is that it won't work since it mixes up x and ×
like many xrandr howtos (all copied from same bad source).

Offtopic:
Btw,you know Bill Griffith ?

---

### Post by Duncan Williams on 2011-08-14
Bill Griffith doesn't ring a bell.
Pity about the xrand addmode link, I thought given it was respected linux site that it would be solid command structure.
It happens to often...
sudo bla bla bla .. will fix your problem..  no, just gave me another ten...

---

### Post by CatKiller on 2011-08-14
> **realzippy said:**
> @catkiller

Pleased to meet you ;-)
I also prefer xorg.conf hack to fix resolution.
..but for some reason the mods don't want this.
Few threads ago when I suggested to create xorg.conf bodhi zazen jumped in claiming that xorg.conf is "depreciated" giving this [link]("http://blog.bodhizazen.net/linux/use-xrandr-to-set-a-screen-resolution/").
zippy

xrandr and xorg.conf are complementary, as we've found in previous threads. xrandr doesn't do anything without a functioning X server, but it addresses limitations of the fact that xorg.conf is static; without xrandr, changing resolution or rotating the display require restarting the X server.

xorg.conf isn't deprecated in favour of xrandr, it's deprecated in favour of efforts like Project Wayland. bodhi.zazen's a nice guy and his contributions to threads are generally good ones, but he's not correct that the myriad xrandr configuration options are any less intimidating to a new user than editing a text file. To a new user, it's all intimidating. The automatic methods are clearly better from that point of view, but it does require functioning hardware.

But I fear we're getting dangerously off-topic :)

---

### Post by realzippy on 2011-08-16
Can you set thread as solved please ? (Threadtools)




If you should have not noticed due to us being little off-topic,the
"permanent" solution is post #11
..have fun.

---

