---
title: "Screen Brightness, on v11"
date: 2011-12-19
forum: General Help
---

### Post by sdad46 on 2011-12-19
Just picked up an HP laptop.  I kept the Windows 7 recovery partition and trashed the rest in favor of Ubuntu 11.

I have lost the use of the special functions on the keyboard, but with 1 exception, that's fine by me.   The one caveat is the screen brightness default, which is dim in my version of Ubuntu. Certainly makes sense for a laptop, and I can easily enough adjust this by use of the screen control, but the control reverts back to dim when power is cycled.  This causes some aggravation in a brightly lit room, as the mouse icon is difficult if not impossible to see. I am wondering where I might find the control text which I could modify to set the brightness to some other value, say, for instance, 50% at startup rather than 0.  Proper syntax may be of some value, also.

---

### Post by Toz on 2011-12-19
The backlight interface files are located at **/sys/class/backlight**. Depending on the laptop and configuration, you may have one or more directories in that location. Assuming the directory *acpi_video*, you should have some further files on that directory including:
- *brightness* (the current brightness value)
- *max_brightness* (the maximum brightness value)

You should be able to directly manipulate the brightness by echoing a value into the brightness file like:
```
echo [COLOR="Red"]5[/COLOR] | sudo tee /sys/class/brightness/[COLOR="Red"]acpi_video[/COLOR]/brightness
```
...(make sure to change acpi_video to your correct interface and the value of 5 should be a value between 0 and the contents of max_brightness).

Now assuming this all works and you determine the brightness level that you want on boot, simply add the following command to your /etc/rc.local file (above the existing *exit 0* command:
```
echo [COLOR="Red"]5[/COLOR] > /sys/class/backlight/[COLOR="Red"]acpi_video[/COLOR]/brightness
```
...again adjusting the values 5 and acpi_video accordingly.

Note: You will need to edit /etc/rc.local with sudo rights:
```
sudo gedit /etc/rc.local
```

---

### Post by sdad46 on 2011-12-19
Thanks, Taz, I'll  chase that down shortly.:p

---

### Post by aeronutt on 2011-12-19
I'd like to do the same thing (have brightness at something other than default at boot), but there are no 'brightness' files in the /sys/class directory. And, there's no /sys/class/backlight directory. (11.10)

---

### Post by Toz on 2011-12-19
> **aeronutt said:**
> I'd like to do the same thing (have brightness at something other than default at boot), but there are no 'brightness' files in the /sys/class directory. And, there's no /sys/class/backlight directory. (11.10)

What is the make/model of your system and what is the result of:
```
cat /proc/cmdline
```

---

### Post by aeronutt on 2011-12-19
> **Toz said:**
> What is the make/model of your system and what is the result of:
```
cat /proc/cmdline
```

Dell Vostro 3500, and 

```
BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=xxxxxxxxxxxxxxxxxxxxxxxxxxx ro i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```

Thanks.

---

### Post by Dans564 on 2011-12-19
what hp laptop u on.  Im on a dv6 and have ways of getting basically everything working so if u have a dv6 ur in luck

---

### Post by JC Cheloven on 2011-12-19
> **sdad46 said:**
> Just picked up an HP laptop.  I kept the Windows 7 recovery partition and trashed the rest in favor of Ubuntu 11.
Just be aware: perhaps that recovery partition is no longer usable. It's usually hard-chained to the orginal OS installed by the manufacturer. It happened to me on several laptops already. And when I asked to the tech support I usually was told something as "the recovery partition has lost its reference, it is no longer usable". Period :(

As for your main question, try this at terminal

```
xrandr --output LVDS1 --brightness 0.5
```

Change 0.5 for something suitable for you (0.7, 1.1, 1.5 ...). That's not permanent, but if you like the result, it can be put to be run at login, so that you find the screen like you want from the beginning.

---

### Post by aeronutt on 2011-12-19
> **JC Cheloven said:**
> Just be aware: perhaps that recovery partition is no longer usable. It's usually hard-chained to the orginal OS installed by the manufacturer. It happened to me on several laptops already. And when I asked to the tech support I usually was told something as "the recovery partition has lost its reference, it is no longer usable". Period :(

As for your main question, try this at terminal

```
xrandr --output LVDS1 --brightness 0.5
```

Change 0.5 for something suitable for you (0.7, 1.1, 1.5 ...). That's not permanent, but if you like the result, it can be put to be run at login, so that you find the screen like you want from the beginning.

Wow, I just ran this on my Dell...and contrast went to 'very washed out', had to reboot. :):)

