---
title: "Change back to default Plymouth Theme"
date: 2010-05-19
forum: General Help
---

### Post by LanternInc on 2010-05-19
I remove nouveau to install the nvidia 195.xxx driver. When I boot back, the plymouth was the ubuntu 10.04 theme. How do I change it back to xubuntu 10.04?

---

### Post by philinux on 2010-05-19
```
sudo plymouth-set-default-theme --list
```To see the list of themes

```
sudo plymouth-set-default-theme **[COLOR="Red"]themename[/COLOR]** --rebuild-initrd

```


Reboot.

---

### Post by LanternInc on 2010-05-19
> sudo plymouth-set-default-theme --list> sudo plymouth-set-default-theme **[COLOR=Red]themename[/COLOR]** --rebuild-initrd^^ I get 'command not found'. I checked synaptic and I do have plymouth and the xubuntu theme installed.

Please help.

---

### Post by philinux on 2010-05-19
Gahhh,

They changed it in late March I think.

sudo update-alternatives --config default.plymouth

---

### Post by LanternInc on 2010-05-19
> **philinux said:**
> Gahhh,

They changed it in late March I think.

sudo update-alternatives --config default.plymouth



I got rid of the Ubuntu theme through synaptic, and installed the spinfinity theme. Its partially working.  I got a black screen and a progress bar at the bottom.


Thanks,

---

### Post by philinux on 2010-05-19
That sounds like plymouths fall back to an ascii progress bar. Is it blue and white blocky graphics along the bottom.

Did you run the above command?

---

### Post by LanternInc on 2010-05-19
Yes. I did run the command. I guess when I removed nouveau, the ubuntu theme went default. I couldn't change it until I removed all the themes except one. 

I tried them all, and all I got was a black screen and (Yes)a blocky blue and white progress bar. Its better than the low res ubuntu theme.

Any other suggestions?

---

### Post by philinux on 2010-05-19
As far as I remember plymouth needs a graphics driver to work so you must have replaced nouveau with something.

---

### Post by LanternInc on 2010-05-19
It seems that plymouth is not yet working properly with nvidia 195.xx.

---

### Post by philinux on 2010-05-19
It works here, 8600gt, but in a lower resolution.

I get a black screen for about 10 seconds then 3 seconds of pink plymouth.

---

### Post by LanternInc on 2010-05-19
I have a 9600gt. Yes. It works with the nvidia 185 via Hardware Drivers with low res in xubuntu plymouth. But when I installed 195.xx, I got an nvidia.ko module error. Black listing nouveau didn't work and I have to remove it.

> I get a black screen for about 10 seconds then 3 seconds of pink  plymouth.I got this after I installed nvidia 195. I'm using xubuntu and yet a ubuntu screen was flashing at boot, I didn't like it.

I'm better off with a black screen and a progress bar for now.

---

