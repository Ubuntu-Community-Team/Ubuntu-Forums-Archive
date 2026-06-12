---
title: "Recompile kernel tutorial"
date: 2010-02-28
forum: General Help
---

### Post by bobin on 2010-02-28
Can you guide me to any tutorial which helps in boosting system speed by recompiling the kernel

---

### Post by bobin on 2010-02-28
bump

---

### Post by bobin on 2010-02-28
bump

---

### Post by lavinog on 2010-02-28
What is your rush?

Checkout the master kernel thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

or the help docs:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by dcstar on 2010-02-28
> **lavinog said:**
> What is your rush?
........

It was obviously too difficult to use the forum search function and get an answer in a couple of minutes, far easier to wait a few hours until someone caves in and serves up the information.

---

### Post by lavinog on 2010-02-28
> **dcstar said:**
> It was obviously too difficult to use the forum search function and get an answer in a couple of minutes, far easier to wait a few hours until someone caves in and serves up the information.
I hesitated at first.

@OP: Don't expect a smooth experience.  Something that was working may no longer work...ureadahead will not work if you use a custom kernel, so you should uninstall it.

Is there a problem with the current speed of the system?

---

### Post by bobin on 2010-02-28
yeah i had a search bootcharts and systems with a similar build as mine were giving a boot of 15-20s while I am stuck at 30s

---

### Post by lavinog on 2010-02-28
Are you still using 9.04 (like your sig says?)
Upgrade to karmic and see how fast your boot is.
Also bootchart delays your boot quite a bit, so when you are no longer needing it, uninstall it.

If karmic isn't fast enough for you, make sure you are using a ext4 file system.

Are you using restricted drivers like nvidia or fglrx?  These are pretty bloated and can slow down your boot also...there is nothing you can really do about this if you plan to keep using them.

disable some startup services that you dont need.
I don't have bluetooth on my laptop...I uninstalled all of the bluetooth packages from my system.

---

### Post by bobin on 2010-03-01
how unbloated are the free nv drivers? Are they good enough?

---

### Post by lavinog on 2010-03-01
> **bobin said:**
> how unbloated are the free nv drivers? Are they good enough?

It should be better, but it doesn't look like they will offer 3d support.
I don't have any experience with nvidia.

---

### Post by sandy8925 on 2010-03-03
Boot times won't really speed up all that much just by recompiling the kernel. As lavinog said use a faster filesystem like ext4. It is way faster than ext3. Getting a faster hard disk helps a lot of course. Dunno abt how good nv drivers are but i don't think performance will be very good. you could try the noveau drivers which are currently being developed. you should also reduce the number of programs that run automatically on startup (this is an absolute necessity in windows thanks to stupid programs that automatically startup unnecessarily each time)

---

