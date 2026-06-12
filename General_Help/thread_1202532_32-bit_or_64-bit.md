---
title: "32-bit or 64-bit"
date: 2009-07-02
forum: General Help
---

### Post by Inventech on 2009-07-02
How can I check whether I am running 32-bit or 64-bit?
I'm not sure how I forgot.

---

### Post by wojox on 2009-07-02
```
uname -a
```

If its 32bit then in the output it will be i686 GNU/Linux
If it is 64bit then in the output it will be x86 64 GNU/Linux

---

### Post by Inventech on 2009-07-02
Thank you! =D>

---

### Post by WRDN on 2009-07-02
To be more specific:

```
uname -m
```

---

### Post by Inventech on 2009-07-02
> **WRDN said:**
> To be more specific:

```
uname -m
```

```
uname -m
x86_64

```
```
uname -a
Linux ubuntu 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

```

I believe "uname -a" is more specific.

---

### Post by WRDN on 2009-07-02
You asked for the tool to find if he was running a 32bit or 64bit OS.
uname -a provides information about the kernel version, OS and some hardware info if available.
uname -m only tells you if you're running a 32bit or 64bit OS, hence, it is more specific to the question, while uname -a provides more general information.

---

### Post by ghostborg on 2009-07-02
A usefull tool although does not show bit version is System Monitor.
You can install System Monitor to your panel.
Right click on your top panel bar and select Add to Panel.
Scroll down the list and choose System Monitor and click on Add button.
Left click on the new icon and choose the System tab.
If you don't like this right click on icon and select remove from panel.

---

