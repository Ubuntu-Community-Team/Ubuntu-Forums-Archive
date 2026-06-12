---
title: "nVidia Crashing Maybe Fixed YMMV"
date: 2010-05-12
forum: General Help
---

### Post by ephman on 2010-05-12
hey,

ok i've been dealing with this totally awful nVidia video card crashing my system for the past couple releases.  it's been a major issue for a lot of other people.  you can read some of the posts i've made.  some of things that have temporarily fixed my issue.  etc...  but i think with the new release 10.04, and the new nVidia driver 195.36.24 i've finally got it working.  so when i originally installed it kicked up this error:


> ERROR: Unable to load the kernel module ‘nvidia.ko’.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

so i searched around and find this way to fix that error.

[http://ubuntuforums.org/showpost.php?p=9211609&postcount=35](http://ubuntuforums.org/showpost.php?p=9211609&postcount=35) 

as a way to fix that error.  and guess what?  been running for 2 days so far straight, no crashes.  i've run the card through it's paces.  lot's of videos (mainly from my blog @ [http://www.ephman.com](http://www.ephman.com) ) running some 3d games, and pushing compiz to the max.

this is my setup:

Ubuntu 10.04
Asus M70VN
Intel Duo T9400 2.5GHz
3.9 gig Ram
nVidia GeForce 9640m GT 1GB

and just if you missed that link up there i'll quote the fix so far:

> sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX=' and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop


good luck if you've been having this awful nVidia crashing problem and this works for you.  And if you love a great tech support story that in a way has to do with this problem you'll love to read the [reason that ASUS SUCKS!!! ]("http://www.ephman.com/article/official-asus-notebook-computer-review")

good luck,

ephman

---

