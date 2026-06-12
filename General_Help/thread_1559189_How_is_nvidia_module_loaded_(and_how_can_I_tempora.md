---
title: "How is nvidia module loaded (and how can I temporarily prevent it)"
date: 2010-08-23
forum: General Help
---

### Post by tabnett on 2010-08-23
Hi,

I've been running mythbuntu 8.04 on my HTPC box for a couple of years, which has been 99% great, but I have the occasional random crashes on boot or shutdown. It's always stable when running though.

I use the nvidia restricted driver and would like to try a series of boot/shutdowns without the nvidia drivers loaded to see if that's anything to do with it.

I've tried removing files containing 'nvidia' from modprobe.d, blacklisting nvidia in modprobe.d, disabling the nvidia-kernel init script, but it's always present on boot. 

It seems to be loaded early in the process according to dmesg (around 25-27). How is it loaded? What can I do to disable it and load with vesa instead? 

If it seems to work ok I'll try switching to the nv driver (which hopefully will work supplying RGB pal via scart).

Thanks,
Tom

---

### Post by LowSky on 2010-08-23
simpliest would be to just uninstall it. 

or edit Xorg to use the vesa driver.

sudo gedit /etc/X11/xorg.conf

change the driver listed form Nvidia to vesa

---

### Post by tabnett on 2010-08-23
I don't really want to uninstall it as I plan to keep using it after the test (for a bit).

I removed the gdm service so X wouldn't start at all, but the nvidia module was still loaded.

I think it must get loaded earlier in the boot process, but I'm not sure how.

---

### Post by tabnett on 2010-08-27
For reference, it looks like adding 

noapic nolapic 

as boot parameters has fixed it.

---

