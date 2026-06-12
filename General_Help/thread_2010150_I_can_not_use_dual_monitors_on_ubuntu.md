---
title: "I can not use dual monitors on ubuntu"
date: 2012-06-25
forum: General Help
---

### Post by searayman on 2012-06-25
When I try and un-mirror my monitors it does not work and gives me this error:

required virtual size does not fit available size: requested=(2560, 1024), minimum=(320, 200), maximum=(1600, 1600)

The funny thing is I did a fresh clean install of the latest ubuntu, and it worked when it first booted. But after applying updates it stopped working...

---

### Post by 3Miro on 2012-06-25
Lower the resolution on one of your monitors and it should work.

What is your video card. It seems Xorg doesn't allow for such a huge resolution, it may be confused about the capabilities of your video card.

---

### Post by searayman on 2012-06-25
> **3Miro said:**
> Lower the resolution on one of your monitors and it should work.

What is your video card. It seems Xorg doesn't allow for such a huge resolution, it may be confused about the capabilities of your video card.

It should work with the resolution I am using because it worked earlier. Before I updated the system after a fresh install. Could my xorg be messed up?

Where is my xorg located. Can i pastebinn it so I can get some help?

---

### Post by 3Miro on 2012-06-25
You can use the lower resolution as a temporary workaround.

Xorg is the server running on your system responsibe for the system graphics. Its main configuration file is:
```
/etc/X11/xorg.conf
```
If you don't have such file on your system then you are using the default settings.

You can post the content of xorg.conf, but it will be more important to know what video card you have.

---

### Post by searayman on 2012-06-25
Here is the link to my xorg conf:

[http://pastebin.com/EakkuUDU](http://pastebin.com/EakkuUDU)

also how can i easily check my graphics card?

---

### Post by 3Miro on 2012-06-25
Your xorg.conf contains only some default settings, nothing wrong with it. Here is the command to show your video card, copy/paste this into the terminal:
```
sudo lshw -C display
```

---

### Post by searayman on 2012-06-25
> **3Miro said:**
> Your xorg.conf contains only some default settings, nothing wrong with it. Here is the command to show your video card, copy/paste this into the terminal:
```
sudo lshw -C display
```

thanks here is the result of that command:


```
  *-display               
       description: VGA compatible controller
       product: RV730XT [Radeon HD 4670]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:52 memory:d0000000-dfffffff memory:fe9f0000-fe9fffff ioport:dc00(size=256) memory:fea00000-fea1ffff
mike@m133414:~$ 
```


If anyone could help me get the dual monitors to work now, that would be amzing!

---

### Post by QIII on 2012-06-25
By what method are you trying to un-mirror?

---

### Post by searayman on 2012-06-25
> **QIII said:**
> By what method are you trying to un-mirror?

using the "displays" app

---

### Post by QIII on 2012-06-25
Do you have the fglrx driver installed?  It would seem so from your previous post.

---

### Post by searayman on 2012-06-25
> **QIII said:**
> Do you have the fglrx driver installed?  It would seem so from your previous post.

yes but not the post-release one

---

### Post by QIII on 2012-06-25
How about fglrx-amdcccle, the Catalyst Control Center?

---

### Post by 3Miro on 2012-06-25
Yes, with the AMD binary driver, you should use the Catalyst Control Center rather than the Display app. I have a Laptop with Intel graphics and the Display app works great, but on my Nvidia desktop, I have to use the Nvidia-Settings utility.

---

### Post by searayman on 2012-06-25
> **QIII said:**
> How about fglrx-amdcccle, the Catalyst Control Center?

that worked perfectly, thanks!

---

### Post by 3Miro on 2012-06-26
> **searayman said:**
> that worked perfectly, thanks!

Glad it works. If you have no more questions about this issue, could you please mark the thread as "Solved".

---

### Post by Ubun2to on 2012-06-26
> **QIII said:**
> How about fglrx-amdcccle, the Catalyst Control Center?

That's what I had to do for my double monitor setup.

---

