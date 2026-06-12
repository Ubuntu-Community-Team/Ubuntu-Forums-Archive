---
title: "[HOWTO]Ubuntu on 2Gb memory stick"
date: 2010-06-28
forum: General Help
---

### Post by Orlando84 on 2010-06-28
Hi all!
At last my HDD on my home laptop crashed at all - no booting from it, not even present on separate desktop like partitions (only some noise).
So before buying a new HDD I decided to install Ubuntu (9.10 Karmic) on my 2Gb memory stick. Here I'll try to share my experience with installation.

Step 1. As my notebook don't like standard console, it needs to set VGA=755 at boot, I hadn't found how to set this option, I decided to set up with Braille console. I booted from DVD, pressed F5 and then selected Braille terminal (For those who have troubles with ACPI have to press F6 and there to select noacpi=on) and then selected Installation in text mode.
Step 2. I booted with inserted memory stick, will jump here to partitioning step omitting all others because they were usual. So I created 1st partition with size 1.8Gb and mount point to /, and 2nd as swap with size 200Mb
Step 3. Very important! When I was propted what packages I'd like to install, I deselected each of them including LAMP server, Ubuntu desktop etc. And after that installation about 150 of packages started.
Step 4. When done GRUB auto installed into MBR of memory stick and I rebooted to my new Ubuntu OS from memory stick.

First of all I needed some X11 environment to be installed in system, I decided to have Openbox as window manager
```
sudo -s
apt-get install xserver-xorg xinit xserver-xorg-core openbox

```
When installation completed I prompted 
```
startx -configure
```
And got a new file called xorg.conf.new in home directory, then I decided to add modeline (mode for monitor)
```
gtf 1280 900 60
``` where first number is X resolution (Horizontal), second is Y resolution, and refresh rate. And copypasted that generated line to xorg.conf.new.
```

cp ~/xorg.conf.new /etc/X11/xorg.conf

```
And then everything started to work I could use startx.
Final Step. You can find here [http://ubuntuforums.org/showthread.php?t=549884](http://ubuntuforums.org/showthread.php?t=549884) how to set up pretty environment in Openbox, there some files (for menu and for autostart) that might be fixed, because they have some "black" spaces. If someone needs them I will guide you through the rest of process.
Good Luck):P

---

