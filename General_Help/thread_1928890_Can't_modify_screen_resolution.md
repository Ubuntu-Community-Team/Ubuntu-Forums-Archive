---
title: "Can't modify screen resolution"
date: 2012-02-20
forum: General Help
---

### Post by BryanR87 on 2012-02-20
Hello Ubuntu world,

                           I am tiring to change my resolution to 1202x670. I have tried everything I found on the net from XrandR to ArandR even installed a package called Resolution Switcher, but to no avail. Now the reason I need such a bazaar resolution size is because I am running an old Samsung T.V. with HDMI connection and it doesn't play with with PC displays (the HDMI that is, it works fine with VGA). I have this same resolution size for my Windows 7 installation, but I used nVidia's control panel to get it (there's an option in there that you can manually resize your resolution). I tried to do this with nVidia X Server Setting but to no avail. Now I read up on this xconfig file like I have many of times before with other Linux Distro's I have used, but I don't understand it one bit (scumbagbrain.jpeg). Now I don't know what exactly you need to know for my hardware, for this issues so here is a start. If you need to know anything else or I forgot to mention something please let me know.

Ubuntu 11.10 64 bit

nVidia GeForce 210

Yes I am using the nVidia driver that the Additional Hardware package provides.

Now with Debian (don't know if this applies for Ubuntu) you have to have a certain Linux image installed. I am using the generic 3.0 something something Linux image. 

Thank you for your time,
Bryan

---

### Post by Paddy Landau on 2012-02-21
I'm no expert on resolution, but may I ask how you tried to change your resolution before fiddling with XRandR and others?

The standard way to change resolution in Ubuntu is through the Monitors application.

---

### Post by BryanR87 on 2012-02-21
> **Paddy Landau said:**
> I'm no expert on resolution, but may I ask how you tried to change your resolution before fiddling with XRandR and others?

The standard way to change resolution in Ubuntu is through the Monitors application.


With XrandR you would type ```
xrandr
``` in the terminal to find out all of your resolution size's, now I have more then the Ubuntu Monitors Application tell me. Second you type in cvt (your desired resolution size) so it would be```
 cvt 1202 670
``` (yes you leave out the x) then you get some lines of command I guess you could call it. Then you type in the terminal ```
xrandr --newmode
``` the previous line of command you got. Then you type in two more line's of commands to finalize the new resolution size BUT it only for that session, once you restart you lose it. So in order to save it for future sessions you have to take the last three lines of commands you type in the terminal. Here is the instruction I got from one of Ubuntu's site's. [HTML]http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html
[/HTML]Now my issue is I get an error during this process. When I go to type in ```
xrandr --newmode "1208x670_60.00"   65.00  1208 1264 1384 1560  670 673 683 696 -hsync +vsync
``` this is the error I get ----> Failed to get size of gamma for output default

Now I found people with the same issue as me and their solution helped them but it didn't help me.(Always my luck)

---

### Post by Paddy Landau on 2012-02-22
Yes, I have used XRandR before (a long time ago before Ubuntu was as polished as it is now).

My question was whether or not you first tried the built-in utility, the application *Monitors*. If you have not tried that, it really is your first port of call. If you have tried it, what was your error?

I think it's best, if you have a problem, to start with the basics, i.e. the functionality that you are supposed to use. Only if we can't get that to work should we start looking at other functions, don't you think?

---

### Post by roelforg on 2012-02-22
Post the output of:
```

sudo cat /proc/cmdline

```

---

### Post by BryanR87 on 2012-03-02
@ Paddy Landau: Yes I tried the built-in utility. It only gives me three resolution sizes (none of which work), so in my opnion it's trash compared to nVidia X server settings and XRandR which give me 10 + sizes

@ roelforg: this is my out put from the code you provided: 

BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=53f01417-aa28-4c1c-9715-c16fa4047e7a ro quiet splash vt.handoff=7

Thank you both for your time,

Bryan

---

### Post by BryanR87 on 2012-03-08
Bump

---

### Post by pootan on 2012-03-08
Since xrandr provided you a modeline you can try making a default xorg.conf file using nvidia-settings(nVidia X server settings) using any resolution available. Once you have done this you can edit your xorg.conf file manually and substitute in the modeline xrandr gave you in the appropriate section. 

See this recent topic. 

[URL="http://ubuntuforums.org/showthread.php?t=1937769"]http://ubuntuforums.org/showthread.php?t=1937769
[/URL]
Be aware that manually editing the xorg.conf file can leave you stranded at a text based login if your refresh rates and resolution aren't supported by your monitor so if you are unsure post here first and someone should be able to help.

---

