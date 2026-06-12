---
title: "nVidia Problems"
date: 2009-11-14
forum: General Help
---

### Post by Bubka3 on 2009-11-14
Hi,
 
I recently installed unbuntu. Ok so download drivers from nvidia for my card and now the look is 640x480 and its the only one I can choose. I want 1440x900. I have 1400x900 on windows and it works fine.
 
**Please Help**
 
Thanks,
Bubka3

---

### Post by upapilot on 2009-11-15
Your sound card is probably not be OpenGL compatible....Or the driver must have not installed properly....try reinstalling your graphics driver.

---

### Post by Bubka3 on 2009-11-15
What does sound card have to do with Graphics, btw I have an nVidia 9400 GT.

---

### Post by upapilot on 2009-11-15
did you try reinstalling the driver?
your driver must have some sort of problem with Ubuntu or perhaps corrupt.
i had problems with one of my driver too but i fixed it by reinstalling the driver

---

### Post by Bubka3 on 2009-11-15
How would I do this?

---

### Post by Darce on 2009-11-15
Go to the System/Administration/Hardware Drivers and make sure the Nvidia accelerated graphics driver is activated. It should have a green dot next to it if is. Else select it and hit activate. If there is more than one, one will be marked [recommended]. Use that one.

Cheers,

Tim

---

### Post by Bubka3 on 2009-11-15
Yea, the recommended one is activated.

---

