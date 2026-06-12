---
title: "No desktop effect/compiz - Nvidia GTX 560 Ti - Ubuntu 10.10"
date: 2012-02-24
forum: General Help
---

### Post by KilledXDestiny on 2012-02-24
Hi all,

I recently updated my PC, included in said upgrade was a Gigabyte Nvidia GTX 560 Ti video card, unfortunately I now find myself unable to turn on even basic level desktop effects let alone start compiz.

When I first booted after upgrading I found myself at CLI and unable to startx due to problems with the nvidia drivers, I ended up downloading and installing the driver from nvidia's site and am booting into the desktop at full resolution but am unable to turn on any level of effects. Normally I have been able to fix this by activating drivers from the "Additional Drivers" screen but there were none listed at this time. 

After a bit of poking around I ended up trying to use x-swat ppa, after updating a driver option came up in "Additional Drivers" which I activated but desktop effects still wont work.

Sorry for the long winded post but I've pretty much been stabbing in the dark on this one, any help would be greatly appreciated.

This is on 10.10 but I am willing to upgrade if it will help and there is a way to be relatively sure I wont have a host of new issues, the reason I haven't upgraded yet is because last time I tried (when 11.04 launched) my system basically stopped working and I ended up doing a fresh install.

Anyway thanks in advance again for any help you can provide.

---

### Post by wildmanne39 on 2012-02-24
Hi, if you installed from the nvidia site and additional drivers then you have more then one driver being used and they are conflicting.

Open synaptic and see which nvidia drivers are installed, and not all will show up in additional drivers even though they are being used.
Thanks

---

### Post by KilledXDestiny on 2012-02-24
Thanks for replying.

Sorry to a pain but I don't have much experience with Synaptic, could you please point me in the right direction once I have it open?

Thanks again.

---

### Post by wildmanne39 on 2012-02-24
Hi, just type nvidia into the search window and see which drivers are installed, or you can use software center but synaptic is more powerful.
Thanks

---

### Post by KilledXDestiny on 2012-02-24
Ok so under installed nvidia I get the following packages.

nvidia-current
nvidia-settings
nvidia-current-modaliases
nvidia-173-modaliases
nvidia-96-modaliases

and I assume these are relevant too?

xserver-xorg-video-nouveau
xserver-xorg-video-nv

A few other bits and pieces are listed by the search too will add them if you need.

---

### Post by wildmanne39 on 2012-02-24
Hi, which ones have green squares by them? you should just post a screenshot of it and post the output of:
```
lspci | grep VGA

```
Thanks

---

### Post by KilledXDestiny on 2012-02-24
Sorry I should have been clearer there, those are all installed packages.

lspci | grep VGA Provides
> 01:00.0 VGA compatible controller: nVidia Corporation Device 1200 (rev a1)


No screenshot sorry, seems the internet doesn't want to upload one -_-"

---

### Post by wildmanne39 on 2012-02-26
Hi, please try this:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```
then reboot
Thanks

---

### Post by KilledXDestiny on 2012-02-26
No luck unfortunately I'm not able to get even "normal" desktop effects to work. Attempting to enable them searches for additional drivers and them simply gives "Desktop effects could not be enabled"

---

### Post by pqwoerituytrueiwoq on 2012-02-26
after you run the last command wildmanne39 gave you you will need to logout and back in which will restart the X server

you may want to add nomodeset to your kernel's boot line (google nomodeset grub)

if you have issues post the output of this command
cat /etc/X11/xorg.conf

---

