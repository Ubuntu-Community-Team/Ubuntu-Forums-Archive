---
title: "Replace Latest Kernel With 2.6.31"
date: 2010-08-04
forum: General Help
---

### Post by kernelles on 2010-08-04
I can't access my grub menu (by pressing space bar on boot) to select a kernel to boot from, and I need to boot into 2.6.31 to fix an intel chip issue. How can I replace the current 2.6.32x kernel with 2.6.31, so it is the ONLY option grub can boot up with?

---

### Post by ajgreeny on 2010-08-04
You need to press the shift key at boot if you are using grub2, or Esc if legacy grub.  Space bar will not do anything as far as I'm aware.

---

### Post by inameiname on 2010-08-04
sudo apt-get install startupmanager

It is an easy gui way to set at default whatever kernel you'd like to run that would boot at startup.

This is of course only if you can get into your operating system and install it.

---

### Post by kernelles on 2010-08-04
> **ajgreeny said:**
> You need to press the shift key at boot if you are using grub2, or Esc if legacy grub.  Space bar will not do anything as far as I'm aware.

LOL! I was pressing the wrong key. Thanks! However, the kernel I need is not there. How can I get 2.6.31 installed, so it shows up in the list of grub options?

---

### Post by dabl on 2010-08-04
> **kernelles said:**
> 

How can I replace the current 2.6.32x kernel with 2.6.31, so it is the ONLY option grub can boot up with?



You didn't say whether you can boot the 2.6.32 kernel at all.  If (using the Shift key and then booting "Recovery Mode", for example) you are able to boot the system, even if only to the command line, then you should be able to install the 2.6.31 kernel with apt-get.

```
sudo apt-get install linux-image-2.6.31-22-generic
```

If it's not in the Lucid repos, you can get it here and install with dpkg:  [http://packages.ubuntu.com/karmic/admin/](http://packages.ubuntu.com/karmic/admin/)

---

### Post by davidmohammed on 2010-08-04
before you downgrade - what type of intel graphics do you have?

run in the terminal

lspci | grep VGA

---

### Post by kernelles on 2010-08-04
> **dabl said:**
> You didn't say whether you can boot the 2.6.32 kernel at all.  If (using the Shift key and then booting "Recovery Mode", for example) you are able to boot the system, even if only to the command line, then you should be able to install the 2.6.31 kernel with apt-get.

```
sudo apt-get install linux-image-2.6.31-22-generic
```If it's not in the Lucid repos, you can get it here and install with dpkg:  [http://packages.ubuntu.com/karmic/admin/](http://packages.ubuntu.com/karmic/admin/)

Yes, I can boot the 2.6.32 kernel no problem, but it has issues with my intel chip, which causes X to crash, which is why I need 2.6.31, apparently.

Thanks so much for the help!

---

### Post by snowpine on 2010-08-04
> **kernelles said:**
> Yes, I can boot the 2.6.32 kernel no problem, but it has issues with my intel chip, which causes X to crash, which is why I need 2.6.31, apparently.

Have you tried disabling Compiz desktop effects? The version of Compiz in Ubuntu 10.04 doesn't have great Intel support. ;)

---

### Post by kernelles on 2010-08-04
> **davidmohammed said:**
> before you downgrade - what type of intel graphics do you have?

run in the terminal

lspci | grep VGA

Here is the output: 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

---

### Post by kernelles on 2010-08-04
> **snowpine said:**
> Have you tried disabling Compiz desktop effects? The version of Compiz in Ubuntu 10.04 doesn't have great Intel support. ;)

Yes, I have, so I'm hoping this kernel patch will fix the problem.

---

### Post by davidmohammed on 2010-08-04
the bug you are suffering from is described [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492") - the recommended workaround is in the description of that bug.

---

### Post by snowpine on 2010-08-04
> **kernelles said:**
> Yes, I have, so I'm hoping this kernel patch will fix the problem.

Too bad disabling desktop effects didn't solve the problem for you (it did the trick for me); however looking at your last post I see we have a different Intel chipset so I'm not sure what to say. :(

---

