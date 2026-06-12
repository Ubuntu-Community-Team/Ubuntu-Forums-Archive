---
title: "Missing driver file on clean install? (X800 GTO PCI-E)"
date: 2006-03-30
forum: General Help
---

### Post by Psycho` on 2006-03-30
As a new linux user I installed Ubuntu earlier. After setup and configuration running smoothly, I rebooted the machine and on startup got an XWindow error (no screens found).

I visited [http://wiki.x.org](http://wiki.x.org) as suggested and read through the FAQ. This is what was suggested:

[I](EE) No devices detected.

Fatal server error:
no screens found

It is very likely that your xorg.conf file doesn't contain the correct driver(s) for the chipset(s) in your system or that your chipset isn't supported by any of the drivers.
You can check for the detected devices in the log file (in most cases /var/log/Xorg.0.log) by looking for lines like:
(--) PCI:*(1:0:0) Neomagic Corporation NM2200 [MagicGraph 256AV] rev 32, Mem @ 0xfd000000/24, 0xfe800000/22, 0xfec00000/20
In this example the active video device (the one with the *) is a Neomagic NM2200 video chip. In order to get this chipset to work you'd have to use the neomagic driver.
If you are using a distribution you should rerun its configuration tool. If there is no such tool, or if it keeps configuring your Xserver wrong you may want to try xorgcfg, the graphical tool shipped with Xorg. You can also let the server generate a config file: as root just run X -configure.[/I]

I did the latter in this case, and ran X -configure at root, which gave an error message along the lines of driver file missing. I'm now lost with what to do :confused:

---

### Post by RoboJ1M on 2006-03-31
sudo dpkg-reconfigure xserver-xorg

That command generates a new /etc/X11/xorg.conf for you depending on your choices.

Choose mostly default options, chipset selection should be ati.

Then reboot and see what happens.

Once you have the ati driver, you can start trying to replace it with the fglrx driver that enables 2D/3D.

I say start, because it's pain incarnate trying to get ATI cards to work.
I'm also new at this and I'm getting nowhere fast.

Remember to not install the built in fglrx, I believe only the latest version off of the ATI site supports that chipset.

There is a very good HOWTO in the HOWTO section of these forums on installaing the latest version.

Regards,

J1M.

---

