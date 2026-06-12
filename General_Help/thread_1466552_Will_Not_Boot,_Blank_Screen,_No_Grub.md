---
title: "Will Not Boot, Blank Screen, No Grub"
date: 2010-04-30
forum: General Help
---

### Post by TreyKerux on 2010-04-30
I have multiple HDDs in my box, one of which being a Win7 install. After installing 64bit version on to my old 9.10 drive (full wipe of drive) and it says everything went well. Afterward though when I rebooted it just hangs at a blank screen. I thought maybe it just didnt load the boot images so I let it sit for up to 40 minutes and realized it should have at least given me an option of which OS to load by now.

After reading a little on the forums, I booted in my live-cd and tried "sudo update-grub" which gave me the following error 
> /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Any suggestions?

---

### Post by dino99 on 2010-04-30
if you can open a terminal (alt+f2):
sudo grub-mkconfig && update-grub

hope you have installed grub2 onto the lucid partition, not over windows mbr.

have you grub1 (grub-legacy) still installed ? if so, need remove/purge it, only grub-pc and grub-common have to be installed

---

