---
title: "Invalid encoding"
date: 2009-08-14
forum: General Help
---

### Post by asai on 2009-08-14
Hi,
I have som trouble with norwegian special caracters.
After som searcing this forum, I have found some tips regarding this issue. But the problem remains.

Heres what I've done so far:
I have some files and folders with special caracters located on a Win XP pc. When I mount a windows share on this computer with smbmount, and then open the folder in nautilus, the filename shows like this: ```
j?ren (Invalid encoding)
```
If I connect this share from a browser, the special caracter displays correctly.
OK, then it's a mount issue, so I changed my mount line in fstab.
First I tried this:
```
//192.168.2.200/share /folder smbfs auto,username=user,password=pass,iocharset=cp850,rw 0 0
```
That didn't work. :(
Then I tried this:
```
//192.168.2.200/share /folder smbfs auto,username=user,password=pass,nls=utf8,rw 0 0
```
Not working. :(

Any suggestions?

---

### Post by asai on 2009-08-17
Solved it.

I put iocharset=utf8 in the fstab line, and all special caracters shows perfectly.

:)

---

### Post by kellemes on 2009-11-22
Thanks, works fine for me..

---

### Post by npss84 on 2010-05-19
Hi

I got the same problem, tried to put the line in fstab, but nothing happens. I got the problem in a partition. How should an example line look like?

---

### Post by asai on 2010-05-23
> **npss84 said:**
> Hi

I got the same problem, tried to put the line in fstab, but nothing happens. I got the problem in a partition. How should an example line look like?

```
//192.168.2.200/share /folder smbfs auto,username=user,password=pass,iocharset=utf8,rw 0 0
```

---

