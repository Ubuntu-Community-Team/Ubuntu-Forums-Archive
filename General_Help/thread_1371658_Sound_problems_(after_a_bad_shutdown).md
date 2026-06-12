---
title: "Sound problems (after a bad shutdown)"
date: 2010-01-03
forum: General Help
---

### Post by knottshawk on 2010-01-03
I was having trouble getting my 8.10 box to restart... it appeared hung on a line talking about alsa (I don't recall what it said). So, we powered off *gulp*... I started back up and the volume icon indicated it was muted. I unmuted and, lo and behold, I have no sound. So, I tried to follow the alsa upgrade instructions at [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24]("http://ubuntuforums.org/showpost.php?p=4298894&postcount=24")

When I tried to run the second script:
```
sudo sh ./alsa_2.sh

```
I got this:
> cp: target `/lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko' is not a directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory
cp: omitting directory `/lib/modules/2.6.24-16-generic/kernel/sound/'
cp: omitting directory `/lib/modules/2.6.27-14-generic/kernel/sound/'
cp: omitting directory `/lib/modules/2.6.27-15-generic/kernel/sound/'


And now my volume indicates it's muted again, and if I try to adjust it I get this error:

> 
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

So... what do I do to fix this mess?

---

### Post by knottshawk on 2010-01-03
Anyone?

---

### Post by danastasio on 2010-01-03
three hours is far too soon to bump a thread. Paitence :-)

though dont get me wrong, i know how distressing this can be (im running lucid. trust me on this one.)

do you have alsamixer installed on your system?

lets see if we can get that to work

```
sudo apt-get install alsamixer
```

also, check for alsa-utils and alsa-oss

```
sudo apt-get install alsa-oss alsa-utils
```

on the off chance that something got booted from your system.

---

### Post by knottshawk on 2010-01-04
Tried that... when I told it to install alsamixer it said 

> E: Couldn't find package alsamixer


The other packages installed fine but if I try to open my volume controls I get:> No volume control GStreamer plugins and/or devices found.

---

### Post by danastasio on 2010-01-05
then perhaps its installed by default?

try running

```
alsamixer
```

and if it works (you will know if it does) change the volume and mute settings, after run

```
sudo alsactl store
```

let me know if that works.

sorry for taking so long. I couldn't get at my computer yesterday

---

