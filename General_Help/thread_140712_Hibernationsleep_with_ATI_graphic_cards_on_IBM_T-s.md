---
title: "Hibernation/sleep with ATI graphic cards on IBM T-series?"
date: 2006-03-06
forum: General Help
---

### Post by tbraun on 2006-03-06
Hello!

I am looking at purchasing a new laptop, and have heard good things
about the IBM T-series. Supposedly, it has good Linux support.

Since I would obviously want to run Ubuntu on it, I am interested to
know if hibernation to RAM and/or disk is working correctly and out of
the box (or only with minimal configuration).

The reason I ask is that I currently have a laptop with ATI graphic card
(Compaq nc6000), and I can absolutely not get 3D acceleration AND
hibernation to work. If I switch off 3D acceleration, the hibernation fairs
better. But what's the fun in this?

The IBM T-series also uses ATI cards, and therefore, I am concerned
wether this would work. Has anyone tries this and can confirm if this
works or not?

Thank you very much...

Tom Braun

---

### Post by hod139 on 2006-03-06
Out of the box Hibernation and sleep will not work due to buggy ATI fglrx drivers.  However, using this [howto]("http://ubuntuforums.org/showpost.php?p=423584"), you can update the drivers to the latest version and then all is good.

---

### Post by zachtib on 2006-03-06
I've got a thinkpad r-series, and they are great for linux

suspend and hibernate will take some teaking, but it can be done

---

