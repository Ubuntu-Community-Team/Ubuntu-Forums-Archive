---
title: "Screen size changes every bootup"
date: 2009-09-02
forum: General Help
---

### Post by ryanfx on 2009-09-02
Hi everyone,

I've been having quite an odd issue with my Ubuntu 9.04.  For some reason every other (or third) time I boot up my laptop the visible screen becomes square and doesn't extend to the full resolution I expect of 1366x768.  So essentially there is about an inch or so of black on either side of the screen.  This is a *STOCK* installation and I have not edited the X server.  I will be happy to provide more information or logs, just ask what you need!

I have also attached the xlog from a boot where I got a square screen


```

ryan@TehLaptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

```

```

ryan@TehLaptop:~$ cat /etc/X11/xorg.conf 

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
ryan@TehLaptop:~$ 

```

---

### Post by sully101 on 2009-09-03
I think it has something to do with this in your log file

> (II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output[COLOR="Red"] TV connected[/COLOR]
(II) intel(0): Using fuzzy aspect match for initial modes
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): [COLOR="Red"]Output TV using initial mode 1024x768[/COLOR]

The intel drivers are not the best at the moment. I would suggest putting a modeline and prefered mode in the monitor section of your /etc/X11/xorg.conf

or adding "xrandr -s 1366x768" to your autostarted applications

---

### Post by ryanfx on 2009-09-03
> **sully101 said:**
> I think it has something to do with this in your log file



The intel drivers are not the best at the moment. I would suggest putting a modeline and prefered mode in the monitor section of your /etc/X11/xorg.conf

or adding "xrandr -s 1366x768" to your autostarted applications

xrandr fails because that is not a currently available mode when it boots up in "TV" mode, so I will edit the xorg with a modeline and let you know

---

### Post by BitJunkie on 2009-09-06
I had the same problem with my Toshiba L505 laptop that has Intel GMA4500 graphics. I added the following to my xorg.conf file, and so far it seems to have solved my problem.

```
Section "Device"
    Identifier    "Configured Video Device"
        [COLOR=Red]Option          "Monitor-LVDS"     "Laptop LCD"
        Option          "Monitor-TV"       "TV"[/COLOR]
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

[COLOR=Red]Section "Monitor"
    Identifier    "Laptop LCD"
    Option        "PreferredMode" "1366x768"
EndSection

Section "Monitor"
    Identifier    "TV"
    Option        "Ignore" "True"    
EndSection[/COLOR]

Section "Screen"
    Identifier    "Default Screen"
    [COLOR=Red] Monitor        "Laptop LCD"[/COLOR]
    Device        "Configured Video Device"
EndSection

```

---

### Post by Chicanob12 on 2009-09-09
> **BitJunkie said:**
> I had the same problem with my Toshiba L505 laptop that has Intel GMA4500 graphics. I added the following to my xorg.conf file, and so far it seems to have solved my problem.

```
Section "Device"
    Identifier    "Configured Video Device"
        [COLOR=Red]Option          "Monitor-LVDS"     "Laptop LCD"
        Option          "Monitor-TV"       "TV"[/COLOR]
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

[COLOR=Red]Section "Monitor"
    Identifier    "Laptop LCD"
    Option        "PreferredMode" "1366x768"
EndSection

Section "Monitor"
    Identifier    "TV"
    Option        "Ignore" "True"    
EndSection[/COLOR]

Section "Screen"
    Identifier    "Default Screen"
    [COLOR=Red] Monitor        "Laptop LCD"[/COLOR]
    Device        "Configured Video Device"
EndSection

```


I have the same exact problem on my Lenovo Ideapad Y530 its the[COLOR=Red] same[/COLOR] [COLOR=Red]Graphics Card[/COLOR]. The resolution it is suppose to have is [COLOR=Red]1280 x 800[/COLOR]. It does not even give me the option.  How do I add what you added with the resolution I want instead of the 1366 x 768? I am a very new to Ubuntu please help!

---

### Post by BitJunkie on 2009-09-09
I'm not an expert regarding xorg.conf, but I would think you would change the line that says ```
Option     "PreferredMode"   "1366x768"
``` to ```
Option        "PreferredMode" "1280x800"
``` But since 1280x800 doesn't seem to be a valid option, I would be reluctant to try it.

---

### Post by Chicanob12 on 2009-09-10
> **BitJunkie said:**
> I'm not an expert regarding xorg.conf, but I would think you would change the line that says ```
Option     "PreferredMode"   "1366x768"
``` to ```
Option        "PreferredMode" "1280x800"
``` But since 1280x800 doesn't seem to be a valid option, I would be reluctant to try it.
 
I did try it already, thats exactly what I did. but like you said its not a valid option so no go.  Do you know if there is anyway to maybe add that option? I can give you any information or logs you may need just ask for what you need.  and maybe how to get them lol cause i'm pretty new at this

---

### Post by BitJunkie on 2009-09-11
So far all I've found is this: [http://ubuntuforums.org/showthread.php?t=357641](http://ubuntuforums.org/showthread.php?t=357641). It mentions trying "sudo dpkg-reconfigure xserver-xorg" and "xresprobe". Although the thread is about an nvidia card with unsuccessful results, it might be worth trying. Make sure you back up xorg.conf first.

---

### Post by ariismail on 2009-09-12
I had the same problem in Samsung X360. When I boot Ubuntu, sometimes it used be in 1280x800, but sometimes not. I modified the Monitor section in xorg.conf as follows

```
Section "Monitor"
        Identifier      "Laptop LCD"
        Option          "PreferredMode" "1280x800"
EndSection

```

It seems to be resolved now.

---

### Post by Chicanob12 on 2009-09-12
> **BitJunkie said:**
> So far all I've found is this: [http://ubuntuforums.org/showthread.php?t=357641](http://ubuntuforums.org/showthread.php?t=357641). It mentions trying "sudo dpkg-reconfigure xserver-xorg" and "xresprobe". Although the thread is about an nvidia card with unsuccessful results, it might be worth trying. Make sure you back up xorg.conf first.



THANK YOU SOOOOOOOOOOO MUCH!!! The link is exactly what I needed. "xresprobe" worked right away. not being able to use my whole screen on my laptop was killing me lol. Again thanks everyone for there suggestions and help!

---

### Post by antony_css on 2010-06-22
I can confirm this bug in Lucid Lynx
I am using HP ProBook 4410s

---

