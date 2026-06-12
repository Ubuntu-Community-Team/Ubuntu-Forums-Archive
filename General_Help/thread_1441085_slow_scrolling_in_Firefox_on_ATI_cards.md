---
title: "slow scrolling in Firefox on ATI cards"
date: 2010-03-28
forum: General Help
---

### Post by DigitalisCZ on 2010-03-28
It took me some time to figure this out and I hope you may find this helpful for you as well. I am using rather old Dell C640 laptop with ATI Radeon Mobility M7 graphics but I believe this can be used for other ATI graphics cards too.

I recently upgraded to Xubuntu 9.10. Overall impression was good but I was experiencing issues with screen notification which were incorrectly displayed. After searching trough few posts I edited xorg.conf to alter video acceleration method to EXA.

Fist, as there is no xorg.conf in /etc/X11/ by default, generate one:
```
$ sudo Xorg -configure
```

Then edit the following lines as root: 
```
Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility M7 LW [Radeon Mobility 7500]"
	BusID       "PCI:1:0:0"
        **Option     "AccelMethod" "EXA"**
EndSection

```

Event though it solved display of notifications it also caused significant drop down in scrolling performance in Firefox - my version is 3.5.8 but I guess this applies to other version too. It took me quite while before I realized this is related together....

So the remedy is change the xorg.conf line now to XAA:
```
  Option     "AccelMethod" "XAA"
```

and to replace xubuntu 9.10 default notifications osd-notify with notification-daemon:
```

$ sudo apt-get remove notify-osd notify-osd-icons

$ sudo apt-get install notification-daemon
```

After this it finally works to my satisfaction....

---

