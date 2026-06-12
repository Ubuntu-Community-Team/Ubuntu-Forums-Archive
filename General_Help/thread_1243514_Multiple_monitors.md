---
title: "Multiple monitors"
date: 2009-08-18
forum: General Help
---

### Post by dlw on 2009-08-18
Which is the best version of Ubuntu to use for multiple monitors.
I have 9.04 and not having much luck.

Thanks,
dlw

---

### Post by scouser73 on 2009-08-18
If you have an nVidia graphics card then setting up dual monitors couldn't be easier.

Go to Terminal and paste this code: **gksudo nvidia-settings**

That will open up the **nVidia X Server Settings** console, click on the **X Server Display Configuration** & from there you can adjust the monitors to suit your needs.

Once you are happy with your monitor setup, click **Apply** then click **Save To X Confuguration File**.

---

### Post by Engenia on 2009-08-19
> **scouser73 said:**
> ....Go to Terminal and paste this code: **gksudo nvidia-settings** ...
Don't try & run it from System -> Administration -> NVIDIA X Server Settings
like I've been doing. :oops:
It needs su privileges to save the modified /etc/X11/xorg.conf file

---

### Post by dtoronto on 2009-08-19
> **scouser73 said:**
> 
Go to Terminal and paste this code: **gksudo nvidia-settings**

That will open up the **nVidia X Server Settings** console, click on the **X Server Display Configuration** & from there you can adjust the monitors to suit your needs.

Thanks this actually answered my question as well.

---

### Post by ISigs on 2009-08-27
> **scouser73 said:**
> If you have an nVidia graphics card then setting up dual monitors couldn't be easier.

Go to Terminal and paste this code: **gksudo nvidia-settings**

That will open up the **nVidia X Server Settings** console, click on the **X Server Display Configuration** & from there you can adjust the monitors to suit your needs.

Once you are happy with your monitor setup, click **Apply** then click **Save To X Confuguration File**.

Hello, I'm also having issues with multiple monitors. I go the the nvidia X Server Settings console, but when I do, it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " So I type gksudo nvidia-config, it waits a moment, and then nothing happens. What should I do? Thanks!

Edit: Nevermind, I figured it out. Thanks for the help!

---

### Post by ja4 on 2009-09-16
> **Engenia said:**
> Don't try & run it from System -> Administration -> NVIDIA X Server Settings
like I've been doing. :oops:
It needs su privileges to save the modified /etc/X11/xorg.conf file

Run it as root by typing

gksudo nvidia-settings

---

### Post by Isarii on 2009-09-17
I have an ATI something or the other (what's the equivalent to dxdiag in Ubuntu?) and all I had to do was plug mine in and set it to not mirror.  It was amazingly easy.

I guess I got lucky though lol.

---

