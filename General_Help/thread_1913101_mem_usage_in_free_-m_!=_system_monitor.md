---
title: "mem usage in free -m != system monitor"
date: 2012-01-21
forum: General Help
---

### Post by ymy on 2012-01-21
Why is that free -m is not equal to system monitor?

Please see the screen shot.
[[IMG]http://img163.imageshack.us/img163/9887/memusage.jpg[/IMG]]("http://imageshack.us/photo/my-images/163/memusage.jpg/")
Thanks

---

### Post by raja.genupula on 2012-01-21
After seeing some time what i have understand is 


raja@raja-desktop:~$ free -m
             total  used    free   shared    buffers     cached
Mem:         1978   1076     902     0         82        590
-/+ buffers/cache:   403     1575
Swap:         5098          0       5098

Total Ram 1978
Free memeory means look at the second line . 403+1575=1978

our system monitor shows that information, its not displaying that cahed memory  , but our free -m command does that . Thats make difference.

---

### Post by ymy on 2012-01-21
> **raja.genupula said:**
> After seeing some time what i have understand is 


raja@raja-desktop:~$ free -m
             total  used    free   shared    buffers     cached
Mem:         1978   1076     902     0         82        590
-/+ buffers/cache:   403     1575
Swap:         5098          0       5098

Total Ram 1978
Free memeory means look at the second line . 403+1575=1978

our system monitor shows that information, its not displaying that cahed memory  , but our free -m command does that . Thats make difference.

Thanks for clearing the confusion.

---

### Post by raja.genupula on 2012-01-22
you are welcome , please mark the thread as solved from thread tools.

---

