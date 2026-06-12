---
title: "How do I save a customized bash promt???"
date: 2010-02-12
forum: General Help
---

### Post by switch10 on 2010-02-12
So I have been messing with this lately, and I cant figure out how to save it.

This gives me what I want:
```
 export PS1='\u@desktop-\@:\w '
```

I tried saving it here: 
```
 /etc/profile 
```

and here:

```
 /etc/bash.bashrc 
```

The files save just fine, but it does not change my bash promt.  What am I doing wrong??

Thanks

Dave

---

### Post by Bonster on 2010-02-12
I just save it to the home folder

~/.bashrc

---

### Post by switch10 on 2010-02-13
Thats it!  Thanks a lot.

Dave

---

