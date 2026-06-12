---
title: "Sansui HDLCD1955C xorg.conf"
date: 2012-02-10
forum: General Help
---

### Post by LinGNUbie on 2012-02-10
For all of us who have a Sansui HDLCD1955C Flatscreen as a monitor, here is a generic xorg.conf file that will give you the native 1368x768 resolution (Tested with 9.04 through 11.10, also works with HDLCD185W):


```
Section "Monitor"
    Identifier	"Configured Monitor"
    Vendorname	"Sansui"
    Modelname	"HDLCD1955C"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
    Modeline "640x480_72.00"   29.50  640 664 728 816  480 483 487 503 -hsync +vsync
    Modeline "640x480_75.00"   30.75  640 664 728 816  480 483 487 504 -hsync +vsync
    Modeline "720x400_70.00"   26.25  720 744 808 896  400 403 413 420 -hsync +vsync
    Modeline "800x600_56.00"   35.00  800 832 904 1008  600 603 607 623 -hsync +vsync
    Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
    Modeline "800x600_72.00"   47.00  800 840 920 1040  600 603 607 628 -hsync +vsync
    Modeline "800x600_75.00"   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync
    Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Modeline "1024x768_70.00"   75.25  1024 1080 1184 1344  768 771 775 802 -hsync +vsync
    Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
    Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
    Modeline "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
    Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
EndSection

Section "Screen"
    Identifier	"Default Screen"
    Device	"Configured Video Device"
    Monitor	"Configured Monitor"
    Defaultdepth	24
    SubSection "Display"
    Depth	24
    Modes	"1360x768@60"	"1280x768@60"	"1280x720@60"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"800x600@75"	"800x600@72"	"800x600@60"	"800x600@56"	"720x400@70"	"640x480@72"	"640x480@60"
    EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

*Suggest this be made a sticky.

---

