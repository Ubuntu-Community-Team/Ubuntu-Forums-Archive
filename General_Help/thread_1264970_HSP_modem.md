---
title: "HSP modem"
date: 2009-09-12
forum: General Help
---

### Post by ttsdinesh on 2009-09-12
i am using PC-tel HSP win2k modem. Can anybody show me the linux driver for it?

---

### Post by JujuLand on 2009-10-02
Download the driver here:

[http://linmodems.technion.ac.il/pctel-linux/?C=M;O=A](http://linmodems.technion.ac.il/pctel-linux/?C=M;O=A)

take the last version
take too the readme file (some difference, but near from the solution)
uncompact the gz file
go to the uncompressed folder
run sudo ./setup
the driver must then be ok with some more commands modprobe, ...
run sudo pppconfig to create your connexion
for me, it seems that the inclusion in dip isnt't possible, or I have perhaps miss something, so launching
ppon <myconfig> won't work
but, sudo ppon <myconfig> don't give me no more error

so, for me, it seems to be ok, except I have no connexion parms with me  to test (I'm just finishing to install it)

A+

---

