---
title: "removing windows from dual boot with ubuntu"
date: 2012-04-01
forum: General Help
---

### Post by mavmic on 2012-04-01
hello again

if i decide to remove windows from my dual boot install with ubuntu will this cause any problems to ubuntu? i made a wubi installation from windows 7 in a different partition on a single disk.

---

### Post by Claus7 on 2012-04-01
Hello &#967;&#945;&#943;&#961;&#949;&#964;&#945;&#953;,

it will be absolutely fine. You will be able to create a new partition, where you will be able to store data or whatever else you like.

Regards &#967;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by bcbc on 2012-04-01
Wubi uses windows to boot. Yes you can boot a wubi root.disk from a normal ubuntu install if you know how, but... for most people, if you just remove windows you won't get that boot option.

What are you hoping to end up with?

---

### Post by westie457 on 2012-04-01
> **mavmic said:**
> hello again

if i decide to remove windows from my dual boot install with ubuntu will this cause any problems to ubuntu? i made a wubi installation from windows 7 in a different partition on a single disk.

Hi with an Ubuntu install via WUBI you cannot remove Windows without destroying the Ubuntu installation because the Wubi installation is a virtual file-system inside Windows.

The best thing you can do is copy everything you want to keep to external media (cd, dvd, usb-stick or another hard drive). Then reinstall Ubuntu choosing to use the whole hard drive.

---

### Post by Claus7 on 2012-04-01
Hello,

> **westie457 said:**
> Hi with an Ubuntu install via WUBI you cannot remove Windows without destroying the Ubuntu installation because the Wubi installation is a virtual file-system inside Windows.

The best thing you can do is copy everything you want to keep to external media (cd, dvd, usb-stick or another hard drive). Then reinstall Ubuntu choosing to use the whole hard drive.

mea culpa! I agree with *westie457*! It is not so easy since you were using WUBI. I focused on your title and not on your starting thread.

Regards!

---

### Post by mavmic on 2012-04-01
thank you all. i wanted to completely remove windows from my laptop. i guess that cant be done with a wubi installation

thank you for your interest

claus7 &#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#960;&#959;&#955;&#973; , &#967;&#945;&#953;&#961;&#949;&#964;&#943;&#963;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#963;&#949; &#963;&#941;&#957;&#945;

---

### Post by bcbc on 2012-04-01
It can be done... depends what you want to do, but e.g. here is an example: [http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration](http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration)

---

### Post by mavmic on 2012-04-02
thank you bcbc . i will keep this as a choice, it looks a little risky to me . many times things look ok in theory but when you try them dont work that good . i wanted a simple solution . i am afraid of meshing this up ( it has been done :( .)
thank you for your interest

---

