---
title: "how do i change the plymouth theme in 10.04?"
date: 2010-05-11
forum: General Help
---

### Post by Blake. on 2010-05-11
just what the title says. i installed a theme from synaptic, but it has no effect. for those of you who don't know, plymouth is the program that shows the boot screen.

---

### Post by lord-zk on 2010-05-13
[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13](http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13)

---

### Post by 98cwitr on 2010-05-13
i just went to the download center and typed in plymouth and installed the theme I wanted.

---

### Post by vikramsngh on 2010-05-22
After installing from Synaptic. Enter in the terminal:

sudo update-alternatives --config default.plymouth

A list will appear from which you can choose your theme.

After that enter in terminal:

sudo update-initramfs -u
Restart your comp and the theme should have changed.

---

