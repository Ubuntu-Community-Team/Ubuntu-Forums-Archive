---
title: "Help with 19&quot; flatscreen!!"
date: 2009-11-01
forum: General Help
---

### Post by dixie460 on 2009-11-01
Howdy all, new Linux user here, converting from Windows!! Just got Ubuntu 9.1 installed on a HP desktop I had layin around. I will be installing Ubuntu all over again on a larger hard drive (this one is only 3 gigs!!) after I get a few issues worked out. First of all, I have a ViewSonic VA1912wb widescreen monitor that I would like to use with my new Ubuntu 9.1 Karmic Koala installation. Problem is that whenever I reboot or startup for the first time, everything goes fine until the Ubuntu splash screen loads (the dark orange/brown screen with the scrolling left-to-right bar)...when the system gets to that point the monitor flashes to a black screen and then the splash screen comes up for a little bit and then flashes back to black and this just continues in a loop over and over with the startup sound playing each time right before it flashes back to a black screen. 

I HAVE noticed that if I hit Ctrl-Alt-F1 when the screen first appears, and then hit Ctrl-Alt-F7 after that, it will go right to the login screen and the monitor will work fine from then on out until the next reboot. OR, if I use an old HP 16" CRT monitor, Ubuntu doesn't think twice about loading up perfectly.

I can't find my xorg.conf file anywhere to edit my display settings...anyone know where it is in 9.1?? 

Thanks!!!

---

### Post by Giblet5 on 2009-11-01
Xorg no longer *requires* an xorg.conf, but it will use /etc/X11/xorg.conf if it's there.

You probably need to create one that *exactly* matches the timing of your monitor.

You'll need the hsync and vsync frequencies in Khz.

Here's an *EXAMPLE* for an HP f2304: ```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "HP f2304"
    ModelName      "CRT-0"
    HorizSync       30.0 - 94.0
    VertRefresh     48.0 - 95.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Monitor        "Monitor0"
EndSection

```

The monitor vendor will have those values somewhere...

Once you have it saved out, you can restart X via: ```
sudo /etc/init.d/gdm restart
``` and it will use the new timings.

NOTE: Make SURE you use the correct timings; older monitors can be destroyed by running them outside of there specified frequency range.

---

### Post by dixie460 on 2009-11-01
I don't have an xorg.conf in my /x11 directory...should I create one? And if so, should I use your example to make mine, and just replace the values with the correct ones for my monitor? Thank you for the quick reply!

---

### Post by Giblet5 on 2009-11-01
> **dixie460 said:**
> I don't have an xorg.conf in my /x11 directory...should I create one? And if so, should I use your example to make mine, and just replace the values with the correct ones for my monitor? Thank you for the quick reply!

Yes.

Yes.

You are welcome. Once you've confirmed that this is corrected, mark the thread SOLVED using the Thread Tools dropdown, please.

---

### Post by dixie460 on 2009-11-02
I'll try that when I get home from work, and if it works I'll be sure to mark the thread as SOLVED.
 
Regards, 
Andy

---

### Post by dixie460 on 2009-11-02
well I tried it and it didn't work. When I right-clicked in the /x11 directory I didn't have the option to create a file (I presume only root can do this) so Right click desktop > Create document > Empty file. I entered the following in there (I couldn't find any direct information online for my screen, but I did find another user's information for the same screen.) 

Section "Monitor"
    Identifier     "VA1912wSERIE"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Monitor        "Monitor0"
EndSection

Saved it to my USB flash drive as xorg.conf  and then opened a terminal window. I typed sudo nautilus...it ran some warnings but did open the file browser successfully. I used it to copy the xorg.conf file to my /x11 directory, then used the following command.
sudo /etc/init.d/gdm restart When it restarted it was still stuck in a loop like I described before. A complete power cycle didn't help either. Any idea what I did wrong?

Thanks!

EDIT: I found this link which shows the same specs for my screen as I typed in xorg.conf...[http://www.viewsonic.com/products/va1912wb.htm](http://www.viewsonic.com/products/va1912wb.htm)

I must have missed it the first time I looked on their site

---

### Post by P4man on 2009-11-02
Try specifying a resolution:. Change the numbers to match your monitor native resolution and optimum refresh rate.

```

