---
title: "hal bool values messed up"
date: 2009-11-28
forum: General Help
---

### Post by someNewb on 2009-11-28
everytime i try to write my own fdi config files for hal and add append/merge some key whose value is supposed to be bool it throws in some random weird characters in lshal (and displays it as "string")

for example...

```
<append key="storage.media_check_enabled" type="bool">false</append>
```would result in something like

```
storage.media_check_enabled = ' []%'> (string)
```while it should bestorage.media_check_enabled = false (bool)

---

### Post by diesch on 2009-11-28
*append* only works for list values, use *merge* for bool values.

---

### Post by someNewb on 2009-11-28
oh thanks

by the way, can you help me?
i would like to stop hal from checking the specific usb device in an endless loop

i am snatching my usb port with this:
```
 <match key="usb.bus_number" int="2">
```and then i was trying to stop it from the endless check in any possible way i found online 
```
<merge key="storage.media_check_enabled" type="bool">FALSE</merge>
<merge key="volume.ignore" type="bool">TRUE</merge>
```but with no luck :( system still keeps checking for the usb devices

edit: i just noticed, when i set volume.ignore to TRUE, it sets it to false when i list it in lshal !?

why would it do that

---

### Post by diesch on 2009-11-28
Try using "true" and "false" instead of "TRUE" and "FALSE".

---

### Post by someNewb on 2009-11-28
still false

what's funny is that the value IS being set, because before lshal doesn't even list volume.ignore

---

### Post by diesch on 2009-12-02
Maybe it gets changed by any other rules after yours.

---

