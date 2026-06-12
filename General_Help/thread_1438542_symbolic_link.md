---
title: "symbolic link"
date: 2010-03-25
forum: General Help
---

### Post by ub007 on 2010-03-25
Hi,

quick ques,
which command will tell me whether a directory is a symbolic link or not?
if it is a symbolic link, is there another command to show me which directories it is linked to?

Thanks in advance,
David

---

### Post by andrew.46 on 2010-03-25
Hi david,

> **ub007 said:**
> which command will tell me whether a directory is a symbolic link or not? if it is a symbolic link, is there another command to show me which directories it is linked to?

In this example I first create a symbolic link on my Desktop to a directory containg my 1st semester History notes:
```

andrew@skamandros~/Desktop$ **[COLOR="Red"]ln -s /home/andrew/documents/hist324[/COLOR]**
```

Now the simple command ls reveals that it is a shortcut and points to the linked folder:

```
andrew@skamandros~/Desktop$ **[COLOR="Red"]ls -l hist324[/COLOR]**
lrwxrwxrwx 1 andrew users 30 2010-03-25 23:02 hist324 -> /home/andrew/documents/hist324
```

Is that more or less what you were after?

Andrew

---

