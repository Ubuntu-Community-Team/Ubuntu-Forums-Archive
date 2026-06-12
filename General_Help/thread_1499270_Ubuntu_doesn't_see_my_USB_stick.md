---
title: "Ubuntu doesn't see my USB stick"
date: 2010-06-01
forum: General Help
---

### Post by fernwoodguy on 2010-06-01
Maybe I'm not the best person to be using this OS (no programming experience since about 1988), although so far I really love it, and I've been searching for a solution for this problem and can't find anything. 

When I stick my usb stick into the slot, it doesn't even light up. It works with my digital camera, my usb mouse works too, but none of my usb sticks do. No lights come on, nothing. 

Anyone know how to fix it?

---

### Post by PaulM1985 on 2010-06-01
There is a Storage Device Manager which can be installed from the tab under Applications (Ubuntu Software Centre).  Does this show your drives?  Maybe your drives have been seen, but not mounted.

Paul

---

### Post by fernwoodguy on 2010-06-01
I've installed the Device Manager but I don't know what I'm looking for...

---

### Post by fernwoodguy on 2010-06-01
But, this works: lsusb 

but I have to open up the terminal every time and enter lsusb for it to find it.

---

### Post by PaulM1985 on 2010-06-02
On the left hand side is the partition list and this gives the list of your drives.  sda is general the main disk I think.  If you click Refresh at the bottom other nodes should appear.  Click on one of these then clicking on the Mount button in the "General Configuration" should mount your disk drives.

Paul

---

### Post by fernwoodguy on 2010-06-03
That didn't worked...sdb appeared in the list after I used the terminal to find it first, but the Mount button did not activate.

---

### Post by dino99 on 2010-06-03
to deal with your partitions and devices, into synaptic install mountmanager, then set your pref into: system admin mountmanager

---

