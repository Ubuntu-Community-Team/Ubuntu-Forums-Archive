---
title: "How does chromium load so fast?"
date: 2012-03-19
forum: General Help
---

### Post by Pacopag on 2012-03-19
Hi.  I've found that Lubuntu fires up Chromium (first time after reboot) on my crappy netbook way faster than Arch fires up Chromium on an i7 desktop.

What gives? Does anyone know if there is some kind of preloading going on at startup in Lubuntu?

---

### Post by TeoBigusGeekus on 2012-03-19
> **Pacopag said:**
> Hi.  I've found that Lubuntu fires up Chromium (first time after reboot) on my crappy netbook way faster than Arch fires up Chromium on an i7 desktop.

What gives? Does anyone know if there is some kind of preloading going on at startup in Lubuntu?

Which desktop environment are you using in Arch?
If it's kde or gnome3 it is to be expected.

---

### Post by Pacopag on 2012-03-19
I'm using xfce in arch.  But it's definitely more than just DE or WM.  I also tried AntiX with icewm on the same netbook, and Chromium also starts up significantly slower than in Lubuntu.

---

### Post by TeoBigusGeekus on 2012-03-19
Are the installations of chromium identical?
Same extensions, settings etc.?

---

### Post by Pacopag on 2012-03-19
I'm not sure.  Lubuntu comes with Chromium out of the box.  I installed Chromium on arch from the standard arch repos.

---

### Post by idoitprone on 2012-03-19
> **Pacopag said:**
> I'm not sure.  Lubuntu comes with Chromium out of the box.  I installed Chromium on arch from the standard arch repos.

Well there is alot of reasons why
I have to say that I used arch and those dev dont really do much other that make sure packages work, compile, and feed through pacman.

After installing arch linux a couple of times on my harddrive, I learned that positition on the harddrive will really affect boot time and opening programs. As core packages are farer from the edge, some times it hangs a few extra milliseconds. Also you update alot, since bit an pieces are all over the hdd

Next, XFCE is more bloated than gnome 2. Sometimes gnome 2 starts apps faster than xfce which therefore mean xfce is more bloated than lxde

Lastly, chromium is getting more and more bloated with each release. Lately, google been adding features without regard for speed regression. These days chromium is taking more and more ram which may bottleneck ur i7 installation, since your running arch, then it prob the most bloated to date; the latest version. Since ubuntu freezes chromium, i believe, you are running a slimmer version to loads into ram faster.

Well these are 3 reasons, I thought up

---

### Post by Pacopag on 2012-03-19
Good stuff idiotprone.  Would 64 vs 32 bit installs have an effect too?  64 bit arch and 32 bit lubuntu.

---

### Post by uRock on 2012-03-19
> **Pacopag said:**
> I'm not sure.  Lubuntu comes with Chromium out of the box.  I installed Chromium on arch from the standard arch repos.

Lubuntu comes with Chromium as its default browser.

---