### Post by upapilot on 2009-11-15
see if this helps[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by Bubka3 on 2009-11-15
That doesnt have Ubuntu 9.10 which is what im using.

---

### Post by upapilot on 2009-11-15
the 8.10 should work

---

### Post by upapilot on 2009-11-15
is your problem somewhat similar to this:
Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

    *

      Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
    *

      Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
    *

      Find the line that says Section "Screen"
    *

      Insert a new line that says Option "UseDisplayDevice" "DFP".
    *

      Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.

---

### Post by Darce on 2009-11-15
Take a look here :

[http://ubuntuforums.org/showthread.php?t=1326504&highlight=nvidia+640x480](http://ubuntuforums.org/showthread.php?t=1326504&highlight=nvidia+640x480)

Involves editing your xorg.conf file and adding your resolutions. As suggested in the thread, remember to backup the file before making any changes.

---

### Post by Giblet5 on 2009-11-15
You just need to tweak the "Monitor" section of your /etc/X11/xorg.conf file.

It's easy as falling off a log.

What's the max refresh rate at 1440x900?

Run cvt against it, snag the hsync and vertical frequency and drop it in.

This will work, but it might flicker:

```
$ cvt 1440 900 60
# 1440x900 59.89 Hz (CVT 1.30MA) **[COLOR="DarkRed"]hsync: 55.93[/COLOR]** kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

Ah ha! 55.93Khz for Hsync.

So edit your xorg.conf via ```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to the Section marked "Monitor". Add two lines above the EndSection statement: ```
    HorizSync   55.93
    VertRefresh 60.00
```

Save it and exit gedit.

Now, restart Xorg via ```
sudo /etc/init.d/gdm restart
```

That'll log you off. The login will appear at 1440x900.

Ta da!


Edit: the section, when done will look like:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       55.93
    VertRefresh     60.00
EndSection
```

If your monitor can do 75Hz refresh, just run the numbers through cvt and plug the new hsync and vert frequencies in.

---

### Post by Bubka3 on 2009-11-15
> **Giblet5 said:**
> You just need to tweak the "Monitor" section of your /etc/X11/xorg.conf file.
 
It's easy as falling off a log.
 
What's the max refresh rate at 1440x900?
 
Run cvt against it, snag the hsync and vertical frequency and drop it in.
 
This will work, but it might flicker:
 
```
$ cvt 1440 900 60
# 1440x900 59.89 Hz (CVT 1.30MA) **[COLOR=darkred]hsync: 55.93[/COLOR]** kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```
 
Ah ha! 55.93Khz for Hsync.
 
So edit your xorg.conf via ```
sudo gedit /etc/X11/xorg.conf
```
 
Scroll down to the Section marked "Monitor". Add two lines above the EndSection statement: ```
    HorizSync   55.93
    VertRefresh 60.00
```
 
Save it and exit gedit.
 
Now, restart Xorg via ```
sudo /etc/init.d/gdm restart
```
 
That'll log you off. The login will appear at 1440x900.
 
Ta da!
 
I have no clue what you are all saying, your confusing me. I that link is also confusing. I am starting to giveup, anyone got any last minute ideas that are easy?

---

### Post by upapilot on 2009-11-15
Ok since your getting desperate:
just backup all your important files, and reintall ubuntu....if you don't know how to delete ubuntu refer to this thread: [http://ubuntuforums.org/showthread.php?t=1034167](http://ubuntuforums.org/showthread.php?t=1034167)
Post the results of how your graphics driver works after reinstallation

---

### Post by Bubka3 on 2009-11-15
I'll still have to install the drivers from nVidia and be back at here so it doesnt make sense to re-install. Ill just use windows , no problem. Thx for tryin to help me.

---

### Post by Giblet5 on 2009-11-15
Reinstalling will put him right back here.

He's here because his GPU can't figure out what kind of monitor he has. Reinstalling won't change that.

---

### Post by upapilot on 2009-11-15
> **Giblet5 said:**
> Reinstalling will put him right back here.

He's here because his GPU can't figure out what kind of monitor he has. Reinstalling won't change that.

hmm...yes your probably right....but none of the help we can provide him can solve his problem...

---

### Post by Giblet5 on 2009-11-15
> **Bubka3 said:**
> I'll still have to install the drivers from nVidia and be back at here so it doesnt make sense to re-install.


What about my post do you not understand?

Is it that you don't understand how to run commands?

---

### Post by Bubka3 on 2009-11-15
> **Giblet5 said:**
> You just need to tweak the "Monitor" section of your /etc/X11/xorg.conf file. **- Ok Got It**
 
It's easy as falling off a log. **- No Comments**
 
What's the max refresh rate at 1440x900? **On Windows 60**
 
Run cvt against it, snag the hsync and vertical frequency and drop it in. **- You lost me here.**
 
This will work, but it might flicker:
 
```
$ cvt 1440 900 60
# 1440x900 59.89 Hz (CVT 1.30MA) **[COLOR=darkred]hsync: 55.93[/COLOR]** kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```
 
Ah ha! 55.93Khz for Hsync. **- Whats Hsync**
 
So edit your xorg.conf via ```
sudo gedit /etc/X11/xorg.conf
``` **I cant I open it from File Browser and edit?**
 
Scroll down to the Section marked "Monitor". Add two lines above the EndSection statement: ```
    HorizSync   55.93
    VertRefresh 60.00
``` **- Got It**
 
Save it and exit gedit. **- Got It**
 
Now, restart Xorg via ```
sudo /etc/init.d/gdm restart
``` **-Got It**
 
That'll log you off. The login will appear at 1440x900. **- Ok**
 
Ta da!
 
 
Edit: the section, when done will look like:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       55.93
    VertRefresh     60.00
EndSection
```
 
If your monitor can do 75Hz refresh, just run the numbers through cvt and plug the new hsync and vert frequencies in.
 
If you can explain that more I can fix this

---

### Post by upapilot on 2009-11-15
> **Giblet5 said:**
> Reinstalling will put him right back here.

He's here because his GPU can't figure out what kind of monitor he has. Reinstalling won't change that.

those things in the white boxex are commands....you should run them in the Terminal which is the equivalent of Windows Command Prompt.
You can access terminal from Applications>Accessories>Terminal

---

### Post by Bubka3 on 2009-11-15
So I open up Terminal and type in
 
> cvt 1440 900 60

---

### Post by Giblet5 on 2009-11-15
Oh.

The problem you're having is because your cable is not passing the monitor ID info to your nvidia controller. It has no idea what it's hooked to.

Under Windows, you would get a CD that has the monitor information included as a .inf file, or Windows would know about the model via an update.

Linux doesn't know about your monitor so there are two values that we can supply to cover the resolution that you most want, 1440x900.


The reason you can't browse to, then edit, xorg.conf is because your user account isn't allowed to. Only the superuser can edit that file.

To do it, open a terminal window (Applications -> Accessories -> Terminal) and enter ```
sudo gedit /etc/X11/xorg.conf
```

That will bring up a gui editor window. Scroll down to the "Monitor" section and make it look like this:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       55.93
    VertRefresh     60.00
EndSection
```

Save it and exit the editor.

Now enter this in the terminal window and you'll be running at 1440x900: ```
sudo /etc/init.d/gdm restart
```

---

### Post by Giblet5 on 2009-11-15
> **Bubka3 said:**
> So I open up Terminal and type in

My last post above is all you need to do to get 1440x900.

I was explaining to you how I figured out what values to use for your monitor. You use the cvt command.

---

### Post by Bubka3 on 2009-11-15
Well this made the login screen 1440x900 but when I logged in back to 640x480 it goes. Sigh

---

### Post by Bubka3 on 2009-11-15
Never mind, then I went into Server X and made it 1440x900.

Thanks All For Helping Me, The Major Noob :D

---

### Post by upapilot on 2009-11-15
learn a lesson from this experience : "Never get frutrated and never give up!"

---

### Post by Giblet5 on 2009-11-15
Does it flicker?

Do you know what the make and model of your monitor is?

I wrote a [complete HOWTO]("http://ubuntuforums.org/showthread.php?p=8302145#post8302145") on getting the most out of your monitor when your video card can't figure it out. It explains why this happens and what to do about it.

---

### Post by Bubka3 on 2009-11-15
Ok, Now everytime a login , i gotta set it to 1400x900, any ideas?

---

### Post by Giblet5 on 2009-11-15
Open a terminal window and enter:

```
rm .nvidia-settings-rc
```

The nvidia settings tool does cool stuff, but it sometimes remembers things it shouldn't. That will help it forget.

If you just installed this system, it would also be wise to run these commands to force regeneration of your session configuration - not mandatory, but I would:

```
cd $HOME
rm -fr .gconf* .gnome* .config .nv*
sudo /etc/init.d/gdm restart
```

That will log you off. When you log in, everything will be the Ubuntu install default, but it should be at 1440x900.

---

### Post by Bubka3 on 2009-11-15
Did this, 
1. Didnt Work
2. Cleared All my Wine Doors Programs
3. Sigh Again

---

### Post by Giblet5 on 2009-11-15
I did qualify that with "If you just installed".

The commands only removed the desktop icons. The wine config and any installed wine progs are still intact.

Can you post your entire /etc/X11/xorg.conf file?

```
sudo gedit /etc/X11/xorg.conf
```

Select it all, hit Ctrl+C to copy, paste it into a CODE block in the comment editor.

---

### Post by chillicampari on 2009-11-15
Can you copy what's in your /etc/X11/xorg.conf file and paste it into the thread (using the "code" tag)?

edit- Giblet beat me to it :D

---

### Post by Bubka3 on 2009-11-15
1. This time it booted up properly.
2. Now my top bar is messed up , my name bubka3 is mis-located.
3. Heres the config.
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Tue Oct 20 21:00:15 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       55.93
    VertRefresh     60.00
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Giblet5 on 2009-11-15
The only thing I can think of that would cause this is if the gnome display-settings tool was used before the nvidia driver was installed.

The way to fix it would be to turn off the nvidia driver, restart Xorg, log in, select System -> Preferences -> Display and set the resolution to 1440x900, reset the nvidia config and restart the X server.

To do all of that, open xorg.conf via ```
sudo gedit /etc/X11/xorg.conf
```

In the "Device" section, change the all lower-case "nvidia" to "nv". Save it and exit the editor.

Run ```
sudo /etc/init.d/gdm restart
```

Log in. Click on System->Preferences->Display (it won't bring up the nvidia settings tool this time). Select 1440x900 and close the tool.

Log off. Log in.

It should be at 1440x900 at login.

Bring up a terminal window and enter:
```
sudo gedit /etc/X11/xorg.conf
```

Go the the "Device" section again.

Change the "nv" to "nvidia", save, and exit.

In the terminal, enter ```
sudo /etc/init.d/gdm restart
```

Now when you log in, it *should* be at 1440x900 with the nvidia driver enabled.

---

### Post by grandtoubab on 2009-11-15
restart your computer
choose the ligne with recovery mode
select boot with root
when root prompt type the following

```
X -configure
```
```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```
```
reboot
```


advice write this command on paper before, be careful it's capital  X and capital X11

---

### Post by Bubka3 on 2009-11-15
Nows it just randomly booting in 1440x900 or smaller like 7##x###.
 
Very picky.

---

