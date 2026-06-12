---
title: "Can't use/install/detect my Nvidia Graphic Card"
date: 2012-07-20
forum: General Help
---

### Post by p4nd4 on 2012-07-20
How do i install my Nvidia Graphic Driver? I mean, before installing Xubuntu, i had a Win XP that runned flawlessly, now if i open a game i just got a black screen... Worse,  i can't set a 1280x720 resolution from the Settings (max i got is 800x600).

System spec:

Toshiba Satellite 1410
256 mb Ram
20 HD Gb
Nvidia GeForce 4 420 Go graphic card
CPU Mobile Intel(R) Celeron(R) CPU 1.50GHz


I tried to install the Nvidia '96',173 and Current packs from the Synaptics app, received an error report, stating something is missing/interfering with the first two, while the "current" was installed, but didn't do any major change... in fact it's like nothing changed.

Any suggestion?

---

### Post by Nixarter on 2012-07-20
Since it is not Optimus, you shouldn't have much trouble.

If you just installed Ubuntu, wait a bit and you'll see a message for "Restricted Drivers" for your video device, and install that.  You can also go to your graphics settings and there should be the option there to install them.

---

### Post by triclops200 on 2012-07-20
EDIT: misread question. Install libgl1-mesa in apt-get.

---

### Post by p4nd4 on 2012-07-21
Thanks but the two tips didn't work

1) There are no such option where you said they would be, neither a "restricetd" message

2) Can't get the pack you suggested via terminal. Say it's impossible to find that pack.

---

### Post by haresear on 2012-07-21
I'm afraid the Nvidia drivers that support your card (nvidia-96) won't work with 12.04. Your only option for running 12.04 on Geforce 4 series is to use the open source driver (nouveau).

---

### Post by p4nd4 on 2012-07-21
> **haresear said:**
> I'm afraid the Nvidia drivers that support your card (nvidia-96) won't work with 12.04. Your only option for running 12.04 on Geforce 4 series is to use the open source driver (nouveau).

Can you please give me the dommand line or the exact name of the app? Thanks:D

---

### Post by haresear on 2012-07-21
The nouveau driver should be installed by default if the nvidia drivers are removed, but based on your description, I'm not sure what graphics drivers are currently in use. Could you issue the following command in a terminal window:
```
lsmod | grep -e nouveau -e nvidia
```

Also you could launch synaptic and search for "xserver-xorg-video-nouveau" which is the open-source driver. I would expect it to be already installed. I would suggest also searching for "nvidia" to see if anything with nvidia in the package name is installed.

---

