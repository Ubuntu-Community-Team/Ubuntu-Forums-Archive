---
title: "problem with nvidia drivers"
date: 2006-06-19
forum: General Help
---

### Post by jnev on 2006-06-19
I just installed kubuntu (already have ubuntu on the hard drive, I could have installed kubuntu desktop but I felt like doing a seperate install) and I have a problem with it. I installed the nvidia drivers and everything was going just fine.. then I installed the new kernel from a dist-upgrade, and everything fell apart. first it rewrote my xorg.conf to one where I get 1024x768 res (my monitor is 1680x1050, when I installed kubuntu it recognized it from install).. and it's running the nv driver, rather than nvidia. when I changed back to nvidia and put  in my resolution, X wouldn't start. when I changed back to nv, it rewrote my xorg.conf and booted back into 1024x768. what's wrong with this? I run the new kernel just fine in ubuntu with my normal resolution and everything works. just to test I installed ubuntu-desktop via apt-get and it did the same thing, so it's not a problem with kde.

anyone know what's wrong and/or how to fix it?
thanks

---

### Post by pyromithrandir on 2006-06-20
Well, after installing the new kernel, you can't use the 'nvidia' driver until you install it again. So, if you just reinstall the nvidia drivers you can use 'nvidia' instead of 'nv' again.

As for the xorg going to 1024x768 when you use 'nv' the only thing I can think of, if you do indeed have your xorg.conf configured to use the higher resolution, is that your nvidia graphics card needs the newest nvidia drivers to give you the performance you need for the higher res.

---

### Post by jnev on 2006-06-20
sorry, I forgot to mention that I did reinstall the nviida drivers after the kernel upgrade.

---

### Post by [S|G] on 2006-06-20
Try this at the terminal:
```

sudo apt-get remove nvidia*
sudo apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules-`uname-r` linux-restricted-modules-common

```

---

### Post by jnev on 2006-06-22
that worked perfectly, thanks!!!

EDIT
ok scratch that.. I just rebooted and it rewrote my xorg.conf again. luckily I made sure to back it up before I rebooted. what could possibly be making it rewrite it??

---

### Post by bforbes on 2006-06-22
Post your entire xorg.conf, maybe that will reveal something.

---

### Post by tseliot on 2006-06-22
Read this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED")

---

### Post by Maikun on 2006-06-22
Hi all. I have a similar problem even after following the instructions at the link posted by tseliot.

I have a TFT Monitor with 1280x1024. All is well with the nv driver. If I do nvidia-enable (or change the xorg file manually to "nvidia") xorg starts with a maximum 1024x780 resolution.

What could be wrong?. I read the later nvidia drivers had a bug when detecting monitor refresh rate and such, but that it was solved with the latest drivers also in dapper.

My xorg.conf file:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load	   "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "de"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "L70A Digital"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
    Monitor        "L70A Digital"
    DefaultDepth    24
    Option         "NoLogo"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection



```

---

### Post by bforbes on 2006-06-22
Your xorg.conf seems fine. Have you tried forcing the resolution by passing it from Grub? Something like this:
```

kernel          /boot/vmlinuz-2.6.16-1-k7 root=/dev/hda1 ro vga=1280x1024

```
That line, or lines if you have multiple kernels installed, are in /boot/grub/menu.lst.

---

### Post by Maikun on 2006-06-22
> Have you tried forcing the resolution by passing it from Grub?

I just tried and it doesn't work. Don't know what to try next.

By the way. A side effect of upgrading to dapper from breezy was for me randomly booting to tty1 instead of kdm.  Rather odd. It happens about a third of the times I boot my computer. Any ideas what it could be? Maybe related to the nvidia problems? (problably not, as it happens with the nv driver).

---

### Post by bforbes on 2006-06-23
Are you sure you added the vga parameter to every grub entry? Other than that I am pretty much stumped. The booting to tty1 issue I have no idea about. You could try a fresh install, but that's really a last resort.

One thing... does your xorg.conf file actually get changed at all? If so you should be able to track down what is changing it.

---

### Post by tseliot on 2006-06-23
[QUOTE=Maikun]I just tried and it doesn't work. Don't know what to try next.

By the way. A side effect of upgrading to dapper from breezy was for me randomly booting to tty1 instead of kdm.  Rather odd. It happens about a third of the times I boot my computer. Any ideas what it could be? Maybe related to the nvidia problems? (problably not, as it happens with the nv driver).[/QUOTE]
Try a fresh installation of Dapper from a Dapper CD (do not upgrade from Breezy)

---

### Post by Maikun on 2006-06-23
> Try a fresh installation of Dapper from a Dapper CD (do not upgrade from Breezy)

Well, that's an obvious solution, but I didn't post to get that answer ;)  

> 
One thing... does your xorg.conf file actually get changed at all? If so you should be able to track down what is changing it.

That's not the problem. Starting with my working "nv" xorg.conf, I just change it to "nvidia" and enable glx and it works (just at a maximum of 1024x780)

*sigh* I'll have to do without 3D accel until I do a clean install with edgy eft :rolleyes:

Thanks a lot anyway.

---

### Post by bforbes on 2006-06-23
Don't give up. There should be a solution to your problem. Have you tried installing the latest nVidia drivers from their website?

---

### Post by tseliot on 2006-06-24
[QUOTE=Maikun]Well, that's an obvious solution, but I didn't post to get that answer ;)  



That's not the problem. Starting with my working "nv" xorg.conf, I just change it to "nvidia" and enable glx and it works (just at a maximum of 1024x780)

*sigh* I'll have to do without 3D accel until I do a clean install with edgy eft :rolleyes:

Thanks a lot anyway.[/QUOTE]
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

If that doesn't work try point 10

---

### Post by Drifter on 2006-06-24
Have u tried easy ubuntu, it has the drivers in it and they are easy to install.

---

### Post by tseliot on 2006-06-24
[QUOTE=Drifter]Have u tried easy ubuntu, it has the drivers in it and they are easy to install.[/QUOTE]
Easy Ubuntu only installs the driver from the repository.

---

### Post by Maikun on 2006-06-25
Ok. I tried point 10 of tseliot's guide, and it didn't work. If I set the Option "UseEDID" "False", I get a resolution of 800x600. Setting Modes "1280x1024_60" doesn't seem to help, either (I get 1024x768 again if I don't disable EDID).

Point 5 is something I've already tried before, but i guess i could try again. I'll report back in a moment.

---

### Post by Maikun on 2006-06-25
Point 5 doesn't work either.

I guess the other possibility is to install the NVIDIA drivers the other way (with the nvidia_installer)

Thanks again.

---

