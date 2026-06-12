---
title: "Blinking cursur after h/w upgrade"
date: 2010-04-19
forum: General Help
---

### Post by SushiBoiNL on 2010-04-19
Hi,

I have ubuntu installed and have been running it for a few months. Some parts of my PC started to not work properly so replaced the motherboard, cpu, video card and PSU.
Everything installed correctly and win 7 beta working fine, however when booting to Ubuntu (I dualboot) I get a black screen with blinking cursor. There is no problem with the hardware as it works fine under Win 7.

I think the problem is that I went from an Nvidia G6600GT graphics card to a ATI Radeon HD5770, as when trying to start xserver from tty1 I got an error message regarding the nvidia drivers, so I searched the forums and figured out how to remove the Nvidia drivers using the cli. However, this has not resolved the challenges. Would running sudo apt-get update resolve this challenge or do I need to do something else? I have a problem with sudo apt-get update which I also need to fix, which is why I haven't tried that yet. Not at home right now so will have to try the suggestions this evening.

Your help is much appreciated!

---

### Post by Bungler on 2010-04-19
So you used this to remove the dirver:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Have you tried the recovery mode selected in the Grub selection menu?

Or perhaps complety remove and re-install the X?

    ```
sudo apt-get remove --purge xserver-xorg
```

    ```
sudo apt-get install xserver-xorg
```

---

### Post by SushiBoiNL on 2010-04-19
Thanks for getting back to me!!!

> **Bungler said:**
> So you used this to remove the dirver:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

No I tried it now and it didn't seem to do anything. However I uninstalled the nvidia drivers by using the following:

```
dpkg -l | grep nvidia | grep ii
```to find out my version number, 185

and then used

```
sudo apt-get remove nvidia-settings nvidia-glx-185 nvidia-common nvidia-173-kernel-source
```. This uninstalled my Nvidia drivers. 

> Have you tried the recovery mode selected in the Grub selection menu?Yes, logged into NETROOT, but not sure what to do. Have done most of the work trying to fix it using normal tty1

> Or perhaps complety remove and re-install the X?

    ```
sudo apt-get remove --purge xserver-xorg
```    ```
sudo apt-get install xserver-xorg
```Tried this and now on boot up get a black screen with some blotches of colour.

Have tested a LIVE CD and Ubuntu works fine off the CD.

Any idea's?

---

### Post by dcstar on 2010-04-20
> **SushiBoiNL said:**
> 
.........
Have tested a LIVE CD and Ubuntu works fine off the CD.

Any idea's?

Ubuntu configures many things during the install process, replacing major hardware components requires a reinstall of Ubuntu so things can be configured correctly.

The Live CD is designed to auto-detect hardware, installed systems are not.

---

### Post by SushiBoiNL on 2010-04-20
> **dcstar said:**
> Ubuntu configures many things during the install process, replacing major hardware components requires a reinstall of Ubuntu so things can be configured correctly.

The Live CD is designed to auto-detect hardware, installed systems are not.

Well I would have liked to have to not reinstall but this did of course do the trick.

Cheers

---

