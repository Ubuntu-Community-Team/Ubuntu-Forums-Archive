---
title: "Die touchpad die!"
date: 2011-11-06
forum: General Help
---

### Post by The Thunder Chimp on 2011-11-06
I would like my touchpad to turn off when I'm using a mouse (or disable the touchpad altogether, since I always use a mouse) because it makes the pointer jerk around whenever I type. It changes my tabs and switches the place where I'm entering text. It is a pain.

How can I turn the darn thing off?

There is no such option under  Shut Down>System Settings>Mouse and Touchpad 
(there is no touchpad tab, see picture). ](*,)
I use ubuntu 11.10.

Thanks!

---

### Post by The Thunder Chimp on 2011-11-06
My bad, a program called touchpad indicator settled the problem.

Thanks anyway!

---

### Post by IWantFroyo on 2011-11-06
```
synclient TapButton1=0
```
```
synclient PalmDetect=1
```

Edit- A little late, I suppose.

---

### Post by tulipán on 2011-11-06
look in here: [http://ubuntuforums.org/showthread.php?t=1565149](http://ubuntuforums.org/showthread.php?t=1565149)
i hope you will find the answer :)

---

### Post by rushikesh988 on 2011-11-06
> **IWantFroyo said:**
> ```
synclient TapButton1=0
```
```
synclient PalmDetect=1
```

Edit- A little late, I suppose.
what does syncclient does ??

---

### Post by Habitual on 2011-11-06
Funniest Subject line I've seen here in years.

---

### Post by hansdown on 2011-11-06
> **habitual said:**
> funniest subject line i've seen here in years.

+1.:)

Glad you gpt it fixed, The Thunder Chimp.

---

