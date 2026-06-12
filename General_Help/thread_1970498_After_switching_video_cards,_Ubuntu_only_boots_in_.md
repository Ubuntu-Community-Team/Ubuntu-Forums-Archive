---
title: "After switching video cards, Ubuntu only boots in recovery mode"
date: 2012-05-01
forum: General Help
---

### Post by Quatrix on 2012-05-01
Yesterday I swapped my NVIDIA card with a different NVIDIA card, but the new one seems to be faulty (screen artifacts on the Windows desktop).  After putting the old card back in, I'm only able to boot to the Ubuntu desktop in recovery mode.  It just hangs if I let it boot normally.  In recovery mode I get the full 1680x1050 resolution and everything seems to work perfectly.

I tried purging the NVIDIA packages and reinstalling nvidia-current, installing NVIDIA's own drivers, renaming xorg.conf, etc. without any luck.  How can I debug this and see exactly where it hangs?

---

### Post by zombifier25 on 2012-05-01
You should reinstall Linux's nvidia driver, Noveau:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch)

---

### Post by zero2xiii on 2012-05-01
Hay,

Have you tried just re-configing xorg?

```
sudo nvidia-xconfig
```

I have had a similar issue and this resolved my issue....

However it MIGHT not work as you noted you have renamed the xorg config file... Curious.

Good luck

---

### Post by Quatrix on 2012-05-01
> **zombifier25 said:**
> You should reinstall Linux's nvidia driver, Noveau:
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:__Need_to_fully_remove_-nvidia_and_reinstall_-nouveau_from_scratch)

Thanks, but those steps didn't help.  In fact, now it won't boot to the GUI in recovery mode either.  I can still press Ctrl+Alt+F1 to get to the shell prompt when it's hanging.

---

### Post by Quatrix on 2012-05-01
> **zero2xiii said:**
> Hay,

Have you tried just re-configing xorg?

```
sudo nvidia-xconfig
```

NVIDIA's driver setup already runs that as part of the process.  I confirmed that xorg.conf was updated (or created) afterward.  It still won't show me the desktop after rebooting.

---

### Post by Quatrix on 2012-05-01
Okay, I can boot to the GUI in recovery mode again after I replaced xorg.conf with a backup I had created in Windows (below).  I still can't boot normally, but this is better than nothing until I finish my C++ project that's due in a couple days (!) and then install 12.04 from scratch.  I'd still appreciate any further suggestions.  Thanks.

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by Quatrix on 2012-05-05
Well, I just installed 12.04 x64 from scratch, and it STILL won't boot normally.  It just sits on a black screen with the blinking cursor in the corner but again works fine in recovery mode.  Any thoughts?

---

### Post by Quatrix on 2012-05-05
Never mind, it works now.  From recovery mode I installed a bunch of updates (including kernel 3.2.0-24) and then used apt-get to install nvidia-current and booted successfully.  I assume that nvidia-current did the trick, though it's strange that it doesn't boot out of the box on a mainstream video card.

---

