---
title: "Figuring out scripting..."
date: 2011-01-16
forum: General Help
---

### Post by jlaki on 2011-01-16
Considering the fact that I reinstall my system quite often and that, after I install my nVidia proprietary driver, my bootscreen becomes ugly, I came to an idea to make my first script following [THIS]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") guide that surely works as I tested it on my and few other machines.

Following the few guides, I came to this:

> 
#! /bin/bash
sudo apt-get install v86d
cd /etc/default/
sudo sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodesetvideo=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"/g' grub
sudo sed -i 's/#GRUB_GFXMODE=640x480/GRUB_GFXMODE=1280x1024/g' grub
cd /etc/initramfs-tools/
sudo sed -i 's/# sd_mod/uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap/g' modules
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub2
sudo update-initramfs -u


Of course, I "chmod +x"ed it.

It seems quite right to me, but it doesn't seem to get the job done correctly.

Can anyone please help me to finish my first script?

Thank you.

---

