---
title: "nvidia problems"
date: 2010-06-01
forum: General Help
---

### Post by sgage on 2010-06-01
Hello All,

I decided to revert to the nouveau drivers after using the nvidia drivers for a month now. I used jockey to remove the nvidia drivers, rebooted, and ... nothing. A few seconds of disk activity, the monitor light comes on, then black screen and silence.

I figured I'd boot into repair-mode and easily fix it, but no-go. Black screen. What's up with that?

Anyway, can someone explain to me how I might be able to recover my video with the LiveCD? I really do not want to re-install the whole thing - I had it tuned to perfection.

TIA!

---

### Post by dino99 on 2010-06-01
try to boot in recovery mode or add video=vesa on the boot line (edit grub with "e" then boot wit "x")

---

### Post by sgage on 2010-06-01
I already tried recovery mode (no go), and adding video=vesa didn't work either.

Any other ideas?

---

### Post by dino99 on 2010-06-01
i cant help you more if you does not describe your hardware and which release is in use.

---

### Post by sgage on 2010-06-01
nvidia GeForce 8500 GT is my graphics card, and I'm running Lucid Lynx, regular Ubuntu, updated as of yesterday.

---

### Post by dino99 on 2010-06-01
i've the same card and its working fine with the packages into synaptic: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

check that the driver is activated: system admin hardware driver (nvidia-current)

you might want the latest release: add this ppa into synaptic repo

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

so boot with "nouveau", goto synaptic and remove/purge ALL the nvidia packages installed, then install the ones (4) above and remove xorg.conf if it exist:

sudo rm -f /etc/X11/xorg.conf

then reboot

---

### Post by sgage on 2010-06-01
I think I haven't made my problem clear:

I can't boot at all, neither "normally" or recovery mode - all I get is a black screen.

My nvidia graphics were working fine with the nvidia driver packages from ubuntu repos. I thought I would revert to nouveau to test, and I used "hardware drivers" to remove nvidia. It seems that in the past, simply doing that would result in reversion to the open-source driver.

When I rebooted, black screens.

So I can't do anything from my installation - I am hoping there is some way to get this fixed via the LiveCD.

---

### Post by dino99 on 2010-06-01
an example of how to chroot :

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by sgage on 2010-06-01
Thanks Dino,

I figured it out - I had used Startup Manager to tweak the boot splash to look better with the nvidia drivers. 

I had to chroot, edit /etc/initramfs-tools/modules to remove the added line, and run update-initramfs -u. Then I could boot to nouveau just fine, and ran hardware drivers to reinstall nvidia drivers.

All is well now - I knew it was possible!

Anyway, I am glad to be back with nvidia. I can't use nouveau, because suspend/resume won't work. Also, Stellarium runs unacceptably under nouveau.

Thanks again for helping...

---

### Post by dino99 on 2010-06-01
hey you're a funny guy, you hide me all your weird tweaks :P

---

### Post by sgage on 2010-06-01
Not hiding, forgetting :KS

---

