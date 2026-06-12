---
title: "desktop does not display with hi-res nvidia"
date: 2011-04-15
forum: General Help
---

### Post by gwfong on 2011-04-15
I'm running Ubuntu 10.10 on a Dell m65 mobile precision laptop w/ nNvidia card.

I booted up my system. Login screen appears. I login. I can hear the login sounds. I can hear my notifications telling me I have email. My mouse works. My keyboard works. But I don't see my desktop. All that's in front of me is the background that I had at login time. I don't see the panels nor the desktop icons. I don't see the interactive grouping/stretchy rectangle thingy when clicking and dragging on the desktop.

I've never experienced this before. I never had a problem w/ this before. I had always been running in hi-res mode.

I did update my system earlier this morning and it wasn't until this afternoon I had to reboot it.

These are the things I've tried, none of which worked.

1) Downgraded my nVidia driver version
2) Changed the xorg.conf to a generic version with basic resolution (I had been running 1900x1200)
3) Tried restarting nautilus. I did this from the command prompt. I just get "Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon.
4) Tried an older kernel
5) Turned off compiz

These are the things I've tried and they do work

1) Boot to recovery menu. Run in failsafeX mode. I can see my desktop but everything is huge.
2) Run Desktop Edition (Safe Mode). I can see my desktop but everything is huge. I also notice that my desktop icons had been moved around. I think I was doing this when I couldn't see them!!
3) When in Safe Mode, I can configure my nVidia settings to be hi-res. But I can't these settings to stick when booting to normal mode.


All help is appreciated.

Gary

---

### Post by csh on 2011-04-15
> **gwfong said:**
> I'm running Ubuntu 10.10 on a Dell m65 mobile precision laptop w/ nNvidia card.

I booted up my system. Login screen appears. I login. I can hear the login sounds. I can hear my notifications telling me I have email. My mouse works. My keyboard works. But I don't see my desktop. All that's in front of me is the background that I has at login time. I don't see the panels nor the desktop icons. I don't see the 

I've never experienced this before. I never had a problem w/ this before. I had always been running in hi-res mode.

I did update my system earlier this morning and it wasn't until this afternoon I had to reboot it.

These are the things I've tried, none of which worked.

1) Downgraded my nVidia driver version
2) Changed the xorg.conf to a generic version with basic resolution (I had been running 1900x1200)
3) Tried restarting nautilus. I did this from the command prompt. I just get "Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon.
4) Tried an older kernel
5) Turned off compiz

These are the things I've tried and they do work

1) Boot to recovery menu. Run in failsafeX mode. I can see my desktop but everything is huge.
2) Run Desktop Edition (Safe Mode). I can see my desktop but everything is huge. I also notice that my desktop icons had been moved around. I think I was doing this when I couldn't see them!!

All help is appreciated.

Gary

Which Nvidia card do your laptop use? Does it have Nvidia Optimus technology?

Can you tell more information about your hardware (e.g. RAM, video memory, etc)?

If your laptop has Nvidia Optimus technology, does your BIOS have any setting to disable this feature by setting to dedicated graphic instead of integrated graphic?

---

### Post by K_45 on 2011-04-15
Apart from the above, start up safe mode, enter this in the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```Reboot. Result?

---

### Post by gwfong on 2011-04-15
NVIDIA Quadro FX 350M 512MB TurboCache (256MB dedicated, up to an additional 256MB shared)
Video BIOS: 005.072.023.021.101.000
LCD: 15.4" Wide UXGA
RAM: 4GB
Disk: 500GB

I didn't see any BIOS setting about Optimus technology. I did see one about using a video card via the dock versus the internal video card. I'm not running on a dock so it shouldn't be an issue. Regardless, I switched it to internal just remove a variable.

The tech specs are here:
[http://www.dell.com/downloads/global/products/precn/en/spec_precn_m65_en_updated.pdf](http://www.dell.com/downloads/global/products/precn/en/spec_precn_m65_en_updated.pdf)

---

### Post by gwfong on 2011-04-15
OK, tried this. It didn't work. There was no difference that I could see.


> **K_45 said:**
> Apart from the above, start up safe mode, enter this in the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```Reboot. Result?

---

### Post by K_45 on 2011-04-15
Try here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by gwfong on 2011-04-15
Yeah, that's the page in my other browser tab. Thanks.

> **K_45 said:**
> Try here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

