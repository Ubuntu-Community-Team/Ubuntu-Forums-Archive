---
title: "how do i read free -m"
date: 2012-08-11
forum: General Help
---

### Post by solitario on 2012-08-11
hello folks.
I found this command to show me how much RAM my system is using, but I don't really understand how to read this. I know what swap is, it's the area where it puts stuff should it run low... I'm especially interested in the difference between used and free and also what buffers means. Any help is appreciated. Thanks.

```
kyle@GX280 ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:           992        670        321          0        142        339
-/+ buffers/cache:        188        803
Swap:         3814          0       3814
```

---

### Post by 2F4U on 2012-08-12
You might want to read through these posts to get a better understanding:

[http://www.computerhope.com/unix/free.htm](http://www.computerhope.com/unix/free.htm)
[http://nilesh-joshi.blogspot.de/2010/04/interpreting-output-of-free-command.html](http://nilesh-joshi.blogspot.de/2010/04/interpreting-output-of-free-command.html)

---

### Post by Cheesemill on 2012-08-12
Another good explanation:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

