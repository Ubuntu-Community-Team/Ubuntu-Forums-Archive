---
title: "Boot Fails After Upgrading to Natty"
date: 2011-05-02
forum: General Help
---

### Post by krishnandu.sarkar on 2011-05-02
Hi, I was using Maverick, I performed upgrade to Natty today morning and rebooted and it was working fine. Then I turned off my PC and left home.

Now in the evening when I'm trying to boot nothing happens, just black screen. Nothing happens after that.

Though I can boot by selecting "Previous Version" but can't boot normally. Though I was surprised that even after selecting "previous version" I was booted in to Natty(I guess so, as the UI is Unity not GNOME).

But can't boot using the Kernel that's listed first in my Menu.

Please help.

---

### Post by krishnandu.sarkar on 2011-05-03
Guys, please reply, any idea??

---

### Post by jacqueshappy on 2011-05-03
Hi,
Can't help you I'm afraid but I'm having similar problems.
Mine won't work at all though.
Thought you would like to know there's others in the same boat!
Any ideas what's up with mine? Check my post

---

### Post by krishnandu.sarkar on 2011-05-03
Yup there are many threads regarding this.

Hope they fix the problem soon with updates.

---

### Post by krishnandu.sarkar on 2011-05-03
> **jacqueshappy said:**
> Hi,
Can't help you I'm afraid but I'm having similar problems.
Mine won't work at all though.
Thought you would like to know there's others in the same boat!
Any ideas what's up with mine? Check my post

BTW the peoples who are having this problem, I've seen almost all of them are able to boot using Previous Version kernel, so you can try that.

If that doesn't also works for you, I'm too noob to help you out. :(

---

### Post by krishnandu.sarkar on 2011-05-05
Ok guys, after reading many posts on Black Screen problem I tried..

1. Adding nomodset to boot option, didn't worked. BTW It was already thee.
2. Removing NVIDIA Drivers, sudo apt-get remove --purge nvidia*. Still no result.
3. Installing NVIDIA Drivers again, sudo apt-get install nvidia-current, sudo nvidia-xconfig. Still didn't worked.
4. Installing kernel image and headers again, sudo apt-get install --reinstall linux-headers-<latest kernel grabbed from uname -a> and sudo apt-get install --reinstall linux-image-<latest kernel grabbed from uname -a>. Still no result.

So what's the problem guys?? Please help. I don't want to perform a clean installation, all my programs and datas will be lost. Why does ubuntu always breaks while upgrading??

BTW at last I tried removing the kernel parameteres and boot only with ro, vga=775 and nomodset and got the text booting, and it says something vbox loading failed.

My PC Configuration is as follows:
Intel Pentium D @ 3.0Ghz
Intel DG945GCCR Motherboard
1x1GB DDR2 RAM and 1x2GB DDR2 RAM (Total 3GB RAM)
XFX NVIDIA 9500GT 1GB DDR2

---