Section "Monitor"
    Identifier     "VA1912wSERIE"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Monitor        "Monitor0"
[COLOR="Red"]   SubSection "Display"
        Depth        24
        Modes      "1024x768_75.00"
    EndSubSection[/COLOR]

EndSection
```

---

### Post by dixie460 on 2009-11-02
I modded the file exactly as you specified with the values you wrote, and restarted...still no good. Were those the correct values for my screen or was that just an example? On the viewsonic website it says: True Resolution   	                1440x900

Thanks!

Andy

---

### Post by P4man on 2009-11-02
> **dixie460 said:**
> I modded the file exactly as you specified with the values you wrote, and restarted...still no good. Were those the correct values for my screen or was that just an example? On the viewsonic website it says: True Resolution   	                1440x900

Thanks!

Andy

I thought I was rather clear that you had the change them?
Still, even the numbers I used should work on just about any monitor (just look ugly and stretched) so im wondering if its not a different problem.

---

### Post by dixie460 on 2009-11-02
DOH!! Sorry I just read your post real quick and didn't "get it" that you intended me to change them. I just put in the values from ViewSonic's spec sheet and it still doesn't work. Let me try changin from 75Hz to 60Hz...

Regards,
Andy

EDIT: changing to 60 Hz didn't work either...going back to 75Hz and still stumped...

Regards,
Andy

---

### Post by P4man on 2009-11-02
There is also the odd chance you have a 16 bit monitor. You could try changing depth 24 to depth 16 if nothing else helps?

---

### Post by Giblet5 on 2009-11-02
> **dixie460 said:**
> well I tried it and it didn't work. When I right-clicked in the /x11 directory I didn't have the option to create a file (I presume only root can do this) so Right click desktop > Create document > Empty file. I entered the following in there (I couldn't find any direct information online for my screen, but I did find another user's information for the same screen.) 

```
Section "Monitor"
    Identifier     "VA1912wSERIE"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Monitor        [COLOR="DarkRed"]"VA1912wSERIE"
