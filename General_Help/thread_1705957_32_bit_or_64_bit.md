---
title: "32 bit or 64 bit ?"
date: 2011-03-13
forum: General Help
---

### Post by peter27 on 2011-03-13
Hi,


How can one check if an ubuntu installation is 32 or 64 bit ?

Thanks in advance.

---

### Post by hai2lp on 2011-03-13
go to terminal and run this command

```
uname -a
```

or 

```
lsb_release -a
```

---

### Post by linuxliam on 2011-03-13
@[hai2lp]("http://ubuntuforums.org/member.php?u=881761")

I tried both of these and can't find any information regarding 32 or 64 bit versions.

@[peter27]("http://ubuntuforums.org/member.php?u=526924")

This link should provide you with all the information you need...

_[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)_

---

### Post by plucky on 2011-03-13
> I tried both of these and can't find any information regarding 32 or 64 bit versions.

uname -a gives

2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 **x86_64** GNU/Linux


**x86_64** is 64 bit,anything else is 32 bit.

---

