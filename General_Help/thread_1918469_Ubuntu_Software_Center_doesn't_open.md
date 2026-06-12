---
title: "Ubuntu Software Center doesn't open"
date: 2012-02-01
forum: General Help
---

### Post by nsamba on 2012-02-01
Hey guys! Couple days ago, the boot partition on my disk got unmounted for some reason, but thanks to the forum, I could fix it.

Now, the problem is that Ubuntu Software Center doesn't start, so I can't install most apps.

This is how it appears on the launcher on the left:

[IMG]http://img338.imageshack.us/img338/1042/screenshotat20120201031.png[/IMG]

It doesn't even have an icon anymore.

Do you know how can I fix this?

---

### Post by raja.genupula on 2012-02-01
```
sudo apt-get install --reinstall software-center
```


and relogin again . 

if its not work then 

**unity --reset-icons**

in terminal

EDIT :i think unity --reset no need because we are dealing with only icons . ok after unity --reset-icons , if its not fine then 
unity --reset
unity --reset-icons

in terminal .

all the best man .

---

### Post by nsamba on 2012-02-01
I tried, but it gets stuck here:

[IMG]http://img88.imageshack.us/img88/9656/screenshotat20120201041.png[/IMG]

---

### Post by raja.genupula on 2012-02-01
ok open your ubuntu dash(Alt+f2) then type sofwtare center . if its giving with original icon of software center then 

open you terminal and  do

```
unity --reset
 unity --reset-icon
 
```
If you are not getting software center with original icon at dash then remove software center and reinstall it . 

All the best .

---

