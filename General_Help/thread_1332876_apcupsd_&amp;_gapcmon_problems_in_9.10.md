---
title: "apcupsd &amp; gapcmon problems in 9.10"
date: 2009-11-20
forum: General Help
---

### Post by Gareth Lock on 2009-11-20
I have a Smart-UPS hooked up to my Dell PowerEdge 1600SC via USB. Ever since I upgraded to Ubuntu 9.10 I can't seem to get either gapcmon or apcupsd to work with it. I'm using the same config options as I was using without any problems when running 9.04. Have any others had this problem?
 
Any suggestions would be welcome.

---

### Post by Jean248 on 2009-11-21
I have exactly the same problem

---

### Post by jack_hmr on 2010-04-25
In 10.04 I found that the usb port was not auto detected as it should be.

In the apcupsd config file I changed "DEVICE" to "DEVICE /dev/usb/hiddev0"

---

