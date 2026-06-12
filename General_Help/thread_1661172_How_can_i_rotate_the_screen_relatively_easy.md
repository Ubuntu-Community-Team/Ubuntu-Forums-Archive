---
title: "How can i rotate the screen relatively easy"
date: 2011-01-06
forum: General Help
---

### Post by a quarter past seven on 2011-01-06
Is their a way i can rotate the screen back and fourth on my netbook so that i can read books on it easier, ive seen ways of doing it where you had to type code into the terminal but that went over my head, is their an easier way of doing it or an app i could use or something,

thanks

---

### Post by realzippy on 2011-01-06
Which netbook/graphics device/driver?

---

### Post by realzippy on 2011-01-06
Anyway,you can try this:

Open a terminal,type
```
xrandr -o left
```

Works?
To return:
```
xrandr -o normal
```


If this works,you can create a starter on the Desktop/Panel,so 1 click will do this.

---

### Post by Dans564 on 2011-01-06
system ---> preferences ---> Monitors ---> screen rotation

Hope this helps

---

### Post by realzippy on 2011-01-06
> **Dans564 said:**
> system ---> preferences ---> Monitors ---> screen rotation

Hope this helps

That needs 6 clicks...

---

### Post by megabyte1234 on 2011-01-06
Go to System > Preferences > Screens, then click the checkbox "Show screens in panel." A screen icon will appear on your panel, and stay there if you reboot. Left-click it and you can rotate your screen in the pop-up.

---

### Post by a quarter past seven on 2011-01-06
> **realzippy said:**
> Anyway,you can try this:

Open a terminal,type
```
xrandr -o left
```Works?
To return:
```
xrandr -o normal
```
If this works,you can create a starter on the Desktop/Panel,so 1 click will do this.


thanks for the answers, this worked best for me becuase i couldent find any monitor or screen button in system preferences,

thanks for your help

---

