---
title: "Networking."
date: 2011-04-03
forum: General Help
---

### Post by galacticaboy on 2011-04-03
I have a computer with Elementary OS Jupiter that is basically Ubuntu 10.10. I would like to network my computer with my fiances who has Windows 7. How can I do that? We both only have one Network card and they both feed to the cable box for internet. Is there a way we can do this so we can share files and such without another network card? I am a newbie and Linux so the dummified version would be great! Thanks!
David

---

### Post by graphius on 2011-04-03
if you are sharing an internet connection, you must be using a router, or at least a hub. All you need to do is install samba on your ubuntu computer
```
sudo apt-get install samba
```
or search for samba in the Ubuntu Software Centre. Configuration is pretty straight forward (easier than in windows, in my opinion)

---

### Post by galacticaboy on 2011-04-03
> **graphius said:**
> if you are sharing an internet connection, you must be using a router, or at least a hub. All you need to do is install samba on your ubuntu computer
```
sudo apt-get install samba
```or search for samba in the Ubuntu Software Centre. Configuration is pretty straight forward (easier than in windows, in my opinion)

Thank You! I will try this!

---

