---
title: "Gspca not installed"
date: 2009-07-10
forum: General Help
---

### Post by piratebill on 2009-07-10
In my system I have a tv tuner and a webcam.  Applications like Cheese, skype and ekiga all see the tv card as a proper video source.  None of them even see my cam as an option.  lsusb produces this:
```
Bus 002 Device 007: ID 046d:08ae Logitech, Inc. Quickcam for Notebooks

```

After googling a bit I found the latest gspca driver supports my cam.  The gspca I downloaded off of [http://mxhaard.free.fr](http://mxhaard.free.fr) didn't even compile, so I turned to Synaptic and downloaded gspca-source.  Following the instructions that came with the source files, I typed
```
sudo m-a prepare
``` which worked perfectly, and then ```
sudo m-a a-i gspca
``` which failed miserably (I can post the errors if it will help, but they are a bit long).  

Now I am probably wrong, but I don't think I have gspca installed at all (even though Jaunty is supposed to already have it?).  Has anyone gotten gspca to compile?  I really want to get my web cam working again (it hasn't since Gutsy).


Edit:
```
sudo modprobe -l | grep gsp
``` shows that I do gspca on the system (under kernel/drivers/media/video/gspca/).  However ```
sudo modprobe gspca
``` returns ```
FATAL: Module gspca not found.
```  Any ideas?

---

### Post by SuperMetroid on 2009-11-09
> **piratebill said:**
> ```
sudo modprobe -l | grep gsp
``` shows that I do gspca on the system (under kernel/drivers/media/video/gspca/).  However ```
sudo modprobe gspca
``` returns ```
FATAL: Module gspca not found.
```  Any ideas?

I have the exact same problem (using Karmic). It shows that I have gspca on my system, because when I use
'$ sudo modprobe -l | grep gsp' it returns:
```
kernel/drivers/media/video/gspca/gspca_main.ko
kernel/drivers/media/video/gspca/gspca_conex.ko
kernel/drivers/media/video/gspca/gspca_etoms.ko
kernel/drivers/media/video/gspca/gspca_finepix.ko
kernel/drivers/media/video/gspca/gspca_mars.ko
kernel/drivers/media/video/gspca/gspca_mr97310a.ko
kernel/drivers/media/video/gspca/gspca_ov519.ko
kernel/drivers/media/video/gspca/gspca_ov534.ko
kernel/drivers/media/video/gspca/gspca_pac207.ko
kernel/drivers/media/video/gspca/gspca_pac7311.ko
kernel/drivers/media/video/gspca/gspca_sn9c20x.ko
kernel/drivers/media/video/gspca/gspca_sonixb.ko
kernel/drivers/media/video/gspca/gspca_sonixj.ko
kernel/drivers/media/video/gspca/gspca_spca500.ko
kernel/drivers/media/video/gspca/gspca_spca501.ko
kernel/drivers/media/video/gspca/gspca_spca505.ko
kernel/drivers/media/video/gspca/gspca_spca506.ko
kernel/drivers/media/video/gspca/gspca_spca508.ko
kernel/drivers/media/video/gspca/gspca_spca561.ko
kernel/drivers/media/video/gspca/gspca_sq905.ko
kernel/drivers/media/video/gspca/gspca_sq905c.ko
kernel/drivers/media/video/gspca/gspca_sunplus.ko
kernel/drivers/media/video/gspca/gspca_stk014.ko
kernel/drivers/media/video/gspca/gspca_t613.ko
kernel/drivers/media/video/gspca/gspca_tv8532.ko
kernel/drivers/media/video/gspca/gspca_vc032x.ko
kernel/drivers/media/video/gspca/gspca_zc3xx.ko
kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
kernel/drivers/media/video/gspca/stv06xx/gspca_stv06xx.ko
```Yet, when I try:
'$ sudo modprobe gspca'
Or to compile gspca's general webcam driver package from source, it says that the gspca module is not found.

---

### Post by clandel on 2009-11-18
+1

Under Debian, it is possible to use the gspca module with kernel version 2.6.26, it seems to be the same problem under Ubuntu as well. I can't use my cam with vendor/product id 046d:08af (as shown by lsusb) anymore.

---

