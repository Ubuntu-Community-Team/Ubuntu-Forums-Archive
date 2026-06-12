---
title: "Textures do not load in 3d games, some screensavers slow."
date: 2012-08-23
forum: General Help
---

### Post by flyingfisch on 2012-08-23
Hi.

When I play FlightGear the textures do not load (the planes are black). Also, some screensavers don't run as fast as on my old (slower) computer.

I am wondering what the problem is.

My screen resolution is 1280x1024, in case that helps.

```

flyingfisch@Office-OptiPlex-745:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fea00000-feafffff memory:d0000000-dfffffff ioport:ecb8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff

```I remember reading somewhere that the i915 driver is bad but I don't know. Maybe its not even a graphics card problem. Any help would be great :)

Also, I don't know why it says I have 2 displays... I only have 1.

---

### Post by dolson60174 on 2012-08-25
i too have the i915 and same issue....if i find something i will post it up

---

### Post by flyingfisch on 2012-08-25
Did blacklisting the i915 driver do anything? I haven't tried it yet, but I was just wondering.

I tried using "nomodeset" in grub, but all that happened was I lost my 3d support, and could not log in to Ubuntu 3D.

GLXGears gives me 35fps without nomodeset and 25fps with it.

Compiz check output (without nomodeset):

```

flyingfisch@Office-OptiPlex-745:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 12.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 



```

---

### Post by flyingfisch on 2012-08-26
Bump.

---

### Post by flyingfisch on 2012-09-10
Bump.

---

### Post by flyingfisch on 2012-09-27
Umm, bump. :-\

EDIT:

OK, even though I do not have a 64 bit version OS running and it seems unrelated, this worked for me: [http://askubuntu.com/questions/73909/screen-tearing-in-11-10-with-intel-graphics](http://askubuntu.com/questions/73909/screen-tearing-in-11-10-with-intel-graphics)


In compiz I added the two options in workarounds.

EDIT2:

That only worked for some 3D things. FlightGear looks like this. My old computer did better than that.

---

