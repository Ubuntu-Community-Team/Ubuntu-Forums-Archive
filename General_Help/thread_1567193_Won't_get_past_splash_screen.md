---
title: "Won't get past splash screen"
date: 2010-09-03
forum: General Help
---

### Post by theophiles on 2010-09-03
I just used the update manager to update to the latest kernel. There were other updates there, but I can't remember what all they were.

Now the computer won't get beyond the splash screen. I waited about 15 minutes the first time for it to load. When I hit esc during the splash screen, I got this warning 
```
GLib-WARNING **: getpwuid-r(): failed due to unknown user id (0
```
After that I think there is more, but my screen runs out of room, but I have this sense that there is more. 

Anyway, that might have nothing to do with the problem. When I boot to recovery mode it finds all the stuff plugged in to the motherboard and USB drives then just stops. 

Booting to the old kernel works just fine.

---

### Post by Pickanotherid on 2010-09-03
I just had the same problem. Got the "Security Update" window and clicked 'Update'. When it finished, it said Ubuntu needs to restart to install updates, so I hit the restart button. Things appeared to be booting okay until the splash screen came up and just sat there forever.

I'm new at this, how do you boot the old kernel??

---

### Post by theophiles on 2010-09-04
When you turn on your computer, put your hand above the "Esc" key because you have to move fast.

During the boot sequence there is a point where it says:
```
Grub loading, please wait ...
Press ESC to enter the menu
```

You have very little time so hit "Esc" immediately.

You will have a list of old kernels to which to boot. Under each kernel is its recovery mode. The most recent kernel is on top (the one that is not working for you and me). So, use the arrow keys to move down past the recovery mode to the next newest kernel.  

This will work until someone tells us how to fix this.

---

### Post by Rubi1200 on 2010-09-04
If an older kernel works, then you may have to stick with it until a fix is found for the issue you are having.

But some more information would also be helpful such as what graphics card do you have installed and which kernel version does not work?

---

### Post by coffeecat on 2010-09-04
> **theophiles said:**
> During the boot sequence there is a point where it says:
```
Grub loading, please wait ...
Press ESC to enter the menu
```

That's with legacy grub. If you're running 10.04 Lucid Lynx with legacy grub you must have upgraded from a pre-9.10 version or downgraded to legacy grub.

@Pickanotherid, if you are running Lucid Lynx and didn't upgrade from an earlier version you will have grub2. If you are not seeing the menu you must have a hidden menu and you need to intercept this with a key press the way theophiles described. The key for grub2 is SHIFT not esc. Sorry - I don't know what the screen prompt is. Just hold the shift key down as the POST finishes.

---

### Post by theophiles on 2010-09-05
My graphics card is a 128MB NVIDIA GeForce 8300GS.

The non-working kernel was the generic kernel which ended in 24, I'd need to restart to see the rest of the numbers. I am booting to the one that ends in 23.

---

### Post by coffeecat on 2010-09-05
> **theophiles said:**
> My graphics card is a 128MB NVIDIA GeForce 8300GS.

The non-working kernel was the generic kernel which ended in 24, I'd need to restart to see the rest of the numbers. I am booting to the one that ends in 23.

In Lucid that would be the 2.6.32-24 kernel which is what I am posting with at the moment, using a nvidia GeForce 8400GS.

Curious. Apart from Pickanotherid, I've not seen other members posting problems with the latest Lucid kernel, and it's clearly working for me with a related graphics chipset - although there could be other hardware reasons for a non-functional kernel. I wonder if one or more of the packages downloaded for the 2.6.32-24 kernel were corrupted during the download. Try opening Synaptic and marking everything installed with '2.6.32-24' in the package name for complete removal. You need complete removal to get rid of the downloaded and cached .deb files. Action that and then reinstall the kernel and see if it works second time around.

---

### Post by perspectoff on 2010-09-05
> **coffeecat said:**
> In Lucid that would be the 2.6.32-24 kernel which is what I am posting with at the moment, using a nvidia GeForce 8400GS.

Curious. Apart from Pickanotherid, I've not seen other members posting problems with the latest Lucid kernel, and it's clearly working for me with a related graphics chipset - although there could be other hardware reasons for a non-functional kernel. I wonder if one or more of the packages downloaded for the 2.6.32-24 kernel were corrupted during the download. Try opening Synaptic and marking everything installed with '2.6.32-24' in the package name for complete removal. You need complete removal to get rid of the downloaded and cached .deb files. Action that and then reinstall the kernel and see if it works second time around.

Yeah, the Plymouth splash screen manager is notoriously unreliable with nVidia graphics cards, even now. I have never figured out or heard of a reliable workaround.

---

### Post by coffeecat on 2010-09-05
> **perspectoff said:**
> Yeah, the Plymouth splash screen manager is notoriously unreliable with nVidia graphics cards, even now. I have never figured out or heard of a reliable workaround.

Agreed that you get an ugly Plymouth with the proprietary nvidia driver but would that cause the failure to complete bootup the OP is experiencing?

---

### Post by Muscovy on 2010-09-05
About once a week I get this error message since I reinstalled 10.04. Normally it hangs for a few seconds, but sometimes it halts and needs a reboot.

The problem started about 2 months ago, then it gave the error and froze every boot. I went in with a live disk, installed some daemon thing, ran it, then removed it. I'll look through Chromium/Bash history to see what it was.

---

### Post by theophiles on 2010-09-05
I tried the complete uninstallation and reinstallation of the kernel. It didn't change anything.

---

### Post by coffeecat on 2010-09-06
Sorry to hear that.

Your simplest option would be to use the previous working kernel until there is another kernel upgrade which, hopefully, won't be problematic. Sorry I can't be of more help.

---

### Post by theophiles on 2010-09-06
That is what I am doing and will continue to do unless another idea presents itself. Thank you.

---

### Post by sandyd on 2010-09-06
> **theophiles said:**
> I just used the update manager to update to the latest kernel. There were other updates there, but I can't remember what all they were.

Now the computer won't get beyond the splash screen. I waited about 15 minutes the first time for it to load. When I hit esc during the splash screen, I got this warning 
```
GLib-WARNING **: getpwuid-r(): failed due to unknown user id (0
```After that I think there is more, but my screen runs out of room, but I have this sense that there is more. 

Anyway, that might have nothing to do with the problem. When I boot to recovery mode it finds all the stuff plugged in to the motherboard and USB drives then just stops. 

Booting to the old kernel works just fine.
see
[http://ubuntuforums.org/showpost.php?p=9814699&postcount=6](http://ubuntuforums.org/showpost.php?p=9814699&postcount=6)

unfortunately, the error is ambiguous, so we have to narrow it down. However, we have to start somewhere....

---

