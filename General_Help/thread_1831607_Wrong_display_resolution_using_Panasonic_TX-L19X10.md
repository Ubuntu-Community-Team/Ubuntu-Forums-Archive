---
title: "Wrong display resolution using Panasonic TX-L19X10B"
date: 2011-08-23
forum: General Help
---

### Post by Martin Houlton on 2011-08-23
Hi

I installed Ubuntu 11.04 about a week ago and everything has been fine except that Ubuntu thinks my monitor has a resolution of 1024x768, while the actual resolution is 1366x768. I can't set a higher resolution through the visual interface (my monitor is detected as "unknown") Are there commands I can issue through the terminal to sort this out?

Thanks.

---

### Post by sikander3786 on 2011-08-23
Welcome to the forums :)

Did you install the proper drivers for your graphics card? Output of the following command would tell us. Get to a Terminal by searching the Dash in Unity or by going to Applications > Accessories > Terminal in classic GNOME and run:

```
lshw -c video
```

---

### Post by Martin Houlton on 2011-08-23
Thanks sikander

That command produces:-

       description: VGA compatible controller
       product: G72 [GeForce 7500 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:24 memory:dc000000-dcffffff memory:c0000000-cfffffff memory:dd000000-ddffffff memory:de000000-de01ffff

But it tells me that I should be logged on as super-user. I remember su from my Xenix days, but it won't accept my password.

---

### Post by sikander3786 on 2011-08-24
You are using the open source Nouveau driver for Nvidia:

> configuration: driver=nouveau latency=0

Go to System > Administration > Additional Drivers in classic Gnome or search the Dash in Unity and see if any proprietary drivers are available for you card. If they are enable, activate and that might solve your issue.

---

### Post by Martin Houlton on 2011-08-25
Hi Sikander

I did what you suggested and found a NVIDIA accelerated graphics driver,  installed that, and when I rebooted I got into the Unity desktop (I was  previously in GNOME). Unfortunately nothing on the screen responded to  the mouse. Thankfully I was able to reboot into an earlier release of  Ubuntu 11.04 which works using GNOME. How can I restore my latest version of Ubuntu?

---

### Post by sikander3786 on 2011-08-26
Just un-install the driver from within classic Gnome and reboot.

Installing the 'nvidia-173' driver from Additional Drivers might help as it is capable of running Unity on older cards better than the new current driver.

---

### Post by Martin Houlton on 2011-08-26
Hi Sikander

I have swapped the monitor for an old Acer 17" that I have. Ubuntu can detect the monitor, I've got 1280 x 1024 resolution, the taskbar doesn't go off the bottom of the screen and I've got my vertical scrollbars back. It's better all round. Thanks for your help.

---

