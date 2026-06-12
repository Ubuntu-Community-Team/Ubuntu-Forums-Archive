---
title: "Screen Resolution Problems"
date: 2009-07-21
forum: General Help
---

### Post by jayorinda on 2009-07-21
I have a Dell 2001FP and an Nvidia graphics card.  The Dell monitor has an optimal resolution of 1600x1200 at 60 Hz.  Unfortunately i I cannot get the resolution any higher than 1024x768.  I have tried everything from installing the nVidia driver, using the xrandr command line tool to add undetected resolutions to modifying the xorg.conf file.  Nothing seems to work.  Any help is appreciated.

---

### Post by Piccy on 2009-07-21
I had a very similar problem (not on my PC but a friends)

I had to manually select the monitor. I am not sure on where that is as I am not on my Ubuntu PC. But try to look for a device listing for monitors and manually selecting the correct monitor

---

### Post by gastly on 2009-07-21
Have you tried to install the package 'nvidia-settings' from synaptic and tried changing the resolution from there?

---

### Post by CatKiller on 2009-07-21
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh    cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to [this page]("http://support.dell.com/support/edocs/monitors/2001fp/EN/specs.htm"), the values you want are

```

         HorizSync       31-80
         VertRefresh     56-76

```

---

### Post by mister_p_1998 on 2009-07-21
Try this, it worked for me..

[http://ubuntuforums.org/showthread.php?p=7618980#post7618980](http://ubuntuforums.org/showthread.php?p=7618980#post7618980)

---

