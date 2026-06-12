---
title: "Screen brightness lesser at highest level"
date: 2010-09-08
forum: General Help
---

### Post by luvshines on 2010-09-08
Don't know if this is the right place to ask this but since it has been bugging me for the past few dayz, I should give it a try newhere :D

Shifted to Ubuntu(10.04) recently from Fedora(11) and noticed something strange with the way screen brightness is working.
When my laptop is on battery power and I increase the brightness to the highest level, the brightness increases to the second last level and then suddenly drops

So, in the following file
```

cat /proc/acpi/video/VID1/LCD0/brightness 
levels:  20 25 30 35 40 45 50 55 60 65 70 75 80 85 90 100
current: 100

```

Brightness is highest at 90 then drops at 100
Haven't noticed this when it's on AC power

Laptop is lenovo Thinkpad. Can I set 90 as the highest level when I switch from AC to batter power. It's very annoying to switch the brightness level each time from 100 to 90 on my own.

I am unable to locate the event which is controlling the brightness when I press the bright[up/down] button

---

### Post by luvshines on 2010-10-02
Bump !!

---

### Post by luvshines on 2010-10-15
---bump---

---

