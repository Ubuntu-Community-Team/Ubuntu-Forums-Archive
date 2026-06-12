---
title: "How to get Ubuntu to display on widescreen monitor?"
date: 2012-01-08
forum: General Help
---

### Post by solorize on 2012-01-08
Hi,

I've just replaced my monitor with a widescreen LG E2251.

But I can't change the resolution to a "wide screen" resolution
any higher than 960 x 540 (16:9)?

I have other modes available, but they stretch the screen.

See screenshot below:

[IMG]http://i11.photobucket.com/albums/a199/solorize/resolution.png[/IMG]

Does anyone know how I can get a higher (16:9) resolution?


Any help would be appreciated. If you need to know anymore details
please let me know and I will try and get the relevant info.

Mark

---

### Post by dak0 on 2012-01-08
Have you tried  from Nvidia control ?
[IMG]http://pic.mk/images/2htJ.png[/IMG]

---

### Post by solorize on 2012-01-09
Hi dak0,

I did try to access Nvidia Control, but all I got was
the following error:


> Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

Any ideas why this is happening? and how to get it to work?

Also my monitor is shown as "UNKNOWN" on the DISPLAYS screen
is there a specific driver I should install from somewhere?
I have had a look but can't seem to find one.

---

### Post by bab1 on 2012-01-09
> **solorize said:**
> ...

Any ideas why this is happening? and how to get it to work?

I had this problem with my Samsung monitor (1140x900) until I realized that the [**_[COLOR="Blue"]EDID info[/COLOR]_**]("http://en.wikipedia.org/wiki/Extended_display_identification_data") is only supplied via a digital (DVI or HDMI) connector.  If you are using an analog video card then it has no way to ID the monitor.  When I installed a new nVidia card I used the DVI connector and the monitor was detected automatically.

How are you connecting your monitor; via an analog or digital connection?

---

### Post by solorize on 2012-01-09
Thanks for the reply.

I am connected via analog, so I guess this is why my
monitor is not being detected :(

Even so should it still allow me to select a widescreen
resolution?

---

### Post by bab1 on 2012-01-09
> **solorize said:**
> Thanks for the reply.

I am connected via analog, so I guess this is why my
monitor is not being detected :(

Even so should it still allow me to select a widescreen
resolution?

Maybe in theory, but not in practice.  The settings you have are pretty much it.  There is not even a xorg.conf file anymore.

---

