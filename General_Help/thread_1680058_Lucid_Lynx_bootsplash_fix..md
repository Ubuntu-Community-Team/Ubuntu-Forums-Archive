---
title: "Lucid Lynx bootsplash fix."
date: 2011-02-01
forum: General Help
---

### Post by stchman on 2011-02-01
Hello all, I have found a fix to the Lucid bootsplash.

The crappy bootsplash in Lucid keeps it from looking polished.  Here is a work around I have come up with.

This work around works especially well for proprietary graphics drivers like nvidia.

Step 1:
Install StartUp-Manager

```
sudo apt-get install startupmanager
```Step 2
Use this code forces Lucid to wait for the graphics driver to load up.
```
&#65279;sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit
```Step 3
Execute StartUp-Manager (System->Administration->StartUp-Manager
On the Boot Options tab check Show boot splash and uncheck Show text during boot
I selected a resolution of 1280x1024 for my 1920x1200 monitor.

After this the boot up looks beautiful!!!!!!

I got some of the ideas from this website.
[http://reformedmusings.wordpress.com/2010/05/01/corrupt-bootsplash-fix-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/01/corrupt-bootsplash-fix-in-ubuntu-lucid-10-04-lts/)

---

