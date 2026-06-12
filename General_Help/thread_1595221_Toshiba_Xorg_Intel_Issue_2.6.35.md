---
title: "Toshiba Xorg Intel Issue 2.6.35"
date: 2010-10-13
forum: General Help
---

### Post by kd5vdo on 2010-10-13
Howdy,

I've been searching these forums and the rest of the Internet for over a week now and have found no one else experiencing this problem.  I have a Toshiba T235-S1350, and upon upgrading the kernel to 2.6.35, Xorg will not load.  I have tried i915.modeset=1, and countless other remedies.  I'm not a complete fool in Linux, but I'm nowhere near being an expert either.  I've never really had any major issues before, so I don't know what logs to post.

If I try to install 10.10 from a USB drive, the installer works, KMS works, but the desktop will not load.  Once I install, I do not even get KMS.  If I downgrade to 2.6.34, I get the splash screen on shut down, but not on boot.  I'm at a loss as to what's happening here and appreciate any help.

Also, it doesn't matter whether I run a 64 or 32 bit install.

Thanks!

---

### Post by ednerd on 2010-10-14
Same laptop, same problem.  Any ideas out there?

---

### Post by cgoldberg on 2010-10-14
also having the same prob with my Toshiba T-235 and Maverick 10.10.

Ubuntu 10.04 install works fine on it.  Ubuntu 10.10 installs fine but can't load X on boot after install.

---

### Post by dino99 on 2010-10-14
got issue with this kernel too, so i've installed 2.6.36 from this ppa:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

only install the kernel packages, then desactivate this ppa into synaptic repo tab, and update again to clean the cache.

---

### Post by kd5vdo on 2010-10-14
Hey, thanks for the reply, I just tried that and this time didn't even get power to the screen.  Backlight won't even come on after grub.  If I boot into recovery mode, it gets up to where it asks what you want to do, but the screen dies before you even see the menu.  Just as a note, sometimes, when running 2.6.35, when I shut down from the terminal, the screen will flash for an instant with either my desktop, or an Intel logo.  It seems X is running somewhere, somehow.

---

### Post by cgoldberg on 2010-10-15
please update this thread if you come up with a solution.  (i'll do the same if I get my T-235 working)

-Corey

---

### Post by kd5vdo on 2010-10-18
Hey ya'll, I seem to have fixed this issue.  I did a couple of things, and I'm not sure if they all work together, or if one of them was the trigger, but I did them in this order, and it fixed it:

1) I really doubt this one was related at all, but require a password to log in, so you see GDM before Gnome loads
2) Add i915.modeset=1 as a kernel boot parameter
3) Explicitly enable KMS very early in boot with the commands from [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

 namely:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u

4) Install the packages for 2.6.35
5) Reboot and enjoy!

If anyone has any insights as to why or how this works, I'm interested just for learning.  My guess is step 3 was the kicker, and for some reason KMS wasn't properly functioning without it.  From what I hear, X won't work without KMS anymore.

Thanks, all!

-Noah

---

### Post by kd5vdo on 2010-10-18
BTW, now the audio is not working with this new kernel.  I'm working on this.  I know very little about ALSA and pulse, so I doubt I'll get this fixed any time soon.  The plus is powertop shows MUCH lower usage with this kernel.  Down from about 13-15W to 9-12W.

---

