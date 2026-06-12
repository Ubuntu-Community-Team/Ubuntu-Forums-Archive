---
title: "Where is xorg.conf"
date: 2012-06-12
forum: General Help
---

### Post by satimis on 2012-06-12
Hi all,

Ubuntu 12.04 desktop

I can't locate xorg.conf.

$ ls /etc/X11/ ```

app-defaults                      fonts    xkb         Xsession
cursors                           rgb.txt  Xreset      Xsession.d
default-display-manager           X        Xreset.d    Xsession.options
default-display-manager.dpkg-tmp  xinit    Xresources  Xwrapper.config

```

Where is the file?  TIA

B.R.
satimis

---

### Post by papibe on 2012-06-12
Hi satimis.

It is not mandatory anymore. Xorg can work without it

If you need to generate one? If so, there are several options depending in which driver are you using (which depends also in your graphic card).

Regards.

---

### Post by deadflowr on 2012-06-12
If you don't have one it means your system doesn't need one to work right. 
However, what is your graphics card?

Certain graphics card have drivers built into the kernel(I think) like intel graphics cards, so they are configured already, no need for a configuration file.

---

### Post by Grenage on 2012-06-12
As above, they often aren't required (not that I think the alternatives are much better).

As you're looking for it, I assume you have a problem, or want to make some changes to your display; care to elaborate?

---

### Post by satimis on 2012-06-12
Hi,

Thanks for your advice.

This box has been working sometimes without problem so far.

CPU Phenom II X6
RAM	8G
OS	Ubuntu 12.04 64bit
on board Video card

$ sudo lshw -C video```

  *-display               
       description: VGA compatible controller
       product: RS780D [Radeon HD 3300]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:c000(size=256) memory:fbde0000-fbdeffff memory:fbc00000-fbcfffff

```

About 3 weeks ago I upgraded this box from Ubuntu 11.04 to Ubuntu 12.04.  It is working without problem.  Today I found the MS wireless mouse seemingly has problem.  Whenever I point it on browser/document etc. the page will scroll down automatically.  Therefore I tried to look at entries of xorg.conf and found it is missing.

That is the complete story.  What I need is to fix my mouse problem.  Is it the problem on the wireless mouse?  TIA

B.R.
satimis

---

### Post by Grenage on 2012-06-12
I would probably swap the mouse, or try it on another machine (if you can).  It may very well be a hardware problem.

---