---

### Post by bdemers on 2011-12-19
Thanks Toz.  The how-to worked just fine on my HP G72.  Added the line to the startup file and away we go!!!!!!!!!!!

The further discussion on the recovery partition is a bit disconcerting, however.  I have yet any reason to look at it, but if all else fails I'll just add that partition to the rest of Ubuntu. I was keeping it just so if I got rid of the laptop, I could return it to Windows 7.  I run XP in Virtualbox.  Box supplies all the drivers and I see very little if any performance degradation. Even cooler, I moved my XP over from a different laptop.  Exported XP as an appliance from old machine, imported into new.  Driver issues?, what driver issues?

---

### Post by Toz on 2011-12-19
> **aeronutt said:**
> I'd like to do the same thing (have brightness at something other than default at boot), but there are no 'brightness' files in the /sys/class directory. And, there's no /sys/class/backlight directory. (11.10)

What video card do you have and which driver are you using?
```
sudo lspci -vnn | grep -A10 VGA
```

---

### Post by aeronutt on 2011-12-20
FYI, the AMD Radeon graphics chip is disabled.

```
 $ sudo lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [xxxx:xxxx] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [xxxx:xxxx]
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series] [xxxx:xxxx] (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: radeon
	Kernel modules: radeon

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [xxxx:xxxx]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at d000 [size=256]
	Memory at f1104000 (64-bit, prefetchable) [size=4K]
	Memory at f1100000 (64-bit, prefetchable) [size=16K]

```

---

### Post by Toz on 2011-12-20
> **aeronutt said:**
> FYI, the AMD Radeon graphics chip is disabled.

```
 $ sudo lspci -vnn | grep -A10 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [xxxx:xxxx] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [xxxx:xxxx]
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at f6400000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Whistler [AMD Radeon HD 6600M Series] [xxxx:xxxx] (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: radeon
	Kernel modules: radeon

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [xxxx:xxxx]
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at d000 [size=256]
	Memory at f1104000 (64-bit, prefetchable) [size=4K]
	Memory at f1100000 (64-bit, prefetchable) [size=16K]

```

Do the following commands adjust brightness:
```

sudo setpci -s 00:02.0 F4.B=A0
sudo setpci -s 00:02.0 F4.B=C0
sudo setpci -s 00:02.0 F4.B=E0

```

---

### Post by aeronutt on 2011-12-20
> **Toz said:**
> Do the following commands adjust brightness:
```

sudo setpci -s 00:02.0 F4.B=A0
sudo setpci -s 00:02.0 F4.B=C0
sudo setpci -s 00:02.0 F4.B=E0

```

Nope, no change at all.

---

### Post by Toz on 2011-12-20
> **aeronutt said:**
> Nope, no change at all.

Can you post back the contents of /var/log/Xorg.0.log? Also, have a look at this link for another method: [http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/]("http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/").

---

### Post by aeronutt on 2011-12-21
> **Toz said:**
> Can you post back the contents of /var/log/Xorg.0.log? Also, have a look at this link for another method: [http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/]("http://blog.ishans.info/2011/09/25/set-brightness-automatically-at-the-startup-in-linux/").

Thanks for the help! I'll give these a try.
EDIT: This script works! I put it in /etc/xdg/autostart, so it takes effect after login, not at the login screen. I'm going to try adding it to init.d.

---

