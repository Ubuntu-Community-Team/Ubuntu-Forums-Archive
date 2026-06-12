---
title: "GDM does not start at boot"
date: 2010-10-15
forum: General Help
---

### Post by gabriel b on 2010-10-15
So for the last few days gdm ans not started on boot up. tty7 is a blank screen and I'm automatically put in tty1. There I can log in and run gdm manually. 

It has a started automatically a few times with out me doing any changes, but most of the times not. So far I haven't found out what the cause is but I've found some similar (the same?) problems:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/583660](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/583660)
[http://superuser.com/questions/142339/gdm-wont-automatically-start-after-boot](http://superuser.com/questions/142339/gdm-wont-automatically-start-after-boot)
[http://ulyssesonline.com/2010/08/14/gdm-does-not-start-in-ubuntu-10-04/](http://ulyssesonline.com/2010/08/14/gdm-does-not-start-in-ubuntu-10-04/)

I'm running 10.04 64-bit if it matters. 

Any suggestions?
/Gabriel

---

### Post by sriraghunath.joshi on 2010-10-15
Hi Gabriel,

I think I have the same problem. 

When I start my ubuntu, only the Command window is opening.. I am not able to view ubuntu like in a graphical interface..

Is that the same problem you are facing too?

Mine is 10.04 ubuntu..

Please solve some body!!

---

### Post by gabriel b on 2010-10-15
ok, now I didn't log in immediately, and got the following error:
tpm_tis 00:0a: tpm_transmit: tpm_send: error -62

related?

---

### Post by gabriel b on 2010-10-16
Nobody?  

Soon I will resort to the 'windows solution', ie reinstallation of ubuntu. But it is not that satisfying as I have no idea if the problem will return. 

/Gabriel

---

### Post by bbossola on 2010-11-20
Same problem here. Trying to unistall / reinstall gdm does not help in the long run. See also this bug:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/675904](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/675904)

Currently, each time, I have now to login trough the command line and manually execute "sudo gdm start". 

Any help?

---

### Post by bbossola on 2010-11-20
Hacked and temporary fixed with the brute-force solution described here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/532436)

---

