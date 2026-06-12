---
title: "Gnome Power Manager Broken"
date: 2010-04-25
forum: General Help
---

### Post by lvleph on 2010-04-25
I am having issues with Gnome Power Manager. My wife and I have identical computers, with Linux Mint 8 installed on both. My Linux Mint 8 is a fresh install, whereas her's was an upgrade. 

Anyway, when I click suspend or hibernate nothing happens, not even an error. On my wife's computer this works just fine.
**sudo pm-hibernate**, **sudo pm-suspend**, and **sudo /etc/acpi/hibernate.sh** do absolutely nothing.

On the other hand
**pmi action sleep**
```

method return sender=:1.1 -> dest=:1.315 reply_serial=2
   int32 1

```

The output from **lshal | grep power_management** is
```

  power_management.acpi.linux.version = '20090521'  (string)
  power_management.can_hibernate = true  (bool)
  power_management.can_suspend = true  (bool)
  power_management.can_suspend_hybrid = false  (bool)
  power_management.is_powersave_set = false  (bool)
  power_management.quirk.dpms_on = true  (bool)
  power_management.quirk.dpms_suspend = true  (bool)
  power_management.quirk.vbe_post = true  (bool)
  power_management.quirk.vbemode_restore = true  (bool)
  power_management.quirk.vbestate_restore = true  (bool)
  power_management.quirk.vga_mode_3 = true  (bool)
  power_management.type = 'acpi'  (string)

```

So I installed uswsusp. From here I tested it with **s2ram** and got the following
```
/dev/mem: Permission denied
Machine is unknown.
This machine can be identified by:
    sys_vendor   = ""
    sys_product  = ""
    sys_version  = ""
    bios_version = ""
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
```
I then tried the same command with sudo and got 
```
Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Gateway         "
    sys_product  = "LT31            "
    sys_version  = "Not Applicable"
    bios_version = "v1.3201 "
See http://suspend.sf.net/s2ram-support.html for details.

If you report a problem, please include the complete output above.
```
Okay, so my comp is not on the white list. So I ran **sudo s2ram -f** and now it went to sleep. I wanted to switch out pmi with uswsusp and so I ran
```

sudo dpkg-divert --rename --divert /usr/sbin/pmi-disabled /usr/sbin/pmi

```
I have also tried **s2ram -f** and got
```

fgconsole: getconsolefd: Invalid argument
Switching from vt-1 to vt1
chvt: VT_ACTIVATE: Bad file descriptor
VT_WAITACTIVE: Bad file descriptor
Segmentation fault

```
However, none of this allows me to just push the sleep button. Not sure where to go from here.

---

### Post by lvleph on 2010-04-26
No one?

---

### Post by lvleph on 2010-04-27
Wow, this sucks. I know the issue is fixed with Lucid, but then I have other things that are broken.

---

### Post by lvleph on 2010-05-02
Well, I ended up upgrading to Linux Mint 9. Then just went back to the old kernel since graphics are broke for me with the new kernel.

---

