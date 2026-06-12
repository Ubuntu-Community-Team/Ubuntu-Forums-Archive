---
title: "Force screen resolution?"
date: 2012-06-11
forum: General Help
---

### Post by Cursed Lemon on 2012-06-11
Hi everyone! 

I'm currently trying to troubleshoot a situation in which the person I'm helping has an [ASUS LCD monitor]("http://www.asus.com/Display/LCD_Monitors/VW193DR/#specifications") that isn't displaying properly. The highest resolution available to her is 1024x768. Her computer is perfectly capable of outputting the 1440x900 native resolution of the monitor, but obviously drivers are at a premium here. 

I know that forcing resolution is possible, but I'm not quite sure how to do it, and past entries on it are rather scattered. She has the latest Ubuntu build. 

Any help?
[]("http://www.asus.com/Display/LCD_Monitors/VW193DR/#specifications")

---

### Post by sudodus on 2012-06-11
Can you find out what is the graphics chip or card? It might be a good idea to install a proprietary driver.

For example, what is the output of
```
glxinfo|grep -i opengl
```
or can you run the gui program ***hardinfo*** and look at the info for Display.

If you don't have the programs, you can search for them and install with ***Synaptics***.

Edit: by the way, is it a laptop, and you want to use an external monitor? In that case, maybe you need to switch off the internal screen, because it might limit the resolution. In many but not all versions of Ubuntu, it is possible to have different resolutions in the internal and external monitor/screen.

---

### Post by Cursed Lemon on 2012-06-11
> **sudodus said:**
> Can you find out what is the graphics chip or  card? It might be a good idea to install a proprietary driver.

For example, what is the output of
```
glxinfo|grep -i opengl
```

Comes back with "unable to open display." 

> or can you run the gui program ***hardinfo*** and look at the info for Display.
 
 If you don't have the programs, you can search for them and install with ***Synaptics***.Running hardinfo in the command line also gives me the same response. I'll run it in GUI form a little later on when she's not using the computer. 

> Edit: by the way, is it a laptop, and you want to use an external  monitor? In that case, maybe you need to switch off the internal  screen, because it might limit the resolution. In many but not all  versions of Ubuntu, it is possible to have different resolutions in the  internal and external monitor/screen.Nope, this is a small tower. :)

---

### Post by Cursed Lemon on 2012-06-11
Just FYI, I'm running these processes remotely.

---

### Post by sudodus on 2012-06-11
> **Cursed Lemon said:**
> Comes back with "unable to open display." 

Running hardinfo in the command line also gives me the same response. I'll run it in GUI form a little later on when she's not using the computer. 

Nope, this is a small tower. :)
Strange, do you run the glxinfo command from a terminal window?
And hardinfo started from the command line or the menu, should run as a GUI program. Are you running a remote session, or have you logged to locally on the computer?

---

### Post by sudodus on 2012-06-11
> **Cursed Lemon said:**
> Just FYI, I'm running these processes remotely.
OK, if you are running ssh, use the option -Y to enable graphics (X forwarding).

```
ssh -Y user@computer
```

---

### Post by mvs1207 on 2012-06-11
Since you are running remotely and would like to see GUI, make sure that you are running a local X server (like Xming for MS Windows) and then do 

```

ssh -X <your friends IP Address>

```

---

### Post by Cursed Lemon on 2012-06-11
I apologize, it seems that she is running 10.10, I was mistaken before and believed that she had the latest version. 

Hardinfo GUI only gives me this: 

