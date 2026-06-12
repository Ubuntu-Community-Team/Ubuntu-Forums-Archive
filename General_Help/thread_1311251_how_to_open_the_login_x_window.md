---
title: "how to open the login x window??"
date: 2009-11-02
forum: General Help
---

### Post by mo24290 on 2009-11-02
I installed ubuntu 9.10 on the same partition with windows xp ,and after I reboot my desktop , I entered the shell and I can't log in the x window .
I pressed Alt-F7 but the screen became black with a small ( - ) in the top of it and it keep blanking.
what is the problem and how can I solve it ??
Thanks...

---

### Post by Giblet5 on 2009-11-02
You can't install Linux on the same partition with Windows XP.

You can install Linux on top of XP (wiping XP out), or you can install Linux on the same disk, but a different partition, as Windows XP.

Which one did you do?

When you flip to the text console via CtrlAltF1, do you get a login: prompt? Can you log in?

If so, run ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

If it still doesn't work, X is having trouble determining the correct timing for your monitor. You'll have to get the hsync and vsync frequencies for your monitor and create a new /etc/X11/xorg.conf file that uses those timings.

The hsync is specified in Khz and vsync is specified in Hz. In xorg.conf, they're specified as a floating point value eg, "vendor says Hsync is 24Khz - 90.3Khz", so you'll use "24.0 - 90.3" (w/o quotes) in xorg.conf.

Here's an example basic xorg.conf for an HP F2304 23" LCD:
```
Section "Monitor"
    Identifier     "HP f2304"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Videocard0"
    Monitor        "HP f2304"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"
    Option         "UseEdid" "False"
    Option         "AllowDDCCI" "False"
EndSection
```

---

### Post by danastasio on 2009-11-02
Hi,
I can't help with your X problem, as i would probably end up totally borking your system :P, but i just wanted to point out that you cannot have linux installed in the same partition as windows XP. Unless you mean that you used WUBI to install ubuntu? I really would like to help, but i cant tell you how many times i had to re-install my system because i was fiddling around with X.

---

### Post by unamanic on 2009-11-02
First question, is this a WUBI install?

Second question, if it isn't WUBI, did you have X on the live CD that you installed from?  

What errors do you see if you login using the text login and enter the command "startx"? 

Do you have an NVidia graphics card? (I've heard there is some times trouble with NVidia and 9.10)

---

### Post by mo24290 on 2009-11-02
I installed ubuntu on the same disk (not the same partition sorry) and there is no errors in the shell I can log in via shell.

---

### Post by mo24290 on 2009-11-02
First of all thank you guys for trying to help me:)....
I wrote recgonfigure code in the shell but there was an error it says "rather than invoking init.d use the restart (8) utility"

---

### Post by unamanic on 2009-11-02
They're trying to get you more used to the Red Hat way:
```

sudo service [service name] [start|stop|restart]

```

plus it looks like they've added their own:
```

sudo restart [service]

```

Although I get the heebie Jeebies typing restart on the command line (a little too close to reboot)



So you get a GUI if you login and enter:
```

startx

```

If this is the case you could try a:
```

sudo dpkg-reconfigure gdm

```

---

### Post by mo24290 on 2009-11-02
Thank you so much ,finally I can see the Xwindow thank god ..:P

---

