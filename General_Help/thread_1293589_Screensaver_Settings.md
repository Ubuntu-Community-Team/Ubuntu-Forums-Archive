---
title: "Screensaver Settings"
date: 2009-10-17
forum: General Help
---

### Post by leftfootleashed on 2009-10-17
Hi,

I have a box running Jaunty that I use as a media player so I don't want a screensaver to be activated or the display to be put to sleep EVER.

I disabled 'activate screensaver when computer is idle' under Screensaver Preferences in the Control Centre, and set the 'put computer/display to sleep...' settings to 'Never' under Power Management.

This worked for a while, but then I started getting a blank screen after so long, though the settings hadn't changed.

I started the Screensaver Preferences from the terminal and found that they had reverted, so I disabled the screensaver, etc. and that worked until I restarted.

Now all the settings are as they should be, but I still get a blank screen after so long. Anyone got any ideas?

Cheers,
Dave

---

### Post by Sam on 2009-10-17
Not sure about this, but try```
xset -dpms s off
```

---

### Post by leftfootleashed on 2009-10-19
Thanks a lot, that seems to work. It seems to revert with a restart, though. Is there a way to permanently change the setting, other than having the command run at boot?

---

### Post by linxuser on 2009-10-20
Try changing your X configuration file to set the DPMS to off.  Probably the quickest surest way to handle it.
If you are not familiar/comfortable with vim, you can substitute the graphical text editor gedit - just change vim to gedit in the command below and remember to save and close the editor window to return.
In a terminal, edit the xorg.conf file as shown below:
```
sudo vim /etc/X11/xorg.conf
```You'll be looking for the Monitor section labeled as **Section "Monitor"**.
If there is more than one, edit both by adding the following text:
```
Option  "DPMS" "off"
```The option may already be present, in that case, just change the value to off.
It may look similar to the below snippet:
```
Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "off"
EndSection
```If you want to find more options to try out in xorg.conf, run the following command in a terminal
```
man xorg.conf
```

---

### Post by leftfootleashed on 2009-10-21
Thanks for your reply. I tried adding the OPTION line you suggested, and then also to the screen section, but neither has worked.
My xorg.conf now looks like:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"	"OFF"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"DPMS"	"OFF"
EndSection
```

Any thoughts?

---