[/COLOR]EndSection
```

Saved it to my USB flash drive as xorg.conf  and then opened a terminal window. I typed sudo nautilus...it ran some warnings but did open the file browser successfully. I used it to copy the xorg.conf file to my /x11 directory, then used the following command.
sudo /etc/init.d/gdm restart When it restarted it was still stuck in a loop like I described before. A complete power cycle didn't help either. Any idea what I did wrong?

Thanks!

EDIT: I found this link which shows the same specs for my screen as I typed in xorg.conf...[http://www.viewsonic.com/products/va1912wb.htm](http://www.viewsonic.com/products/va1912wb.htm)

I must have missed it the first time I looked on their site

Try that.

The "Identifier" value is what you use to reference that in other sections.

---

### Post by P4man on 2009-11-02
> **Giblet5 said:**
> Try that.

The "Identifier" value is what you use to reference that in other sections.

Doh. Missed that. Good catch.

---

### Post by Giblet5 on 2009-11-02
> **P4man said:**
> Doh. Missed that. Good catch.

Mmm. Bitter dregs. ;)

---

### Post by dixie460 on 2009-11-02
Changing to 16 bit depth didn't work, neither did changing the value for Monitor under Section "Screen".

Am I doomed to using my crappy CRT??

Regards, Andy

---

### Post by Giblet5 on 2009-11-02
> **dixie460 said:**
> Changing to 16 bit depth didn't work, neither did changing the value for Monitor under Section "Screen".

Am I doomed to using my crappy CRT??

Regards, Andy

Did you restart X after changing the identifier?

```
sudo /etc/init.d/gdm restart
```

If you did, please post your xorg.conf instead.


PS: I know this can be frustrating when you're not sure what all of these commands are doing or how they do it. If you're wondering about some of them, just ask. I'll be happy to explain.

We can get this monitor working as well as it can possibly work, but it's a very manual process. It used to be a LOT harder if that's any comfort. I learned back when you had to modify the X code and recompile, so I find this stuff just easy as anything...but I remember breaking things and yelling too.

---

### Post by dixie460 on 2009-11-02
Well I broke it now... I took it upon myself to try some other things...namely the instructions on this page:

[http://ubuntuforums.org/showthread.php?t=120942](http://ubuntuforums.org/showthread.php?t=120942)


Section "Monitor"
    Identifier    "VA1912wSERIE"
    HorizSync    30-82
    VertRefresh    50-85
    Option        "DPMS"
    Modeline     "1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946
EndSection


SubSection "Display"
        Depth        24
        Modes        "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection


I only did what listed above, changing my xorg.config file to look like that.

Now when I boot, it gives me the terminal login instead of the GUI...

Any idea how to change the settings back so at least I have some GUI functionality?

And yes, it is frustrating because I just switched to Linux and don't know a whole lot. If you would like to take the time to help me understand what's going on here, I 'd really appreciate it, along with the help that everyone else has offered up. I will say that it's a sure bet I'll be on here helping others as soon as I've got enough experience to do so.

Thanks again!!

---

### Post by Giblet5 on 2009-11-02
Log in in text mode. Execute the following:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.notquite
sudo /etc/init.d/gdm restart
```

That will put you back in the GUI, but still not right.

Log in. Bring up a terminal window. Enter ```
sudo gedit /etc/X11/xorg.conf
```

Select, copy, and paste this into gedit, then save it and exit gedit: ```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen          0 "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Generic Mouse"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier   "Generic Mouse"
    Driver       "mouse"
    Option       "CorePointer"
    Option       "Device" "/dev/input/mice"
    Option       "Protocol" "ExplorerPS/2"
    Option       "ZAxisMapping" "4 5"
EndSection
    
Section "Monitor"
    Identifier    "VA1912w"
    HorizSync     30.0 - 82.0
    VertRefresh   50.0 - 85.0
    Option        "DPMS"
EndSection

Subsection "Device"
    Identifier    "gpu"
EndSection

Section "Screen"
    Identifier   "Screen0"
    Monitor      "VA1912w"
    Device       "gpu"
    DefaultDepth 24
EndSection
```

Then restart the X server via ```
sudo /etc/init.d/gdm restart
```

---

### Post by dixie460 on 2009-11-02
Thanks for gettin me back into the GUI. Unfortunately, it still goes in a Login screen/black screen loop when I boot/reboot. I see the xorg.conf file is gone, and replaced by a xorg.conf.notquite file. Let me try using gedit to recreate the xorg.conf file again, I'll be right back with the results.

Regards
Andy

---

### Post by Giblet5 on 2009-11-02
> **dixie460 said:**
> Thanks for gettin me back into the GUI. Unfortunately, it still goes in a Login screen/black screen loop when I boot/reboot. I see the xorg.conf file is gone, and replaced by a xorg.conf.notquite file. Let me try using gedit to recreate the xorg.conf file again, I'll be right back with the results.

Regards
Andy

Waitin...


Gotta go for now. Back in 90 minutes.

---

### Post by dixie460 on 2009-11-02
No good, I verified that I cut and pasted everything properly, and restarted via the command you gave me, and it dumped me to a black screen. I plugged in my CRT and it showed up all black there also. Went back to my flatscreen, rebooted, and it gave me the terminal login again. Ran the commands again and got back into the GUI, and here I am now.

I've got to be up at 5am (my time, on the west coast of Florida) so if I don't reply again tonight I will check about 10:00 tomorrow morning from work. I really appreciate all the help so far!!

