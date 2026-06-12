---
title: "terminal error"
date: 2011-12-16
forum: General Help
---

### Post by mmtmm on 2011-12-16
I just installed lubuntu 11.10. In the terminal on other linux versions, i can type "eject cdrom" to open the drive and "eject -t cdrom" to close the drive. But it doesn't work on lubuntu 11.10. It worked fine when I had lubuntu 11.04 on this computer.

The terminal error says "unable to find or open device for: cdrom"

Anybody know what is wrong?

---

### Post by scorchgeek on 2011-12-16
Does
```
$ ls /dev | grep cdrom
```
give any results? If not, the problem is that you don't have a symbolic link to the cdrom drive in /dev. (According to *man eject*, the argument to eject is simply the device name that you want to dismount.)

You could get around the problem by finding the other device file that corresponds to your cdrom drive (on my system it's scd0) or by creating a link.

---

### Post by mmtmm on 2011-12-16
> **scorchgeek said:**
> Does
```
$ ls /dev | grep cdrom
```
give any results?
Nope,no results.

> You could get around the problem by finding the other device file that corresponds to your cdrom drive (on my system it's scd0) or by creating a link.
No clue how to do this. It's listed on disk utility as /dev/sr0.

---

### Post by scorchgeek on 2011-12-17
> **mmtmm said:**
> 
No clue how to do this. It's listed on disk utility as /dev/sr0.

I'll have to admit to not knowing exactly how myself. I know how to create a symbolic link (ln -s command), but I'm not entirely sure that'd work as expected on a device.

But you should just be able to run ```
eject sr0
``` and have it work.

If you don't want to have to remember the device name, you can make eject always use sr0 with a bash alias. This way you can just type "eject" and your cdrom will open. 

You can add the alias in a pinch with
```
$ echo "alias eject='eject /dev/sr0'" >> ~/.bashrc
```

(Alternatively, you could replace the first "eject" with "ejectcd" or any other command alias you want to use.)

---

### Post by mmtmm on 2011-12-17
eject sr0 and eject -t sr0 work PERFECTLY!

Thanks scorchgeek! :)

---

### Post by scorchgeek on 2011-12-17
Please mark this thread as solved from the "thread tools" link at the top of the page if you have no more questions.

---

### Post by mmtmm on 2011-12-17
> **scorchgeek said:**
> Please mark this thread as solved from the "thread tools" link at the top of the page if you have no more questions.

Got it. 

I have more Qs, but not for this problem...anymore.

---