Display Resolution: 1280x1024 pixels (was also mistaken on the screen size, but that's still 5:4 on a 16:10, :x )
OpenGL Renderer: Software Rasterizer 
X11 Vendor: The X.Org Foundation

---

### Post by sudodus on 2012-06-12
Ubuntu 10.10 has passed end of life. That means that she is no longer receiving security updates. I suggest that you try with the new version 12.04. Depending of the cpu, graphics card and ram, different flavours of Ubuntu might be the best, so if you can post information about it, we can give better help.

- Ubuntu with Unity desktop environment, modern and needs a lot of horsepower.

- Kubuntu with KDE desktop environment, modern and needs a lot of horsepower.

- Xubuntu with XFCE desktop environment, modern but simpler and needs less horsepower.

- Lubuntu with LXDE desktop environment, ultra-light-weight and needs the least horsepower or will be very fast on a powerful computer

I suggest that you download some iso-files and make boot CD or USB drives. Then test the flavours live (without installing to the internal drive).

---

### Post by Yellow Pasque on 2012-06-12
Get the Xorg log (/var/log/Xorg.0.log) and pastebin it.

---

### Post by Cursed Lemon on 2012-06-12
> **sudodus said:**
> Ubuntu 10.10 has passed end of life. That means that she is no longer receiving security updates. I suggest that you try with the new version 12.04. Depending of the cpu, graphics card and ram, different flavours of Ubuntu might be the best, so if you can post information about it, we can give better help.

- Ubuntu with Unity desktop environment, modern and needs a lot of horsepower.

- Kubuntu with KDE desktop environment, modern and needs a lot of horsepower.

- Xubuntu with XFCE desktop environment, modern but simpler and needs less horsepower.

- Lubuntu with LXDE desktop environment, ultra-light-weight and needs the least horsepower or will be very fast on a powerful computer

I suggest that you download some iso-files and make boot CD or USB drives. Then test the flavours live (without installing to the internal drive).

She will eventually be upgraded to the newest build, but I'm concerned that the monitor will continue presenting this problem.

---

### Post by LinGNUbie on 2012-06-12
Usually if there is a "tweak" needed for the monitor setup. then an upgrade will break that config and you will have to "tweak" again. I would suggest making a backup of the config (xorg.conf) once it is sorted out before an upgrade, so that it may be reused after the upgrade completes. Otherwise upgrade, then sort the monitor issue out.

---

### Post by Cursed Lemon on 2012-06-12
> **LinGNUbie said:**
> Usually if there is a "tweak" needed for the monitor setup. then an upgrade will break that config and you will have to "tweak" again. I would suggest making a backup of the config (xorg.conf) once it is sorted out before an upgrade, so that it may be reused after the upgrade completes. Otherwise upgrade, then sort the monitor issue out.

I'll grab a Xorg and pastebin it like was suggested later today (as I can't grab it out of Gedit remotely). 

The upgrade should happen fairly soon, so I'll see about fixing it in 10.10, then I'll try the same thing in 12.04. =)

---

### Post by Cursed Lemon on 2012-06-12
> **Temüjin said:**
> Get the Xorg log (/var/log/Xorg.0.log) and pastebin it.

Here is the Pastebin you wanted! 

[http://pastebin.com/BeqGPPeL](http://pastebin.com/BeqGPPeL)

---

### Post by Yellow Pasque on 2012-06-12
It's a SiS 741 GPU (yuck) and it's stuck with the generic VESA driver. Try manually setting the virtual screen size to 1440x900
[https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected)

---

### Post by LinGNUbie on 2012-06-12
After looking through the pastebin, it seems that the dde info is not being reported correctly to the drivers, so I would think that an xorg.conf with the correct settings should suffice to get the display working at the desired resolutions. After creating one and rebooting, be sure NOT to use Nvidia's control panel to configure displays, ONLY use the included display tool in the desktop or Nvidia's config will overwrite your created xorg.conf, corrupting it.

---

### Post by sudodus on 2012-06-13
> **Cursed Lemon said:**
> She will eventually be upgraded to the newest build, but I'm concerned that the monitor will continue presenting this problem.
Often (particularly if the computer is fairly new compared to the operating system) the hardware detection does not work properly. So it is really worthwhile to test the new 12.04 version of [KLX]ubuntu live (booted from CD/USB). It has a fair chance to succeed without tweaking (because of the improved/updated hardware detection and drivers in the kernel).

---

### Post by LinGNUbie on 2012-06-15
Any further progress?

---

