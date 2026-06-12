---
title: "Problems with network after xorg install"
date: 2005-03-01
forum: General Help
---

### Post by psyko-lefse on 2005-03-01
Alright, here's the problem. Just installed ubuntu. The first thing I did was upgrading to Hoary (to get WiFi to work), then I upgraded the kernel to 2.6.10-686 to get speedstep to work. After these upgrade both wifi and speedstep where working. Then I installed the xorg-drivers to get 3dsupport. The installation went problem-free, but I still dident had 3dsupport. But the wifi was working fine. Then I changed device driver in the xorg.conf -file from "ati" to "fglrx". Wee, 3dsupport :D

But after I changed device-driver, my wireless connection dont work anymore. I cant seem to activate it in Networking, and it showes no wireless devices detected. help?

---

### Post by psyko-lefse on 2005-03-01
It looks like the change of device driver has deleted my wireless card, because I tried to delete the old connection and make a new one, but I didn't have any wireless devices to choose from :?: 

Will try changing the driver back to ati, to see if this solves the WiFi-problem.
But then, of course, 3dsupport will be gone, so it cant be a final solution....

---

### Post by psyko-lefse on 2005-03-01
It worked when I set the device driver back to ATI, but then the 3D support didn't work...

---

### Post by Term1n4l on 2008-02-25
I am currently having this same problem with my brothers computer. Is there any way to use the fglrx drivers and still have access to the internet?

Does anyone have a fix for this problem or possibly an idea?

---