Regards,
Andy

---

### Post by Giblet5 on 2009-11-02
Are you absolutely sure that the monitor is a Viewsonic VA1912w? The timings you found are correct.

Let's try another xorg.conf, but with a complete set of color depths and forcing the refresh rate to a sane value. Viewsonic states that this monitor provides the best quality at 1440x900 with a 60Hz refresh rate, so let's use that.

Same drill as before. ```
sudo gedit /etc/X11/xorg.conf
```

Copy/paste the following into gedit, then save, and exit.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Generic Mouse"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Generic Mouse"
    Driver         "mouse"
EndSection
    
Section "Monitor"
    Identifier     "VA1912w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
EndSection

Subsection "Device"
    Identifier     "gpu"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Monitor        "VA1912w"
    Device         "gpu"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"
    Option         "UseEdid" "False"
    Option         "AllowDDCCI" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900@60"
    EndSubSection
EndSection
```

Then restart the X server via ```
sudo /etc/init.d/gdm restart
```

If you get a black screen, try hitting Ctrl + Alt + PLUS (the plus key on the numeric pad) and see if it syncs up. That will cause the display adapter to cycle through the different color depths defined in the config file.

If it still won't sync, then flip to the text console via CtrlAltF1, log in, and execute these commands: ```
cp /var/log/Xorg.0.log xorg.log
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.full
sudo /etc/init.d/gdm restart
```

Now that you have your GUI back, post the contents of xorg.log, which is now in your home directory.

---

### Post by dixie460 on 2009-11-03
Ok, thanks. I'll be home in 8 hours, so when I get there I'll try that out and post back. According to the decal on the front, my monitor is a VA1912wb, not just a 1912w.
 
Regards,
Andy

---

### Post by dixie460 on 2009-11-03
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Janet 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=2a28f695-b1b6-46cc-9861-80f98c2303aa ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  3 15:15:37 2009
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 24 of section Monitor in file /etc/X11/xorg.conf
    "Subsection" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log



That's the logfile above. It ain't liking "Subsection" I see...should I change it to "SubSection"? Anyhow, here's what I did...I changed xorg.conf, then restarted the X server with the command you gave me. It dumped me to a black screen and stopped responding...keyboard, mouse, and all so needless to say Ctrl-Alt-PLUS didn't work. Had to power cycle to get it to respond again. It's still doing the same thing as it originally did, stuck in a loop. I noticed you said that if it still won't sync to hit Ctrl-Alt-F1 to go the the console...I have NEVER seen a console when I've hit Ctrl-Alt-F1, it always just turns black. That is currently my only way to get the GUI up is to wait til my screen turns black, hit Ctrl-Alt-F1 at the right moment, and then either Ctrl-Alt-F7 or Ctrl-Alt-F9. The screen is black the whole time I'm giving it F-key commands. I only knew to try that because I read somewhere online that it could help out in some way? But I take from what you said that it's actually supposed to be a terminal...??

By the way, where it says Janet in the logfile, that is just what I named this particular computer if it matters any.
Regards
Andy

---

### Post by Giblet5 on 2009-11-03
Let's try another xorg.conf, but **[COLOR="DarkRed"]without[/COLOR]** the typo this time (sorry).

Same drill as before. ```
sudo gedit /etc/X11/xorg.conf
```

Copy/paste the following into gedit, then save, and exit.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Generic Mouse"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Generic Mouse"
    Driver         "mouse"
EndSection
    
Section "Monitor"
    Identifier     "VA1912w"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
EndSection

Section "Device"
    Identifier     "gpu"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Monitor        "VA1912w"
    Device         "gpu"
    DefaultDepth    24
    Option         "UseEdidFreqs" "False"
    Option         "UseEdid" "False"
    Option         "AllowDDCCI" "False"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900@60"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900@60"
    EndSubSection
EndSection
```

