---
title: "Xorg DPI settings not being used"
date: 2010-01-25
forum: General Help
---

### Post by officeboy on 2010-01-25
First off my monitor is a 720p plasma, native resolution is  1024x768 and yes it's 16:9. Video is onboard ATI 4200 (AMD780G). and I've tried the fglrx, ati, and radeon drivers. So I would like my dpi settings to reflect that the pixels are longer horizontally (that there are less of them)

So i've been changing DisplaySize, and tweaking X with other options like [Option   "NoDDC" "true"] etc.  Nothing seems to change the display.

So then I check xdpyinfo and it reports what I have in X and it's what i've configured.:confused:.  So I try wiping out X and seeing what it picks up and what do you know, it's auto-detecting everything fine. :confused::confused:
```
screen #0:
  dimensions:    1024x768 pixels (160x90 millimeters)
  resolution:    53x95 dots per inch
```

So the problem, it's not using these settings.  I can change the DisplaySize to 1000 10  or 10 1000 and the display does not change, but xdpyinfo does correctly report what I've entered. 

What else could be driving the display?

---

### Post by officeboy on 2010-01-26
Ok. the radeon drivers do just seem to ignore xorg.conf

```
screen #0:
  dimensions:    1024x768 pixels (271x203 millimeters)
  resolution:    96x96 dots per inch

```
```
Section "Monitor"
        Identifier  "TV"
        VendorName  "Samsung"
        ModelName   "PN42B450"
        HorizSync   30 - 55
        VertRefresh 60
#   For 1024x768 at 100dpi  (16:9)
        DisplaySize  346        195
EndSection

```
Am i missing something? (that is my whole xorg.conf btw)

---

### Post by officeboy on 2010-01-26
With the fglrx things seem like they would be better..
```
screen #0:
  dimensions:    1024x768 pixels (160x90 millimeters)
  resolution:    163x217 dots per inch

```

```
Section "Monitor"
        Identifier  "TV"
        VendorName  "Samsung"
        ModelName   "PN42B450Colormeister 5000"
        HorizSync   30 - 55
        VertRefresh 60
        DisplaySize  346        195
        #   For 1024x768 at 100dpi  (16:9)
EndSection

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "fglrx"
EndSection


```

It's not using that screen setting thats for sure.

---

### Post by officeboy on 2010-01-26
And xorg can be updated if i get my naming and stuff all right... but it doesn't work.  Right now I'm typing this at
```
screen #0:
  dimensions:    1024x768 pixels (1346x195 millimeters)
  resolution:    19x100 dots per inch

```

And you would think it would make a difference as far as readability goes.
```
Section "Monitor"
        Identifier  "Default Monitor"
        VendorName  "Samsung"
        ModelName   "PN42B450Colormeister 5000"
        #HorizSync   30 - 55
        #VertRefresh 60
        DisplaySize  1346       195
        #   For 1024x768 at 100dpi  (16:9)
EndSection

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        Monitor         "Default Monitor"
EndSection

```

Help.

---

