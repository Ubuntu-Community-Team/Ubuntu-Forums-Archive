---
title: "No 3D acceleration for GTX 560 Ti?"
date: 2012-07-19
forum: General Help
---

### Post by Rsjc741 on 2012-07-19
So i've installed the driver now, twice. Both occasions were because Xserver felt like breaking.

So even though I've installed the driver (which looks WAY too encompassing to do any good) and have tried to set up nvidia's xserver, it keeps on telling me my graphics card is unknown.

This wouldn't be a problem except for the fact that Virtualbox refuses to enable 3D acceleration without a discovered and fully working card.

So has anyone got a Nvidia GTX 560 Ti to work fully?

Mine is the PNY XLR8 version.

---

### Post by Rsjc741 on 2012-07-20
bump

---

### Post by triclops200 on 2012-07-20
Try installing libgl1-mesa and libgl1-mesa-glx
If both of those don't work, try xlibmesa-gl and xlibmesa-glu

---

### Post by 3Miro on 2012-07-20
Could you describe your problem in more details?

- is Ubuntu installed stand-alone or dial-boot or is it inside of a Virtual Box.

- how are you installing the driver, there should be a check-box in Additional Drivers, that's hardly encompassing.

---

### Post by Rsjc741 on 2012-07-20
Sorry guys, I keep it short in the beginning so people don't tl;dr it from the start.

I'm running 12.04 as host OS

Installed on the fail-safe console (essentially what ALT+CTRL+F1 looks like) by sh'ing the official release Nvidia.run file.


I've tried a couple of things though...

I downloaded the Beta to see if the known 3D acceleration disabled bug was gone. Couldn't stop xserver, so I looked for a ppa for an install file.

Found one, ran it (it's called nvidia-current), upgraded, back to the console mentioned above.

This time I installed version 3.0.5b.

Still console'd me.

Then I did apt-get remove nvidia-current

restarted, and then my screen was back to normal.


BUT

My other monitor was working (it wasn't before all of this)

I just went to prop drivers and activated the post-release updates.

System Settings still reports my graphics card as "Unknown" with a standard experience.

---

### Post by 3Miro on 2012-07-20
The correct way to install the Nvidia driver is via Additional Drivers or via Synaptic/Ubuntu Software Center installing nvidia-common, nvidia-current and nvidia-settins.

The correct way to see if the driver has been installed is the nvidia-settings. Other tools may not be able to read the proprietary driver.

Uninstall any drivers that you may have downloaded from Nvidia and install nvidia-current. Then check with Nvidia-Settings, if it shows the right driver, then you are good to go.

If not, post back and post the output of the following 3 commands:
```
cat /etc/X11/xorg.conf
sudo modprobe | grep nvidia
sudo lspci | grep VGA
```
This will tell us about the configuration of the Xorg server, the nvidia kernel module and the video card detected on your system.

---

### Post by CatKiller on 2012-07-21
> **Rsjc741 said:**
> 
So has anyone got a Nvidia GTX 560 Ti to work fully?


It's never not worked. Ubuntu & Kubuntu, just installed through Additional Drivers and restart. No muss, no fuss.

I suspect you've made a rod for your own back by messing about with other methods.

---

