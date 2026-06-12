---
title: "gpointing-device-settings Segmentation Fault"
date: 2010-11-15
forum: General Help
---

### Post by tedrogers on 2010-11-15
Hi all,

For no reason I'm aware of, I was experimenting with gpointing-device-settings and trying to get it to remember my settings for disabling the touchpad on my Lenovo T500, which it won't do.

Anyway, after uninstalling and reinstalling gpointing-device-settings I now get a Segmentation Fault when running under sudo.

It won't run at all without sudo or even with gksudo.

Any ideas?

Thanks.

---

### Post by galvatron408 on 2010-11-30
I'm running ubuntu 10.10 and this thing only works the first time after it is installed. On subsequent launches, it just segfaults. I have not found any useful workaround.

---

### Post by tengisu on 2010-12-12
same here, it worked right after i installed it but segfaulted on reboot.

---

### Post by mennowo on 2010-12-12
Here, this never worked... Just segmentation fault right off the start...

Ubuntu 10.10, 64 bit. Using Wacom BambooFun 6x8 tablet.

---

### Post by Lutin on 2010-12-27
A later version (1.5.1-3) of gpointing-device-seetings can be downloaded from [here]("http://packages.debian.org/squeeze/i386/gpointing-device-settings/download") - it might help you out. However, it still doesn't disable tapping even when the box is checked for this.

But at least it doesn't give a Segmentation Error anymore..........

---

### Post by sandgren on 2010-12-29
> **Lutin said:**
> A later version (1.5.1-3) of gpointing-device-seetings can be downloaded from [here]("http://packages.debian.org/squeeze/i386/gpointing-device-settings/download") - it might help you out. However, it still doesn't disable tapping even when the box is checked for this.

But at least it doesn't give a Segmentation Error anymore..........

Thanks Lutin, It works perfectly.

---

### Post by arty.net on 2011-04-27
it is good for me....it disable tapping without any problem....

---

