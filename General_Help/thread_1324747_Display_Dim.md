---
title: "Display Dim"
date: 2009-11-12
forum: General Help
---

### Post by prem1er on 2009-11-12
I was wondering if there was an option to change the time of the display dim in the power management settings. There is an option to toggle the 'dim display when idle', but the idle timer is like 10 seconds and I would like to increase it. Using 9.10. Thanks.

---

### Post by prem1er on 2009-11-13
bump.

---

### Post by prem1er on 2009-11-17
bump

---

### Post by my_key on 2009-12-09
Type alt + F2 (to run a program) and run gconf-editor. Go to / > apps > gnome-power-manager > backlight and change the value of idle_dim_time to whatever value you like (in seconds, the default value is 10). I changed it to 20.

Cheers 

Michael

---

### Post by prem1er on 2009-12-10
Thank you.

---

