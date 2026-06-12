---
title: "Visual effects - none"
date: 2009-07-14
forum: General Help
---

### Post by Mikael P. on 2009-07-14
Hello,
I am wondering if anyone could help out with this? When I switch my visual effects to none I get a flickering screen. Though the frequency is very low like once every twenty seconds so it's still possible to use it. But I'd rather it to go away.
How do I get rid of it?

Switching to Normal is not an option in this case as that will crash certain aspects of Maya.

Grateful for any help.

(oh, and I am on jaunty 9.04 with a 64 bit system.)

---

### Post by bodyharvester on 2009-07-14
go to ADMINISTRATION > SYSTEM TESTING

see whats going on there, it may tell you

---

### Post by Mikael P. on 2009-07-14
No, sadly nothing from that report. All of the tests it performed worked fine.

---

### Post by bodyharvester on 2009-07-14
on Window$ id suggest going into control panel and choosing devices/hardware manager to see if any devices have that exclamation mark near them but for ubuntu im not too sure

ill tell you if i think of anything

good luck

---

### Post by Mikael P. on 2009-07-14
hmm yes. I guess it is related to overlay in some kind of way. Graphic drivers not liking something.
But I have yet to gain my wizards hat to be able to fix it.

Thanks for your help anyway!

---

### Post by Mikael P. on 2009-07-16
If anyone else runs into this problem. Here is how I fixed it.

It seems to be related to the powermizer functionality that has been broken for what seemed ages.

I was running the latest official nvidia drivers 180.xx and updated to the stable (beta?) drivers 185.xx

Now it's all gone. (Though I did some other smaller changes to files located in obscure places. So if that doesn't fix it for you. Holler and I'll give you a full description).

---

