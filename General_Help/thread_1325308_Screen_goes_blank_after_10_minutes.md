---
title: "Screen goes blank after 10 minutes"
date: 2009-11-13
forum: General Help
---

### Post by JackTheKnife on 2009-11-13
I have an issue on DELL Inspiron 1100 laptop used as a kiosk machine. When is on idle the screen goes blank after 10 minutes. I have turned off a screen saver and a power management for a screen. Any idea what can be wrong? Thanks

---

### Post by sisco311 on 2009-11-13
Open a terminal and post the output of:
```
xset q | grep -A 3 DPMS
```

---

### Post by KayakJim on 2009-11-13
If you are sure that Power Management and Screen Savers are disabled, check the video card control panel (e.g. ATI Catalyst control center or nVidia's, depending upon your card) to see if they do not have a setting for blanking the screen after a period of time.

---

### Post by JackTheKnife on 2009-11-13
> **sisco311 said:**
> Open a terminal and post the output of:
```
xset q | grep -A 3 DPMS
```

I have got this:

```

Stanby:0 Suspend:0 Off:0

DPMS is Enabled
Monitor is On

```

---

### Post by JackTheKnife on 2009-11-13
> **KayakJim said:**
> If you are sure that Power Management and Screen Savers are disabled, check the video card control panel (e.g. ATI Catalyst control center or nVidia's, depending upon your card) to see if they do not have a setting for blanking the screen after a period of time.

It is Intel Extreme Graphics so I don't know what I need to look for.

---

### Post by sisco311 on 2009-11-13
Well, run:
```
xset q
``` in a terminal.

If you see something like:
```
...
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
...

```
then you have to disable the screensaver:
```
xset s 0 0
```
to make it permanent edit the ServerFlags section in th xorg.conf file:
```

Section "ServerFlags"
#...
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection

```

[http://www.shallowsky.com/linux/x-screen-blanking.html]("http://www.shallowsky.com/linux/x-screen-blanking.html")

[http://www.ubuntugeek.com/workaround-for-feisty-screensaver-bug.html]("http://www.ubuntugeek.com/workaround-for-feisty-screensaver-bug.html")

---

### Post by JackTheKnife on 2009-11-13
Thanks.

---

### Post by last1 on 2011-02-08
I refer to this thread every single time I do a new install, that big dpms page is too wordy to reference and these options work great. Just leaving a comment here so it'll be easier for me to find it later. 

Oh and it's good to note as well that in the above ServerFlags code, the quotes around ServerFlags need to be replaced with regular quotes or it won't work. Those are some sort of special quotes using unicode or something and xorg doesn't like it. It should be ```

Section "ServerFlags"
#...
        Option          "BlankTime"     "0"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "0"
EndSection



```

---

### Post by Miller1 on 2013-02-15
Since Ubuntu 9.10 we have the option of using xorg.conf or not, I have not used it and instead, to turn off the screensaver and power management I have put the following commands in the "Startup Applications" which is accessed via the list of options that comes up when you click on the icon to get to the Logout / Suspend etc menu.

To disable DPMS:

xset -dpms


To turn off the screensaver:

xset s off


Once the above 2 commands are added to the startup command list and the machine rebooted, the screen stays alive.

BTW, to access the GUI for the screensaver, it is not available in the expected place (System Settings) and you have to access it via Dash Home and type 'screensaver'. This is the xscreensaver preferences dialogue gui. The startup settings will of course override whatever this screensaver is set to, which is what I wanted.

---

