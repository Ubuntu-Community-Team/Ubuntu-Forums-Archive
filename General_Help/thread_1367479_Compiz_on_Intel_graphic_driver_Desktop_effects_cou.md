---
title: "Compiz on Intel graphic driver: Desktop effects could not be enabled"
date: 2009-12-29
forum: General Help
---

### Post by abcuser on 2009-12-29
Hi,
on Ubuntu 9.10 I have tried to enable compiz from System | Preferences | Appearance | Visual Effects | Extra and got error: "Desktop effects could not be enabled".

So I have downloaded [compiz-check](http://forlong.blogage.de/entries/pages/Compiz-Check) and executed script. The output is:
```

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

I also got message that this graphic card is in blacklist and I selected yes to remove it from blacklist.

I have also checked and there is no proprietary driver listed in System | Administration | Hardware Drivers.

When I try to enable compiz background picture is displayed and then Ubuntu freezes.

Any idea how to enable compiz?

Regards

---

### Post by ywh842005 on 2009-12-29
I have intel GMA 4500MDH which runs smoothly, and i run compiz-check, getting the same result with u. 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

I think it is the problem with ur driver.

---

### Post by abcuser on 2009-12-29
> **ywh842005 said:**
> I think it is the problem with ur driver.
Hi,
when installing Ubuntu 9.10 system always froze during install, so I selected "low graphic" before installing and then Ubuntu installed successfully.

I have executed ./compiz-check and got error that "vesa" card is not supported. I have found on web that I should replace "vesa" from
/etc/X11/xorg.conf and replace it with "intel" in Device section.
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

```
I changed to "intel" and rebooted, when rerun the compiz-check I got message from first post.

How do reinstall Intel graphic driver?
Regards

---

### Post by falconindy on 2009-12-29
Just because compositing is available doesn't necessarily mean its enabled. Add this to /etc/X11/xorg.conf:

```
Section "Extensions"
	Option         "Composite" "Enable"
EndSection
```

Restart GDM, try again.

---

### Post by abcuser on 2009-12-29
falconindy, I tried your suggestion and Ubuntu still freezes.

---

### Post by falconindy on 2009-12-29
> **abcuser said:**
> falconindy, I tried your suggestion and Ubuntu still freezes.
I notice you've got Intel graphics. Are you using Kernel Mode Setting? If not, there's a million tutorials on how to enable it.

---

### Post by abcuser on 2009-12-30
> **falconindy said:**
> Are you using Kernel Mode Setting? If not, there's a million tutorials on how to enable it.
Hi,
I have set [kernel mode settings](http://codsplaice.blogspot.com/2009/10/enabling-kernel-mode-setting-with.html) and when turning on compiz (System | Preferences | Appearance...) Ubuntu freezes too.

Any idea what could be wrong with my compiz?
Regards

---

