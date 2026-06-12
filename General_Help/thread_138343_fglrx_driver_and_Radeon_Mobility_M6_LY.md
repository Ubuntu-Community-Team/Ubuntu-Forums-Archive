---
title: "fglrx driver and Radeon Mobility M6 LY?"
date: 2006-03-01
forum: General Help
---

### Post by event on 2006-03-01
I'm trying to get the fglrx drivers working with my roommate's laptop, which is an HP Pavillion ze5000s, and has a Radeon Mobility M6 LY. I'm using ubuntu 5.10.

I've followed some HOWTOs about installing te fglrx drivers, but once I change the driver to "fglrx" in xorg.conf and restart the X environment, the X environment crashes and wont boot.

I try the command sudo fglrxinfo and get this error message:
```
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/volatile/fglrx.ko): No such device
```

How can I enable 3d acceleration with this video card?

---

### Post by Belgy on 2006-03-15
I have the exact same card in my Thinkpad X22, and I can't for the life of me get 3d acceleration working. This is in Dapper though, but, I am pretty sure when I had Breezy on here, it worked just fine. I think something's broke in the kernel.

Love to know if anyone has an answer/work around, then maybe, just maybe, I could get me some Xgl/Compiz loving, although from what I've read, this particular card is a little at the lower end when it comes to Xgl...

---

### Post by joelito on 2006-03-15
Can you point to at least some of the HOWTOS you refer to, maybe I can help narrow the necesary steps (What works for me)

---

### Post by Belgy on 2006-03-15
I've tried _ALL_ of the HOWTOs, and none of them work to get 3d acceleration working on this.

Personally for me it's not that big of a deal to get 3d acceleration working on this laptop, but, it sure would be nice to show off Xgl to my uni friends who can't wait for Vista.

---

### Post by sublime on 2006-03-15
i just went through 4 hours of reading guides and trying stuff to get my x200m working with breezy and i finally found one that worked.  [this guide](http://wiki.cchtml.com/index.php/Ubuntu) is the only one that worked for me.  just make sure you read it very carefully and also make sure to save your madwifi drivers if your roommate uses an atheros wireless card.  its all detailed in the guide

---

### Post by joelito on 2006-03-22
OK. Assuming you are using the drivers from the repositories, these are the steps that worked for me. I can't help you if you are downloading from the ATI website.

Turning off the Xserver from a terminal [CTRL+ALT+F1]
```

sudo /etc/init.d/gdm stop (could be /etc/init.d/kdm if using kubuntu)

```

reinstall the driver and the linux restricted modules
```

sudo apt-get --reinstall install linux-restricted-modules-$(uname -r) xorg-driver-fglrx

```

configure the xserver with
```

sudo nano /etc/X11/xorg.conf

```

Modify your "Device" section so it will look like this. Change the identifier if you want
```

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

```

[COLOR="Red"]Restart Your Computer[/COLOR]
```

sudo restart

```

if everything worked then you sould see this from the gnome-terminal or konsole when using "fglrxinfo"
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1050 (X4.3.0-8.23.7)

```

---

