---
title: "rcsoccersim"
date: 2010-12-21
forum: General Help
---

### Post by smss on 2010-12-21
I install the rcsoccersim by this:
```
$sudo add-apt-repository ppa:gnurubntu/rubuntu
$sudo apt-get update
$sudo apt-get install rcsoccersim
```But for me does not work!

---

### Post by howefield on 2010-12-21
> **smss said:**
> ```
$sudo add-apt-repository ppa:gnurubntu/rubuntu

```

Perhaps you would have better luck with

```
sudo add-apt-repository ppa:gnurubuntu/rubuntu
sudo apt-get update
sudo apt-get install rcsoccersim
``` 

And moved to General Help.

---

### Post by karthick87 on 2010-12-21
Did you get any error on adding the PPA??Because it's 
```
 sudo add-apt-repository ppa:gnurubuntu/rubuntu
```

---

### Post by smss on 2010-12-21
No
 I do not receive an error when I add ppa.
And when I open the program by```
Alt+F2
(and type this =>) rcsoccersim
```
 Does not work for me!

---

### Post by karthick87 on 2010-12-21
Have you installed **rcsoccersim**??

---

### Post by howefield on 2010-12-21
Instead of using Alt + F2, try opening it in a terminal.

What is the output ?

---

### Post by smss on 2010-12-21
I ran rcsoccersim by terminal and saw these errors :```
QGLContext::makeCurrent(): Failed.
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    128 (Uknown extension)
  Minor opcode: 5 (Unknown request)
  Resource id:  0x4200028
```

---

### Post by smss on 2010-12-21
Ok
I understand that in this version of the monitor-14.0.3 has some bugs.
And I understand that I should install monitor-13.
Thanks a lot of all.

---

