---
title: "Xorg hogging resourses"
date: 2011-09-02
forum: General Help
---

### Post by dhkillian on 2011-09-02
HI
Just installed Kubuntu, I have been using Un=buntu fo rthe past year or so and wanted to see what KDE was like.

I'm trying to understand why Xorg is constantly using so much CPU and memory. My machine is running sooooo slooooow. 
Be grateful for any suggestions

---

### Post by realzippy on 2011-09-02
Suggest you give more infos.
How much RAM & CPU used?
Tasks running?
Machine specs ?
Which kubuntu version?
Kwin or compiz ?
Which kernel?

---

### Post by dhkillian on 2011-09-03
Reloaded nvidia graphics driver, turned off machine and left for the night. Booted up today, seems to be running ok. In TOP, I see XORG running 4.3% of mem (2gb) and 2 -6% of CPU (Dual Core 2 ghz). I don't see XORG when I look in system monitor, wonder why.

Apps running are Chrome and Thunderbird


Running Kubuntu 11, where do I find kernal info?

Regards

---

### Post by realzippy on 2011-09-03
4.3 % of 2Gb isn't much,is it?
Kernel:

```
uname -a
```

---

### Post by dhkillian on 2011-09-03
2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by occams_beard on 2011-09-03
If you have effects enabled, turn off the 'blur' effect in the kwin effects. I tried using kubuntu a few months ago and had similar issues with it. (also using nvidia).

I never did track down what was causing the insane memory usage of xorg though, but after a couple days it would always use > 1 GB of memory which is ridiculous.  I just gave up on KDE, it's always been way too buggy for my taste.

---

