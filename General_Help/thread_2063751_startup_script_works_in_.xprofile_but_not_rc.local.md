---
title: "startup script works in .xprofile but not rc.local"
date: 2012-09-27
forum: General Help
---

### Post by RFRFG on 2012-09-27
how can i get it to work in rc.local?

[SIZE="3"]**rc.local**[/SIZE]
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
xrandr --newmode "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
xrandr --addmode VGA1 1280x1024
xrandr --output VGA1 --mode 1280x1024
exit 0
```

[SIZE="3"]**.xprofile**[/SIZE]
```
xrandr --newmode "1280x1024"  108.88  1280 1360 1496 1712  1024 1025 1028 1060 $
xrandr --addmode VGA1 1280x1024
xrandr -s 1280x1024
```

[SIZE="3"]**xrandr with rc.local (but not .xprofile)**[/SIZE]
```
xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        59.9 +
   640x480        59.9 +
   1024x768       59.9  
   800x600        59.9  

```

[SIZE="3"]**xrandr with .xprofile**[/SIZE]
```
xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
LVDS1 connected (normal left inverted right x axis y axis)
   1024x768       60.0 +
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1280x1024      60.0* 
DVI1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)

```

```
ls -l etc/rc.local
-rwxr-xr-x 1 root root 468 Sep 26 10:01 etc/rc.local

```

---

### Post by dcstar on 2012-09-28
> **RFRFG said:**
> how can i get it to work in rc.local?
..........

You don't. rc.local can be executed before the X system starts, and with any X commands you need to specify the device.

rc.local is not really the appropriate the place for any graphical commands.

---

### Post by RFRFG on 2012-09-28
thank you very much, so just stick with .xprofile?

---

### Post by ringding on 2012-10-26
Try adding a 5 second pause before the script to be run.  Sometimes rc.local runs too soon....

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sleep 5 
<script to run>
exit 0
```

---

### Post by mali2297 on 2012-10-26
I would not suggest to use rc.local. There are a few alternatives given here:
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently](https://wiki.ubuntu.com/X/Config/Resolution#Setting_xrandr_changes_persistently)

---

