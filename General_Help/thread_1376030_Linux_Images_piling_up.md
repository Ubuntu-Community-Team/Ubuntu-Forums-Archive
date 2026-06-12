---
title: "Linux Images piling up"
date: 2010-01-08
forum: General Help
---

### Post by bluestar14 on 2010-01-08
every time a new linux_image_generic install, my grub boot menu gets longer, any way to delete old images?

---

### Post by mk1w86 on 2010-01-08
There is some information here on removing boot entries in Ubuntu 9.10:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by ibuclaw on 2010-01-08
The dirty way of doing this (without sifting through every single package) would be something along the lines of:
```
sudo apt-get purge $(dpkg -l | awk '/linux.+(headers|image).+/{print $2}' | grep -v `uname -r`)
```
Copy the entire extract, and paste it in.

If you need clarification on what any of it does, just ask!
Regards
Iain

---

### Post by garvinrick4 on 2010-01-08
You can use Synaptic and remove versions not wanted. Like 2.6.31-14 or something and type
it in and then find kernel and remove. Or you can do the Terminal.
 Also a setting that will only keep 2, I think default is 7 or something crazy. Look in menu and see how many it is suppose to retain.

---

### Post by staf0048 on 2010-01-08
Go to synaptic and install startup-manager.  There is an option in one of the tabs related to the number of kernels to keep in grub.  I don't think it actually deletes them, rather it just takes them out of the menu.  This way you don't have to deal with it every time a new kernel is installed - it will always keep the same number of kernels you specify.

---

### Post by bodhi.zazen on 2010-01-08
> **tinivole said:**
> The [s]dirty[/s] geeky way of doing this (without sifting through every single package) would be something along the lines of:
```
sudo apt-get purge $(dpkg -l | awk '/linux.+(headers|image).+/{print $2}' | grep -v `uname -r`)
```Copy the entire extract, and paste it in.

If you need clarification on what any of it does, just ask!
Regards
Iain

The "dirty" was of doing this is, if your kernel is working, put the kernel on hold :lolflag:

---

### Post by ibuclaw on 2010-01-08
> **bodhi.zazen said:**
> The "dirty" was of doing this is, if your kernel is working, put the kernel on hold :lolflag:

I suppose there is also that Janitor app (Accessible via System->Administration->Janitor)

But last time I checked it removed your pockets - as well as cleaning them. ;)

---

### Post by Ginsu543 on 2010-01-09
Yeah, I'd stay away from Computer Janitor as it removes programs you don't want to remove. I personally use Synaptic to remove kernels I don't want. Just remember to remove all the appropriate files for the kernel version you want to remove:

1) linux-headers-2.6.31-xx
2) linux-headers-2.6.31-xx-generic
3) linux-image-2.6.31-xx-generic

You need to remove all three. The recommendation is that you keep the latest kernel and the previous working kernel so that in case something goes wrong with the current one, you can use the previous kernel to boot up with.

---

