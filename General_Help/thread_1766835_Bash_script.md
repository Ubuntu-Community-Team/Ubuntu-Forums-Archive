---
title: "Bash script"
date: 2011-05-24
forum: General Help
---

### Post by g999b on 2011-05-24
Hi All,

I have a bash script question... I don't know if Ubuntu forum is the right place to ask. If appropriate where (in which section) can I post my question. Thanks.

---

### Post by doas777 on 2011-05-24
> **g999b said:**
> Hi All,

I have a bash script question... I don't know if Ubuntu forum is the right place to ask. If appropriate where (in which section) can I post my question. Thanks.
depends on the script I suppose. there is the Programming Talk section.
how about posting it here?

---

### Post by papibe on 2011-05-24
Sure, go ahead. In the worst case it will be moved to another sub forum.

Regards.

---

### Post by g999b on 2011-05-24
Thanks,

Newbie question I presume...

I'm trying to isolate a process number from 'ps aux'. Let's say i'm trying to isolate the process number of say Chromium.

So here is my input:
ps aux | grep chromium | cut -c11-14

This works fine, and the output is a list of 4 digits processes usually looking like that:
1965
1986
1997
2200
2456

My question is : i would like to isolate only the first process (in my example 1965) and use it as a variable... How can I do that? Thanks for helping.

---

### Post by doas777 on 2011-05-24
the 'head -1' command will return the first line of a file, so:
```
ps aux | grep chromium | cut -c11-14| head -1
```should do ya

[http://www.computing.net/answers/unix/get-the-first-line-from-a-file/7981.html](http://www.computing.net/answers/unix/get-the-first-line-from-a-file/7981.html)

---

### Post by g999b on 2011-05-24
Yup, works fine.

Appreciate! Thanks mate :)

---

