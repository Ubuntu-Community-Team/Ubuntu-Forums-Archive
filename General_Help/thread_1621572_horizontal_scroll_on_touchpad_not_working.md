---
title: "horizontal scroll on touchpad not working"
date: 2010-11-14
forum: General Help
---

### Post by emerick7 on 2010-11-14
Upgraded to 10.10 from 10.04 yesterday. Only negative thing I'm experiencing is the horizontal scroll region is not really working. Vertical works great and has it has been. Horizontal is activated (under Mouse>Touchpad>Enable Horiztonal (Edge) Scrolling.

When I move horizontally in the region, the cursor remains in the same place. If I try it many times it does work, but it's pretty much useless.

I'm using the hp tc4200 with a synaptics touchpad.

Any help or ideas? Thanks.

---

### Post by emerick7 on 2010-11-15
any experts on touchpads here who could help me out? thanks very much!

---

### Post by emerick7 on 2010-11-17
apparently I'm the only one having this problem eh?

first time I haven't been able to get help from the forums, so does anyone have an idea of where else to look for an answer?

---

### Post by akhilshetty88 on 2010-11-21
hi emerik7.... hope u  have got the problem solved... 
i too have a similar problem..... exept that the pointer moves but i cant right click on anything....... im using an hp pavilion dv6 3020tu ... what should i do.... ?
thanks :-)

---

### Post by emerick7 on 2010-11-21
did you try out System>Pref>Mouse? there's a touchpad tab where you can enable horizontal (edge) scrolling.

as for me I'm still stuck. hopefully someone will come along with an answer...

---

### Post by emerick7 on 2010-12-06
Problem solved!

Here's how I solved it - went to [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad), specifically where it said: "Install the DKMS driver package provided in [https://bugs.launchpad.net/bugs/308191](https://bugs.launchpad.net/bugs/308191) (comment #115, #116). Reboot, and go to System > Preferences > Mouse > Touchpad and select "Two-finger scrolling"."

Went to that link, and downloaded/installed the deb file [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/546697) and rebooted. Didn't change a thing in the properties.

Now it works as expected!!

Just figured I'd let anyone know in the future who ran into this problem.

---

