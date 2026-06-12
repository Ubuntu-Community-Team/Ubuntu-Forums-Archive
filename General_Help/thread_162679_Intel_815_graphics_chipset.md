---
title: "Intel 815 graphics chipset"
date: 2006-04-19
forum: General Help
---

### Post by nephesh on 2006-04-19
Hi all,

I have a Dell Inspiron 2500, 1ghz pentium 3, 256mb ram, with an Intel 815 graphics chipset.  I am running ubuntu dapper 6.06 (.08 now I think) and I am wondering how I can get 3d acceleration working.  Intel has 'Linux' drivers at 

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

but they are in .rpm format and are meant for the redhat distribution.  I'm not sure how to deal with that in ubuntu since most packages are .deb format.  Any help would be appreciated with this.

Thanks,
nephesh

---

### Post by nephesh on 2006-04-19
nevermind it turns out 3d support is built into ubuntu.
however, 3d support can only be used at 16 color depth rather than 24.
so i just did a
sudo gedit /etc/X11/xorg.conf

and changed the default depth to 16

---

### Post by xenmax on 2006-04-19
Yup, i have intel i810E graphics card and i also sadly realized a few weeks ago that hardware acceleration is only possible for my graphics card-i810 driver combo at 16bit color depth.:( Here is a snip from man page of my driver:  man i810
> 
DESCRIPTION
       i810  is  an  Xorg  driver for Intel integrated graphics chipsets.  The
       driver supports depths 8, 15, 16 and 24.  ........................ The driver sup&#8208;
       ports hardware accelerated 3D via the Direct  Rendering  Infrastructure
       (DRI),  but only in depth 16 for the i810/i815 and depths 16 and 24 for
       the 830M and later.
SUPPORTED HARDWARE
       i810 supports the i810, i810-DC100, i810e,  i815,  830M,  845G,  852GM,
       855GM, 865G, 915G and 915GM chipsets.

However, I wonder if this is a driver restriction or the graphics card simply cannot do hardware acceleration.

---

