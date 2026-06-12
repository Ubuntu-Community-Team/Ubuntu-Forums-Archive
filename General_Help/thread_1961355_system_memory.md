---
title: "system memory"
date: 2012-04-19
forum: General Help
---

### Post by winzip on 2012-04-19
What is the command to find system's installed memory in GB format ?

---

### Post by texpat on 2012-04-19
Try

```
free
```

or

```
free -g
```

Get more info with

```
man free
```

---

### Post by winzip on 2012-04-19
If i write free -g it prints.
Total = 15.

If i write free -m it prints.
Total = 16084.

What is the connection between these two number ? Whats the math here ?

---

### Post by HiImTye on 2012-04-19
it's base 2
meaning it doubles every step up
**1** 2 4 **8** 16 32 64 128 256 512 **1024**
a byte is 8 bits and there are 1024 bytes in a kibibyte
1024 is the base unit that memory is broken down into (unless you are talking about manufacturer's GB in which case it is base 10) so all units are divisible by 1024
in otherwords, 1024 B = 1KiB, 1024 KiB = 1 MiB, 1024 MiB = 1 GiB
GiB is the standard for computing measurements of data, as GB is used interchangeably as base 10 and base 2. it creates less confusion having GB only mean the manufacturer's base 10 and GiB meaning the logical unit of base 2

---

### Post by winzip on 2012-04-19
Not understood. Is not it gb to mb conversion ?

---

### Post by HiImTye on 2012-04-19
thats the problem, GB means two very different things, depending on whether you are speaking about manufacturers sizes (1 000 000 000 bytes) and logical size (1 073 741 824 bytes)
this is why GiB is meant to mean the latter

basically, GB had classically always been a logical base 2 unit size, but manufacturers started using the opposite scheme for unit size
it actually was more confusing in the old days when 1.44 MB disks were using a base of '1024' 1000 byte units

---

### Post by codemaniac on 2012-04-19
Hello winzip , 

In a nutshell it is simple maths .
16084 megs = (16084/1024) gigs = 15 gigs .
1 Gigs = 1024 Megs .

---

### Post by winzip on 2012-04-19
Thanks. That helped

---