Then restart the X server via ```
sudo /etc/init.d/gdm restart
```

If you get a black screen, try hitting Ctrl + Alt + PLUS (the plus key on the numeric pad) and see if it syncs up. That will cause the display adapter to cycle through the different color depths defined in the config file.

If it still won't sync, then flip to the text console via CtrlAltF1, log in, and execute these commands: ```
cp /var/log/Xorg.0.log xorg.log
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.full
sudo /etc/init.d/gdm restart
```

Now that you have your GUI back, post the contents of xorg.log, which is now in your home directory.

---

### Post by dixie460 on 2009-11-03
Well how bout that! Just for fun, I removed the system drive (the one with Ubuntu on it) from the HP box it was in and put it in a Gateway that was just given to me. The Gateway has an ATI graphics card...connected it to my flatscreen and it works!! I'm going to use the screen with this Gateway now, but Ubuntu is running on a 3Gb HDD. What I'm gonna do is go buy maybe a 160Gb+ drive, put Karmic on it, and run it in the Gateway. The 3Gb drive will go in the HP case, and I'll pair it with the old CRT I have and maybe set it up in my son's room so he can learn to use a computer.

I really appreciate all the help from everyone, especially Giblet5. A big thank you to everyone. ;) I would still like to know what my logfile is telling me, if you could please have a look at my last post.

Now, my next project will be to set up Karmic 64 bit to dual boot with Windows 7 64 bit on my new Inspiron 1545 which should be arriving soon. I might even get rid on windows altogether...it depends on what I have that might only run in windows, but after jumping right in and seeing Ubuntu, and how easy it is to change system files and whatnot (as opposed to hacking windows just to change something that's not supposed to be changed), I know that win 7 won't be used a whole lot anyway.

Thanks again!

Andy

---

### Post by Giblet5 on 2009-11-03
> **dixie460 said:**
> Well how bout that! Just for fun, I removed the system drive (the one with Ubuntu on it) from the HP box it was in and put it in a Gateway that was just given to me. The Gateway has an ATI graphics card...connected it to my flatscreen and it works!! I'm going to use the screen with this Gateway now, but Ubuntu is running on a 3Gb HDD. What I'm gonna do is go buy maybe a 160Gb+ drive, put Karmic on it, and run it in the Gateway. The 3Gb drive will go in the HP case, and I'll pair it with the old CRT I have and maybe set it up in my son's room so he can learn to use a computer.

I really appreciate all the help from everyone, especially Giblet5. A big thank you to everyone. ;) I would still like to know what my logfile is telling me, if you could please have a look at my last post.

Now, my next project will be to set up Karmic 64 bit to dual boot with Windows 7 64 bit on my new Inspiron 1545 which should be arriving soon. I might even get rid on windows altogether...it depends on what I have that might only run in windows, but after jumping right in and seeing Ubuntu, and how easy it is to change system files and whatnot (as opposed to hacking windows just to change something that's not supposed to be changed), I know that win 7 won't be used a whole lot anyway.

Thanks again!

Andy


Even better! Congrats!

Here's the pertinent part of the Xorg.0.log file with my typo pointed out:
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Janet 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=2a28f695-b1b6-46cc-9861-80f98c2303aa ro quiet splash
Build Date: 26 October 2009 05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 3 15:15:37 2009
[COLOR="DarkRed"](==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 24 of section Monitor in file /etc/X11/xorg.conf
"Subsection" is not a valid keyword in this section.[/COLOR]
```

If you compare the latest xorg.conf with the previous one (that generated this error), you'll see that at line 24, I put "SubSection" where "Section" was the correct syntax.

The way *I* would have fixed it is to execute (from the text console) ```
vi +24 /etc/X11/xorg.conf
```

I would have changed it to "Section", saved it out, and restarted via the /etc/init.d/gdm restart.

Interesting hint: gedit understands +NN line number syntax on the command line. It saves counting. ;)

Have fun.

---

