---
title: "Monitor disfunction?"
date: 2010-08-20
forum: General Help
---

### Post by dek8 on 2010-08-20
I have a fairly new Samsung 2233RZ 120hz lcd hooked up to a GeForce 8800gt...

When i click on the Brightness and Contrast controls on the monitor it gives me "Not available"... 

Does the linux nvidia drivers disable my monitor functions? is my monitor improperly configured? do i need to take some steps in setting up my monitor?

there are some tiny white scanlines going through the display horizontally if i look real close...      


anyone got any ideas?


minimimalist ubuntu 10.04/XFCE4
same happend on ubuntu 10.04 gnome... with or without the geforce drivers.

---

### Post by dek8 on 2010-08-20
something with the nvidia drivers... 

195. got scanlines but everything else works good. also no monitor brigtness or contrast settings.

173. will only run 120hz in native resolution.

256. wont boot after saving the settings to x.

---

### Post by LowSky on 2010-08-20
make sure your opening nvidia settings with gksu (graphical sudo), otherwise you cannot save the Xorg file.

open a terminal and type this to open
```
gksu nvidia-settings
```

lastly most monitors will not run at full refresh rate if you do not use the recommended resoluiton, and if you try to set manually set it it can cause damage to the LCD. Just a warning.

---

### Post by realzippy on 2010-08-20
*make sure your opening nvidia settings with gksu (graphical sudo), otherwise you cannot save the Xorg file.*

...that's a relic.Meanwhile you are asked for password when saving
to xorg.conf,no need to open with gksudo....

Suggest to create a bug-report.Open terminal:

```
sudo nvidia-bug-report.sh
```

and post the created log file please...

---

### Post by dek8 on 2010-08-20
well im back to using 195 again... its refresh works good, now... some resolutions wont do 120 tho, and i have no monitor controls for brightness and contrast... 

u want the bug report?

where is it located btw?


something else ive noticied in the display applet for xfce i have 10 diffrent settings ranging from 50-59hz, and another setting of 157hz... the monitor supports 60, 100, 110 and 120.

doesnt all of this have to do with something about some EDID profile for the monitor?

---

### Post by realzippy on 2010-08-20
The bug report is generated in the same directory where you run the command
from,so "vanilla" it is in your user's home folder.

As I understand,the 120 Hz technology -may be wrong- just doubles the frequency internally in the monitor,creating interpolate images to improve movement/blur,but the HDMI/VGA signal remains at 60 HZ.

If there are EDID problems this will occur in the bug file,so post it please!

---

### Post by dek8 on 2010-08-20
dvi dual link
.

---

### Post by realzippy on 2010-08-20
From your bug-report:

Aug 20 14:10:05 NVIDIA(0): Setting mode "DFP:1680x1050_120+0+0

means,if 1680x1050 @ 120 Hz is the monitor's native resolution,everything is o.k.,
also it not claims about a missed EDID from DFP-0...


brightness settings:
Do not have [this]("http://www.google.com/imgres?imgurl=http://www.rancholinux.com.ar/wp-content/uploads/2007/05/nvidia-settings.png&imgrefurl=http://ubuntuforums.org/showthread.php%3Ft%3D598439&usg=__DmhDLtTgkSxPMo1CHt5kwVUS9Pc=&h=338&w=579&sz=157&hl=de&start=0&zoom=1&tbnid=CIorZfzjCxjVFM:&tbnh=128&tbnw=219&prev=/images%3Fq%3Dnvidia-settings%2Bbrightness%26um%3D1%26hl%3Dde%26client%3Dubuntu%26sa%3DN%26channel%3Dfs%26biw%3D1680%26bih%3D836%26tbs%3Disch:1&um=1&itbs=1&iact=rc&dur=74&ei=L6JuTNGAMNW7jAe-maT7CA&oei=L6JuTNGAMNW7jAe-maT7CA&esq=1&page=1&ndsp=27&ved=1t:429,r:6,s:0&tx=72&ty=32")?:

---

### Post by dek8 on 2010-08-20
no, the nvidia settings applet is fine, its on the monitor, when i turn on the controls on it for brightness and contrast the osd on the monitor says Not Available. 

in both 173 and 256 i had the option to use the monitor controls and the scanlines were gone. on 195 i got scanlines and no monitor controls.

---

### Post by realzippy on 2010-08-20
Then why not stay with 173.xx ?
No "scanlines",native resolution in 120 Hz....everything fine !?

if 256.xx crashes after saving to xorg.conf,you could try to install 256.xx
and use the xorg.conf file made by 173.xx......

---

### Post by dek8 on 2010-08-20
basically for quake live, if i run 60hz its real laggy and choppy on this monitor, and its what i bought it for. native is slow too....


Could u make an EDID zippy? i read up some place that we could force x to run from the custom EDID instead of the monitors chip... cant find the link now ill look for it...

im really new to linux, just started using it since i got tired of firefox crashing all the time, starting to like it. think i will swap to linux. just keep a 7 installation for games. and maybe get a ps3 now since they hacked it.

---

### Post by dek8 on 2010-08-20
found this...

[I]Option "UseEdidFreqs" "boolean"

    This option controls whether the NVIDIA X driver will use the HorizSync and VertRefresh ranges given in a display device's EDID, if any. When UseEdidFreqs is set to True, EDID-provided range information will override the HorizSync and VertRefresh ranges specified in the Monitor section. If a display device does not provide an EDID, or the EDID does not specify an hsync or vrefresh range, then the X server will default to the HorizSync and VertRefresh ranges specified in the Monitor section of your X config file. These frequency ranges are used when validating modes for your display device.

    Default: True (EDID frequencies will be used)[/I]

[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/appendix-b.html)

---

### Post by realzippy on 2010-08-21
I think there is no problem reading the edid file...otherwise nvidia-bug report would have complained.In Nvidia-settings you can [acquire the monitors edid]("http://img236.imageshack.us/img236/4779/nvidiasettingik4.png"),think there will no difference but you can try...

Why not using the 173.xx driver where everything is ok?(Or do I understand wrong?)

Using or creating a custom EDID could easily destroy your monitor.You can compare the EDID acquired by 173.xx and 195.xx,but there will be no difference I think..
maybe it is worth a test,but I would prefer comparing/swapping the xorg.conf files created by the different drivers...



OFFTOPIC:

BTW,what's your name in Quakelive?

---

### Post by dek8 on 2010-08-21
i looked at the xorg config and its about the same. i cant do 120hz in anything but native with 173 or i would use them.

how often does nvidia drivers get released officially for linux? 
maybe just wait for them and see if they fix it properly.

the 195 are good enough now, i got contrast and brightness in the nvidia applet, its not a biggie, and the scanlines are too small to boughter me. and im real happy with linux otherwise so...


dek88 in ql

---

### Post by realzippy on 2010-08-21
...isn't native resolution 1st choice?

...dunno,but they are fast,especially when there is a bug ("scanlines"),it is
normally corrected a few days later.
Another idea is to test the drivers from [xswat]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").


BTW,check the [NVforum]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")..

..pleased to meet you in QL...

---

### Post by dek8 on 2010-08-22
thanks for the links. im trying over at nvforums, tried those 256 from xswat, they basically went just like the official drivers.

yes, native is the first one.

---

### Post by dek8 on 2010-09-02
basically putting in  

Option         "UseEdidFreqs" "no" under the display adapter and VertRefresh     120.0 under the monitor settings in xorg.conf fixed this for me with the new 256 drivers.

---

