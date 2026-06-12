---
title: "xscreensaver-command: no screensaver is running on display :0.0"
date: 2010-08-21
forum: General Help
---

### Post by patrick295767 on 2010-08-21
Hello, have you ever tried to type into xterm ? (output of 5-11.1) : 
```
 xscreensaver-command  -lock
xscreensaver-command: no screensaver is running on display :0.0
```


If it is working for you, which version of xscreensaver do you have ?
```
dpkg -l | grep xscreensaver
```

---

### Post by patrick295767 on 2010-09-25
simply run first:


```
screensaver &
```

and lock it :```

 xscreensaver-command  -lock

```
I usually lock with daisy flowers :)

---

