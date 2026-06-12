---
title: "Controlling brightness of screen of mu Ideapad"
date: 2010-03-09
forum: General Help
---

### Post by gunjannigam on 2010-03-09
I am using Ubuntu 9.04 Jaunty Jackalope on my Lenovo IdeaPad S10-2. I have to set brightness of screen using command line argument, as the Fn key of my keyboard is not working.
I tried various options such as
```

echo -n 40 > /proc/apci/video/OVGA/LCD/brightness

```
It changed the current value in the file to 40 from 100 but the brightness of the screen remained same.

Then I tried using 
```

     "xrandr --prop"

```
It said
```

     BACKLIGHT: 5 (0x00000005)    range:  (0,10)

```

Then I used
```

xrandr --output LVDS --set BACKLIGHT 7

```
the value changed but still the brightness of screen remained the same


Then I also tried 
```

     setpci -s 00:02.0 f4.b=01

```
00:02.0 was the address of VGA device returned by lspci 

It changed the value but still the brightness of screen is constant. 
I tried all the commands on Ubuntu Netbook Remix 9.04 also. There also these commands didn't worked
Do I need to install some other package so that the brightness of screen is changed using command line?

---

