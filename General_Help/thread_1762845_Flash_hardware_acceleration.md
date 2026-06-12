---
title: "Flash hardware acceleration"
date: 2011-05-19
forum: General Help
---

### Post by lordgibbness on 2011-05-19
System: Acer Revo R3700 (64-bit Atom CPU / Nvidia ION GPU)
OS: Ubuntu 10.10 64-bit (amd64)

Hi,

I have followed various guides (liks below) to try and get Flash 10.2 (actually recently installed 10.3) to run with full hardware acceleration but I don't seem to have been very sucessful.

When I run an HD flash video (from Youtube for example) it still drops frames and reports the video mode as "undefined video rendering".

[Link 1]("http://blog.aleutia.com/2011/02/01/flash-10-2-hardware-acceleration-in-ubuntu-linux/")

[Link 2]("http://askubuntu.com/questions/16172/getting-flash-10-2-gpu-acceleration-working")

This is quite important as I want to use this machine as a media PC but the flash performance using the CPU is very slow.  When using XBMC media software the flash performance is excellent (but not every website - e.g. Lovefilm in the UK - is supported in XBMC).

If you could help it would be most appreciated.

Thanks,
Rob.

---

### Post by lordgibbness on 2011-05-21
If this isn't the best forum to find people using ubuntu with an acer revo - can anyone recommend a site that I could use?

I'm sure there must be people out there who have got flash and ubuntu working properly together - I probably just need to find the correct file to edit...

---

### Post by lovinglinux on 2011-05-21
If you are using a vdpau supported nVidia card, you can make flash work with it. Install vdpau, then use [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") to apply the necessary tweak to use it. However, I don't think the 64bit version of flash has vdpau support.

---

