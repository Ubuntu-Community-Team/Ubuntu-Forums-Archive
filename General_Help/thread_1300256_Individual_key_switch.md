---
title: "Individual key switch"
date: 2009-10-24
forum: General Help
---

### Post by meinvateristnein on 2009-10-24
i have a german laptop ... although its handy as most know in german the y and z buttons are switched because of the sound thez make ... obviouslz this is a problem ....... my question is is their anz way to keep the german kezboard layout and just switch these two kezs individuallz??? 

 anz help is much appreciated!!

---

### Post by Johnny B on 2009-10-24
to get your keymap:
> xmodmap -pke
find Y and Z in there 
for me Y=29 and Z=52

to change your keymap:
> xmodmap -e 'keycode 52 = z'
xmodmap -e 'keycode 29 = y'  

---

### Post by meinvateristnein on 2009-10-24
OMG thank you so much ... it worked like a charm

---

