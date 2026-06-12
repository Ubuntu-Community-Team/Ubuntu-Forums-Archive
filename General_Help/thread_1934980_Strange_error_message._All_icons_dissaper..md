---
title: "Strange error message. All icons dissaper."
date: 2012-03-03
forum: General Help
---

### Post by inf1nity on 2012-03-03
Hi guys,
I am running Ubuntu 11.10 on Linux 3.0.0 -12-generic. Here are a couple of issues-

1.Sometimes when i boot up, the main loading screen(or whatever it is called) doesn't stretch to the whole screen but shows only partially like this

[[IMG]http://img685.imageshack.us/img685/5794/screenshotat20120303193.png[/IMG]](http://imageshack.us/photo/my-images/685/screenshotat20120303193.png/)


2. Also, sometimes, on startup i get the following error message-

[[IMG]http://img832.imageshack.us/img832/8898/screenshotat20120303194.png[/IMG]](http://imageshack.us/photo/my-images/832/screenshotat20120303194.png/)


And after that, all icons change to default and instead of the normal black theme, my desktop becomes like this-

[[IMG]http://img580.imageshack.us/img580/4323/aftererror.png[/IMG]](http://imageshack.us/photo/my-images/580/aftererror.png/)

Whats happening..??

---

### Post by MG&amp;TL on 2012-03-03
It looks like a graphics/resolution problem. Can you open a terminal (Ctrl-Alt-T) and give us the output of:

```
lspci
```

and what resolution does your monitor normally support? Also, hardware specs would be helpful.

As for the default theme, that is a bit odd. We'll fix the resolution first, then see if we can work on that.

---

### Post by inf1nity on 2012-03-03
Output of lspci-

```
kaustubh@E4500-13285:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

---

### Post by inf1nity on 2012-03-03
> **MG&TL said:**
> what resolution does your monitor normally support? Also, hardware specs would be helpful.

Here are my system specifications(As seen in System Info)-

   Memory      993.9 MiB
Processor    Intel® Core&#8482;2 Duo CPU E4500 @ 2.20GHz × 2
 Graphics      Intel® 945G x86/MMX/SSE2
  OS Type       32-bit
     Disk            8.2 GB

My monitor's native resolution is 1280x1024. But i have run it on 800x600 and 1024x768 for a long time without any problem (In windows 1024x768 is the permanent resolution).

---

### Post by MG&amp;TL on 2012-03-03
[LEFT]Well, IDK how to fix it, but googling your chip results in this: [http://askubuntu.com/questions/50966/screen-corruption-with-946g-82945g-gz](http://askubuntu.com/questions/50966/screen-corruption-with-946g-82945g-gz)

Which might give you more information.
[]("http://askubuntu.com/questions/50966/screen-corruption-with-946g-82945g-gz")[/LEFT]

---

