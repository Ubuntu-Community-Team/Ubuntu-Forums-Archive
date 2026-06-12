---
title: "Brightness Control Doesn't Work?"
date: 2011-03-17
forum: General Help
---

### Post by khoraski on 2011-03-17
I added the Brightness Applet to the top panel, but when I change the brightness, nothing happens. D:
I can't stand this, it's like my screen is stuck on supa-bright and it's hurting my eyes.
When I load my PC up in Windows, the brightness control works just fine. But it doesn't seem to work on Ubuntu.

---

### Post by realzippy on 2011-03-17
Which graphics card,driver do you use?
Is it a laptop?If so,which one?
Which ubuntu version?Gnome or KDE?

---

### Post by khoraski on 2011-03-17
> **realzippy said:**
> Which graphics card,driver do you use?
Is it a laptop?If so,which one?
Which ubuntu version?Gnome or KDE?

All I know is I use an Acer laptop, and Ubuntu 10.04 LTS.

---

### Post by realzippy on 2011-03-17
So open a terminal,type

```
lspci | grep  VGA
```

and post the command's output here.

---

### Post by khoraski on 2011-03-17
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

---

### Post by realzippy on 2011-03-17
And this one to get your laptop model:

```
sudo dmidecode -s system-product-name
```

---

### Post by khoraski on 2011-03-17
```
Aspire 5336
```

---

### Post by realzippy on 2011-03-17
There are several bugs and several workarounds existing for your intel vga
device,eg:

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041)

...seems as you had to play with several boot options as suggested in the bug-reports.Take a can of tea & time and read through the given links.
Sorry,but there seems not to be an instant solution.

---

### Post by Zevaka on 2011-03-17
use
```
sudo setpci -s 00:02.0 F4.B=XX
```
where XX can change from 00 (absolute darkness) to FF (full brightness)
temporary fix, but you can automize it on ac power on/off

---

### Post by khoraski on 2011-03-17
> **realzippy said:**
> There are several bugs and several workarounds existing for your intel vga
device,eg:

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948?comments=all)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041)

...seems as you had to play with several boot options as suggested in the bug-reports.Take a can of tea & time and read through the given links.
Sorry,but there seems not to be an instant solution.

I read one of them and found out how to change the brightness, but it only works per window. So I change the brightness of the window, and not the screen. It's okay, but I still wish it fixed.

---

