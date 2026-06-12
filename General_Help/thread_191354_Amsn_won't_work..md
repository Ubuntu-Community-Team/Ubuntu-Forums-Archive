---
title: "Amsn won't work."
date: 2006-06-07
forum: General Help
---

### Post by Somenoob on 2006-06-07
I just get this error msg.

```
Segmentation fault
```

---

### Post by panurge77 on 2006-06-07
check this thread:
[http://www.ubuntuforums.org/showthread.php?t=186135](http://www.ubuntuforums.org/showthread.php?t=186135)

---

### Post by krackjack on 2006-06-11
Try this and it should work. No need to remove Tcl8.5. Just get amsn to work with Tcl8.4. Here's how

(open a terminal)
cd /usr/share/amsn
sudo vi amsn
(enter password)
(edit mode)
(change the line) exec wish $0 (to) exec wish8.4 $0
(save file)
Now start amsn from Application > Internet >

I'm guessing this is a good temporary fix until the issue is taken care of in Tcl8.5

KJ out

---

