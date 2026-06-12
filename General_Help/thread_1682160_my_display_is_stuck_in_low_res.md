---
title: "my display is stuck in low res"
date: 2011-02-05
forum: General Help
---

### Post by punkbohemian on 2011-02-05
I recently updated ubuntu (I'm still using hardy heron), and during the restart, it prompted me to select my monitor. However, I haven't done anything with my hardware in years, so I don't remember the exact model of my monitor (I know it's an hp pavillion dv6000 laptop). I'm guessing that until I select the right model, ubuntu will only display in low res mode. Is there some terminal command that will can tell me the model of my monitor? Or, is there any other way I can I solve this problem? Thanks.

---

### Post by GOROSSI on 2011-02-05
run this command using a terminal  to find your monitor model 

sudo lshw | less 

then you should be able to select by going system >> administration >> display 

faling that edit your xorg.conf in /etc/X11 as root

---

### Post by punkbohemian on 2011-02-05
I'm not sure if that worked. I don't have the system>>admin>>display option. Also, that command line returned:

```

linux-box
    description: Notebook
    product: HP Pavilion dv6700 Notebook PC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF835123Z
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4638-3335-3132-335A-001E68D702AE
  *-core
       description: Motherboard
       product: 30D2
       vendor: Quanta
       physical id: 0
       version: 79.2E
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.58 (06/16/2008)
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu:0
          description: CPU

```

I'm not seeing anything telling me about my display.

---

### Post by spaceboy909 on 2011-02-06
Btw, are you still using Hardy?  If not, which distro?  You might consider upgrading; it might make for an easier video setup as Hardy is a couple of years old now.

Looks like it might be one of these:  [SIZE=2]

"Graphics: Optional  NVIDIA  GeForce Go 7200 discrete graphics. Standard NVIDIA GeForce Go 6150  graphics and NVIDIA nForce Go 430 chipset with AMD processors."
[/SIZE]

---

### Post by punkbohemian on 2011-02-06
Yeah, I'm still using hardy. It works for me (well, until now :P). 

So, yeah, I know I have an NVIDIA driver, and I activated it in the settings, but the pop up menu is asking me about my monitor (and there are literally hundreds of options). The only thing that will work (so far) is the generic plug and play option which is only low res.

---

### Post by dino99 on 2011-02-06
i dig my memory but its so far :(

it seems to be an xorg.conf issue. The actual kernel directly deal with X, so no need of xorg.conf, but it depend of which kernel you are using.

re-run nvidia-settings to rebuild xorg.conf

---

### Post by punkbohemian on 2011-02-06
I re-ran it and it said that I apparently wasn't using a nvidia driver (even though it's active under my hardware drivers. When I went to the nvidia settings, it told me to run nvidia-xconfig, which gave me this output:

```

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

```

I'm guessing this isn't good.

---

### Post by punkbohemian on 2011-02-08
*bump*

---

### Post by dino99 on 2011-02-08
if you use a recent kernel (> 2.6.32) then you can remove xorg.conf

sudo rm /etc/X11/xorg.conf

or rename it if you find that scary

---

### Post by punkbohemian on 2011-02-09
Ok, so here's what happens. I run: 

```
sudo rm /etc/X11/xorg.conf
```

and restart my computer. I'm then in a high res mode, but my nvidia is disabled. So, I enable the drivers (again), and have to restart the computer. When I do that, it drops back to low res mode and during start up it pops up the monitor selection box.

So, while I can technically get a high-res mode, it's not really fixed. Any other ideas? Thanks.

---

### Post by whatthefunk on 2011-02-09
Enable your drivers then do:

```
less /etc/X11/xorg.conf
```

Is there anything there?  If so, show us.  It sounds like enabling your drivers may be rewriting the xorg.conf file.

---

### Post by punkbohemian on 2011-02-10
I guess it is rebuilding that file. When I run that command, I get this:

```

Section "Device"
        Identifier      "Default Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Defaultdepth    24
EndSection

```

---

### Post by cyb3r_sn4k3 on 2011-02-10
Did you try nvidia-xconfig?

---

### Post by punkbohemian on 2011-02-10
Should I run nvidia-xconfig after deleting xorg.conf or after re-enabling the nvidia drivers, and restarting the computer, which rebuilds xorg.conf?

---

### Post by punkbohemian on 2011-02-16
*bump*

---

### Post by jwcalla on 2011-02-16
> **punkbohemian said:**
> Should I run nvidia-xconfig after deleting xorg.conf or after re-enabling the nvidia drivers, and restarting the computer, which rebuilds xorg.conf?

Make sure the nvidia drivers are enabled, make a backup copy of xorg.conf just in case, then run nvidia-xconfig with admin privileges

sudo cp /etc/X11/xorg.conf ~/xorg.conf.backup
sudo nvidia-xconfig

then

sudo nvidia-settings

and see if any monitors or resolutions are listed in the display configuration

then post your new xorg.conf here

---

