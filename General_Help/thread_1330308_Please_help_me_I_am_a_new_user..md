---
title: "Please help me I am a new user."
date: 2009-11-18
forum: General Help
---

### Post by ibrahim.k on 2009-11-18
Hi,

Guys I have just installed ubuntu 9.4 on my laptop (HP- dv6 1045)

But I cant hear sounds please help me out with this 

I have tried to update the current version but it didn't work.
Also I have tried to install codex to run mp3 files i can see the equalizer moving but still no sound. 

Thanks,

---

### Post by 73ckn797 on 2009-11-18
Click on the speaker icon at top left panel and see if volume is turned down.

---

### Post by drs305 on 2009-11-18
I don't know if you have previous experience with Ubuntu, but here are a couple of first steps.

Double-click the speaker symbol on the upper panel. Are the volumes up - especially Master and PCM?

You can also set the default volume by opening a terminal (Applications, Accessories, Terminal) and typing:
```
alsamixer
```

You can also get to the Sound panel via System, Preferences, Sound: Devices tab. Try clicking on the "Test" button. If you don't hear anything, try changing the Sound playback setting from Autodetect to one of the other options and see if "Test" produces any sounds with a more specific option.

---

### Post by P4man on 2009-11-18
Starting a new topic wont change the fact that you are likely bitten by [the bug I linked to in your first thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870"). If installing backports didnt work try this as explained in the bug report: Open a terminal (applications > accessoiries > terminal) and copy paste the following lines:

```
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_data 1
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_dir 1
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_mask 1
```

If that makes the sound work, then you are a victim of that same bug.

---

### Post by ibrahim.k on 2009-11-18
> **P4man said:**
> Starting a new topic wont change the fact that you are likely bitten by [the bug I linked to in your first thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363870"). If installing backports didnt work try this as explained in the bug report: Open a terminal (applications > accessoiries > terminal) and copy paste the following lines:

```
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_data 1
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_dir 1
sudo ./hda-verb /dev/snd/hwC0D0 0x1 set_gpio_mask 1
```If that makes the sound work, then you are a victim of that same bug.


Thanks every body non of this worked actually,

P4man I am so desperate also trying this didn't work

---

### Post by ibrahim.k on 2009-11-18
p4man thank you for everything .
Is there anything that i can do to fix that bug ??

---

### Post by P4man on 2009-11-18
if the above commands didnt help, then im not sure. Is it possible to download the latest version (9.10) and test it from the cd?

---

