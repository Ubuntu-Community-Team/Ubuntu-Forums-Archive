---
title: "black screen"
date: 2009-07-15
forum: General Help
---

### Post by kiwimenace on 2009-07-15
OK, i get a black screen. start computer, grub loads, i choose, jaunty boots, i login, the little bars moves across get to the end, then i just get black screen. The shade of blackness does change a couple of times.
 Events leading upto this.
 I was playing with startup manager a little and also another splash program that i forget the name of,,, never changed anything accept told it to show txt as it loads, also i tried to make it load a splash pick but that didnt work. Actually i had even restarted it with no problem before i had the black screen problem. The other thing i did note is that the text while loading jaunty doesnt show anymore.
 Any help to recover my system will be great.

---

### Post by CrusaderAD on 2009-07-15
Try this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

