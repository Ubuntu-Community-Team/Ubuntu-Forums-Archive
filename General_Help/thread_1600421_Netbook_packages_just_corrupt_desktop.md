---
title: "Netbook packages just corrupt desktop"
date: 2010-10-18
forum: General Help
---

### Post by gohanssjn on 2010-10-18
Dell Latitude XT
N-Trig touch screen
ATI x1250 Video Card
Ubuntu 10.10

If I install the Netbook packages (either with the Netbook CD or by installing them into a Desktop installation), I just get garbage on the screen that is unusable.

A picture says it all:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=172797&stc=1&d=1287459034[/IMG]

Any ideas to get the Netbook edition working?

---

### Post by kerry_s on 2010-10-18
the new netbook is 3d, so you need your vid drivers installed & working before you log in to netbook.
so at log in screen select gnome, install your drivers then try again.

---

### Post by gohanssjn on 2010-10-19
Not sure what drivers to install to be honest.  I had Compiz up and rnning and it said it install the video drivers, but I guess that is not enough?

---

### Post by sikander3786 on 2010-10-19
You can activate the drivers from System > Administration > Additional Drivers.

If they are not listed there, you can manually download and install them as per instructions here.

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

---

### Post by nighthawkix on 2010-10-25
The video drivers from ATi cannot be installed.

After decompressing the drivers, I get an error in the command prompt and the installation terminates.

---

### Post by sikander3786 on 2010-10-25
> **nighthawkix said:**
> The video drivers from ATi cannot be installed.

After decompressing the drivers, I get an error in the command prompt and the installation terminates.
Can you please reproduce the error and post it here?

---

### Post by nighthawkix on 2010-10-26
Sorry :-/ I gave up on the Netbook edition and decided to stick with the Desktop edition of 10.10

I'm completely new to Linux/Ubuntu so I'm going to learn using a OS that is known to work :-)

---

### Post by miki4242 on 2010-11-01
I tried installing ubuntu-netbook and unity as additions to a regular ubuntu-desktop install on a Dell Latitude XT a week ago and ran into the same problem.

This is what I've found:

- Unity doesn't work because it requires some capabilities (like non-power-of-two textures) which the video hardware (ATI Radeon Mobility X1250) doesn't support and which the default X video drivers for it don't emulate.
- ATI removed support for older hardware like the Mobility X1250 from its proprietary fglrx some time ago, so I couldn't try this.
- ATI does have a 'legacy' fglrx driver which should support the Mobility X1250, but that driver doesn't work with the current X server version in Ubuntu, so I couldn't try that either.

Yep, there you have it, a Catch-22.

I solved this by installing the latest bleeding edge drivers from the xorg-edgers PPA, which resulted in a Gallium3D driver taking care of the ATI hardware.
Now Unity does start, and I can use it with the touchpad and single-touch touchscreen :)
I haven't managed to get multitouch working yet, this may be related to various N-Trig issues.

---

### Post by nqd on 2010-11-02
What package in Xorg that you installed to get the 3D driver to work? Were you able to enable scrolling in other apps beside firefox and chrome?

---

