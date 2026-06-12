---
title: "Please Help!!!!"
date: 2009-10-29
forum: General Help
---

### Post by ikon_ on 2009-10-29
What happens when i boot into my Jaunty(Ubuntu 9.04) is that all works fine but if my bluetooth is switched off or if I want to decrease the brightness of my monitor using the laptop buttons I am unable to do the same. I don't know what the problem is but I just can't do these things. 
I have a Dell Studio laptop with 3GB RAM and 320 HDD. Please somebody help.:confused:

---

### Post by akakingess on 2009-10-29
I saw someone else with the brightness keys not working, and I'm not sure we ever got that fixed, but I believe you can add the Bluetooth applet in the "taskbar" next to where the volume and time are, also, you can open up adminstration-->log-in manager, and I believe there are startup options or "services" and bluetooth is in there I know, cuz I disabled it since I didn't use it on that particular machine.

---

### Post by PeggySue on 2009-10-29
Hi,

My sister had a problem with Dell studio screen brightness using 9.04.  I followed this thread:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/392812]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/392812")
and tried Bucik85's fix.  It didn't work so I removed the fix and to my surprise the screen brightness control has worked perfectly ever since!!
I don't understand the details but the problem might be on the apic front.  Look out for acip which is something else.  Google both.

For Bluetooth try, system | preferences | bluetooth.

Good luck.

---

