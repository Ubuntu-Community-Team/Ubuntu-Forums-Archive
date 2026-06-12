---
title: "I can not get screen resolution above 800x600"
date: 2011-02-11
forum: General Help
---

### Post by asifnaz on 2011-02-11
here is output of lspci

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 21)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0d.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
00:0f.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 21)
```how can I get resolution more than 800X600 . 

I am not a very experienced user so I will really appreciate if you help me by step by step procedure .

Thank you

---

### Post by vat with tux on 2011-02-11
Go to system>preferences>monitors

There u can set resolution .:)

---

### Post by grahammechanical on 2011-02-11
Please confirm that the monitor will work effectively at screen resolutions greater than 800x600 and that the video/graphic card can run the monitor at resolutions greater than 800x600.

A monitor can be damaged if it is run at a resolution greater than the optimum setting defined by the manufacturer. If the OS is preventing you from setting a higher resolution it could be doing it to prevent you from damaging the monitor.

Some distributions allow the user to set the monitor resolution. This information is then stored in a configuration file which is read at boot up.

It is my understanding that Ubuntu does things differently. I think at boot time the operating system uses the video card to access information stored in the monitor and uses this information to configure the display. I think that it does this every time we boot. This is why we can attach a new monitor and Ubuntu will recognize it and run it. I may be wrong, of course.

You will need to provide more information about your computer, its video card and the monitor. Try checking out the websites of the manufacturers.

Regards.

---

### Post by realzippy on 2011-02-11
*VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP*

Think I can help:
Open a terminal,type (mind that capital X ):
```

gksudo gedit /etc/X11/xorg.conf
```

An empty file will pop up.
Paste all this into the empty file:

```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1280x1024"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection
```

If you want an other resolution than 1280x1024,change it in the line:
"Modes 1280x1024" to your needs,eg "Modes 1024x768";close the file
saving changes.Reboot & pray.
If (don't think so) you cannot boot afterwards,boot in recovery mode,drop to shell,log in and delete the xorg.conf:

```
sudo rm /etc/X11/xorg.conf
sudo reboot
```



This should work on nearly any LCD monitor;if you run an older VGA,the hsync/VertRefresh value has to be changed,but then we need to know which monitor you use.

---

### Post by asifnaz on 2011-02-11
> **vat with tux said:**
> Go to system>preferences>monitors

There u can set resolution .:)

maximum choice I am given is 800X600

I think this is something to do with ( SiS 630/730  ) controller

---

### Post by realzippy on 2011-02-11
*I think this is something to do with ( SiS 630/730 ) controller*

Indeed.
Please test my suggestion from post #4

---

### Post by asifnaz on 2011-02-11
> **realzippy said:**
> *I think this is something to do with ( SiS 630/730 ) controller*

Indeed.
Please test my suggestion from post #4

Thank you so much . I really appreciate your help . 

a friend of mine told me that 

```
dpkg-reconfigure xserver-xorg
```

might also do the job 

thank you again .

---

### Post by realzippy on 2011-02-11
> **asifnaz said:**
> Thank you so much . I really appreciate your help . 

a friend of mine told me that 

```
dpkg-reconfigure xserver-xorg
```

might also do the job 

thank you again .

Maybe it works also,but you had to run it with "sudo"  :
*sudo dpkg-reconfigure xserver-xorg*
You can try it if suggestion from post #4 does not work...anyway,I
would suggest *sudo Xorg -configure* instead,but first test my xorg.conf...

---

