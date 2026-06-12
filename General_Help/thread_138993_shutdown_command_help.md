---
title: "shutdown command help"
date: 2006-03-03
forum: General Help
---

### Post by ice60 on 2006-03-03
hi, i want to turn the computer off at 01:00 will this work?

```
shutdown time 01:00
```

thanks

---

### Post by aysiu on 2006-03-03
If you read the manual (```
man shutdown
```) this is what it says about time: > The time argument can have different formats.   First,  it  can  be  an
       absolute time in the format hh:mm, in which hh is the hour (1 or 2 dig&#8208;
       its) and mm is the minute of the hour (in two digits).  Second, it  can
       be  in the format +m, in which m is the number of minutes to wait.  The
       word now is an alias for +0.

I know the generally suggested command is ```
sudo shutdown -h now
``` so maybe it would be ```
sudo shutdown -h 01:00
```

---

### Post by ice60 on 2006-03-03
thanks, aysiu. i did look at the man. i suppose i should just try it and see :rolleyes: i might try 

```
shutdown time +80
```

for 1 hour 20 minutes, that's if i my brain can work out the numbers correctly :mrgreen: i'm going to try one out now. \\:D/

---

### Post by ice60 on 2006-03-03
OK, i admit you were right i seem to be still here, i always get commands wrong first time #-o

BTW, thanks. i just tried it and it works. i stopped the test shutdown with ctrl-c

---

### Post by aysiu on 2006-03-03
Why don't you test out a hard time? So if it's 22:00 where you are, you can make the command ```
sudo shutdown -h 22:05
``` and see if it works. If it does, you can change it to ```
sudo shutdown -h 01:00
```

---

### Post by ice60 on 2006-03-03
it worked perfectly :cool: 

this is the other command i was trying to do. this would shutdown in 5 minutes
```
$ sudo shutdown -h +5
```

---

