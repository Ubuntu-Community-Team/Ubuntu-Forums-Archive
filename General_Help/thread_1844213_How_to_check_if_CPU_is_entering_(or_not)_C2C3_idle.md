---
title: "How to check if CPU is entering (or not) C2/C3 idle state?"
date: 2011-09-14
forum: General Help
---

### Post by Governa on 2011-09-14
I have a Dell Latitude D620 laptop running 11.04 . I feel that the machine gets a little bit too hot underneath when running nothing at all.

Question: Is there any way to check if the CPU is by any chance not entering C2/C3 idle state?

---

### Post by Governa on 2011-09-15
*shameless bump*

---

### Post by wt8008 on 2011-09-15
Take a look at powertop, it is in the repositories. It shows the percentage of time your CPU is in the various C states.

[http://en.wikipedia.org/wiki/PowerTOP](http://en.wikipedia.org/wiki/PowerTOP)

---

### Post by Governa on 2011-09-15
Perfect, just what I was looking for. Thanks a lot!

For the newbies out there (like me) after installing you need to run it via terminal.

```
sudo powertop
```

---

