---
title: "Disk Cloning Command from terminal"
date: 2009-08-21
forum: General Help
---

### Post by Go_Big_Blue on 2009-08-21
Hello all.

I've been following along on another post, but was hoping someone might have a quick answer for me.

I am trying to copy over byte-by-byte one hdd to another brand new (but larger) hdd.  I am running the 8.04 LiveCD, and I am using the following command:

```

sudo -s
dd if=/dev/sda of=/dev/sdb

```

When I run this command, all I get is a blinking cursor. Is there a tag line that I can add to this command to get a feedback of progress?  Any help would be greatly appreciated.

Oh yeah, one other point.  When I enter the following:

```

sudo -s
dd if=/dev/sda of=/dev/sdb & pid=$! while kill -USR1 $pid; do sleep 1; done

```

I get the following response:

```

bash: syntax error near unexpected token 'do'
```

Any help is greatly appreciated.

---

### Post by rbc on 2009-08-21
[http://madberry.org/2009/02/dd-with-progress-bar-try-dcfldd/](http://madberry.org/2009/02/dd-with-progress-bar-try-dcfldd/)

---

### Post by Go_Big_Blue on 2009-08-23
Thank you.

---

