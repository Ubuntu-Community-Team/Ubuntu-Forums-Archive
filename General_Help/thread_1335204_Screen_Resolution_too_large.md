---
title: "Screen Resolution too large"
date: 2009-11-23
forum: General Help
---

### Post by mrfotheringham on 2009-11-23
I have reinstalled 9.10 and now my screen resolution too large also my screen Hz is limited to 60hz.
Please help

---

### Post by Giblet5 on 2009-11-23
[One of many howtos]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145").

---

### Post by mrfotheringham on 2009-11-23
I have a non branded crt monitor which is fairly old is there a way of finding the info another way?

---

### Post by Giblet5 on 2009-11-23
The HOWTO shows you two ways: one, having the specs of your monitor, and the other knowing what your monitor can do (resolution-wise).

If you're missing BOTH, then you can try:

Experimenting! (Get familiar with Ctrl+Alt+F1 and Ctrl+Alt+F7 to flip back and forth between the console and the graphics screen)

Try bumping the VESA resolution one step... You're at 1024x768@60hz, try 1164x800@75. 1280x1024@72. etc etc

cvt command/edit xorg.conf/try it/rinse/repeat

When the screen goes black, or displays "OUT OF RANGE", or blows purple smoke, you've gone too far, so back off to the previous settings.

---

### Post by mrfotheringham on 2009-11-23
Thanks will follow advice and hope not to get smoked!

---

### Post by jwmuelle on 2009-11-23
xrandr should also be able to display the current display capabilities... 

Here's output from my Acer Aspire 5100 laptop with Radeon card utilizing dualhead capabilities:

$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 1700, maximum 2048 x 2048
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9* 
   1280x1024      75.0     60.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1280x800+160+900 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
S-video disconnected (normal left inverted right x axis y axis)

Note the display names if you're going to use xrandr to set specific screen size, in my case LVDS is the laptop display, VGA-0 is the external monitor:

xrandr --output VGA-0 --mode 1024x768

my standard setting is:
xrandr --output LVDS --auto --output VGA-0 --auto --above LVDS

I have my VGA monitor on a riser behind the laptop with the end effect of the VGA monitor being above my laptop screen.

Or... use the system>>preferences>>display application to use a gui to configure the screens.  This app has the added feature for dualhead users of creating a basic xorg.conf if the resulting virtual size of the 2 monitors needs to be increased.  This is my entire xorg.conf on this system, created by this app.

$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2048 2048
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection


My laptops with integrated Intel graphics end up using slightly different names for the monitors:  ex. LVDS1 for laptop, VGA1 for external.

jw

---

### Post by mrfotheringham on 2009-11-23
Thanks all. I have followed Giblet5s recs and with great success. I did find a makers mark and site said resolution 1280x1024. However now I could possibly view entire pages of the Encylopedia Brittanica! Do I just return to Gegit to now lower res?

All help app

---

### Post by Giblet5 on 2009-11-23
> **jwmuelle said:**
> xrandr should also be able to display the current display capabilities...

When DDC/CI and EDID protocols fail (non-compliant monitor, bad cable, etc), xrandr will do nothing (which is exactly why this problem appears in the first place). In these cases, all xrandr can do is determine some capabilities of the *graphics card* (not the monitor), which is all but useless since almost any modern graphics card can exceed the capabilities of commercially-available display devices.

> **mrfotheringham said:**
> Thanks all. I have followed Giblet5s recs and with great success. I did find a makers mark and site said resolution 1280x1024. However now I could possibly view entire pages of the Encylopedia Brittanica! Do I just return to Gegit to now lower res?

All help app

You can assume that 640x480@60 is fully supported.

So use cvt to figure out the frequencies for that, then specify a HorizSync and VertRefresh *range*, placing a '- between the lower and higher frequencies.

Then you can switch resolutions using the Gnome Display Settings tool.

---

### Post by mrfotheringham on 2009-11-23
Thanks will amend res

---

