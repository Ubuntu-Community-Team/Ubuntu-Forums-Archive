---
title: "How to Use /etc/rc.local?"
date: 2012-01-16
forum: General Help
---

### Post by tokyo-joe on 2012-01-16
I want to configure my display gamma at every boot, so I added the following line in /etc/rc.local.

    xgamma -gamma 0.6

However, it doesn't work. When I manually execule the above command from CLI after boot, it works.

How can I make it to perform xgamma command everytime the system boot up?

---

### Post by Lars Noodén on 2012-01-16
Will it work if you put the full path to xgamma?

```

/usr/bin/xgamma -gamma 0.6

```

And to belabor the obvious, that line is before 'exit'.

---

### Post by amauk on 2012-01-16
You'll need to add this to your bashrc file
When rc.local executes, the graphics subsystem isn't yet loaded

```
gedit ~/.bashrc
```
Add at the end
```
xgamma -gamma 0.6
```

---

### Post by tokyo-joe on 2012-01-16
> **amauk said:**
> You'll need to add this to your bashrc file
When rc.local executes, the graphics subsystem isn't yet loaded

```
gedit ~/.bashrc
```
Add at the end
```
xgamma -gamma 0.6
```

This method did not work at boot. However, when I start a gnome terminal, it executes "xgamma -gamma 0.6".

hmmm.....

---

### Post by tokyo-joe on 2012-01-16
> **Lars Noodén said:**
> Will it work if you put the full path to xgamma?

```

/usr/bin/xgamma -gamma 0.6

```

And to belabor the obvious, that line is before 'exit'.

I tried this as you exactly suggest, but it did not work...

---

### Post by Lars Noodén on 2012-01-16
I'm unclear as to what xgamma does but if you nee it to be present in your graphical environment then it should go in [font=Courier New].xsessionrc[/font] in your home directory.  The file is not there by default, you have to add it yourself.

---

### Post by Xgen on 2012-01-16
I would try 'xgamma -gamma .600' (without quotes) in your Startup Applications.

---

### Post by tokyo-joe on 2012-01-16
> **Lars Noodén said:**
> I'm unclear as to what xgamma does but if you nee it to be present in your graphical environment then it should go in .xsession in your home directory.  The file is not there by default, you have to add it yourself.

It did not work either.
The file was not there, so I created the file and edited. But it did not work...

Xgamma is a command that adjusts colour setting of your system, by the way. The usage is;
  xgamma -gamma [place a preferred gamma value. The default value is 1.0]

---

### Post by tokyo-joe on 2012-01-16
> **Xgen said:**
> I would try 'xgamma -gamma .600' (without quotes) in your Startup Applications.

I tried this, but it did not work either.
hmm...

---

### Post by Xgen on 2012-01-16
> I tried this, but it did not work either.

Works for me, as this is similar to the gamma setting I use, as it would drop out on reboot with my ATI/AMD 6970 card. Perhaps mention what graphics card you are using.

---

### Post by tokyo-joe on 2012-01-16
> **Xgen said:**
> Works for me, as this is similar to the gamma setting I use, as it would drop out on reboot with my ATI/AMD 6970 card. Perhaps mention what graphics card you are using.

My machine is Lenovo ThinkPad X61. The graphic chip is Intel X3100, based on the information on this page.
[http://support.lenovo.com/en_AE/detail.page?LegacyDocID=MIGR-67777]("http://support.lenovo.com/en_AE/detail.page?LegacyDocID=MIGR-67777")

---

### Post by tokyo-joe on 2012-01-16
I also have to mention that adding xgamma command to >System>Auto Start does work for Kubuntu 11.04 installed in another partition on the same machine.

I am not sure what makes this difference, though...

---

### Post by Xgen on 2012-01-16
Okay, grasping at straws here....what about adding Gamma <value> to xorg.conf? Perhaps under Section "Monitor" as suggested here:

[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html]("http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html")

---

### Post by tokyo-joe on 2012-01-16
> **Xgen said:**
> Okay, grasping at straws here....what about adding Gamma <value> to xorg.conf? Perhaps under Section "Monitor" as suggested here:

[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html]("http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html")

/etc/X11/xorg.conf nor /etc/xorg.conf can't be found in my system. My system is Ubuntu 11.10. Where is this file??

---

### Post by Xgen on 2012-01-16
[https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

---

### Post by tokyo-joe on 2012-01-17
> **Xgen said:**
> [https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config")

This didn't crate a xorg.conf file.
Which means I have to create the xorg.conf file?
Where can I find the appropriate parameters (other than gamma) to put into the newly created xorg.conf file??

---

### Post by AMDphreak on 2012-09-20
> **Xgen said:**
> Okay, grasping at straws here....what about adding Gamma <value> to xorg.conf? Perhaps under Section "Monitor" as suggested here:

[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html]("http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html")

Whoah! I used your suggestion, and I added a "Monitor" section to my /etc/X11/x.org.conf , and it bricked my X server entirely, after I rebooted. I couldn't even use the fail-safe X session recovery mode. I had to go into Ubuntu's root terminal recovery mode and comment out the section I added in order to get back into Ubuntu. I'm using Ubuntu 12.04 LTS.

I have a major question for the X server designers. I mean, if their own specifications caused my X session to crap out, then what other solution could exist for this?

---

### Post by AMDphreak on 2012-09-20
> **Xgen said:**
> I would try 'xgamma -gamma .600' (without quotes) in your Startup Applications.

I tried this, too. My results were not exactly a failure.

The xgamma command ran instantly when I logged in, but it was killed a split second later. I don't know why this happened, so I can't triage it.

---

### Post by AMDphreak on 2012-09-20
I found a solution that works for me in GNOME 3.0 Unity on Ubuntu 12.04 LTS.

The solution is, unfortunately, not system-wide, so it will not automatically apply to any other users of the computer, and it will not apply before you log in. There are some more limitations included at the end of this post*.

You should use a program called LPROF to create a new ICC profile. You can use the program to adjust the output levels of the primary channels, Red, Green, and Blue, and then you export the setting as an ICC profile (profile.icc file). Make sure you save it somewhere that you can remember. I saved it in my home directory /home/{myusername}

Then you go to the GNOME System Settings, and you click on "Color". Inside this feature, you should click on your monitor, if and when it shows up in the list of configurable devices. After you click on the device name, click on the "Add Profile" button. In the drop-down list, you choose "Other Profile..." and this will give you a file selection window (file selection dialog). Then, you navigate to the file and select it, then click Import. Then you must reboot.

* The other limitation that I found is that none of these solutions will persist in your X session, if you decide to open up a new TTY (TeleTYpewriter) prompt. So, if you hit Ctrl + Alt + F8 and then decide to go back to your GNOME session by hitting Ctrl + Alt + F7, then all your X color settings will disappear, no matter which method you used to get there.

I am extremely disappointed in the color correction implementation on Linux. This is really sub-par. Maybe X server needs to be redone from scratch so that it respects changes to its settings for different control levels (session-wide, system-wide, driver-wide).

---

