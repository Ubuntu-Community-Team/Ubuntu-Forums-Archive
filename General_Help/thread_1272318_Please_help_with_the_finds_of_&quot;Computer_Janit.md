---
title: "Please help with the finds of &quot;Computer Janitor&quot;!"
date: 2009-09-22
forum: General Help
---

### Post by Saurabhdua on 2009-09-22
Hi Guys!

Iam so-so fond of Optimization Tools within Windows that Iam literally missing/finding void those within Ubuntu!

Anyways...I tried my First Hands-on for the 'Computer Janitor'. Here's what I have got to deliberate & that SCARY Warning message putting the entire onus of the probable forthcoming MESS onto a user!

Please refer to the attached image & help me decide if I can really delete these .deb packages?

Thanks!

---

### Post by wojox on 2009-09-22
Yes you can delete those old kernels. To double check open a terminal and type:

```
uname -r
```

That's the kernel your currently using. Ex.

```
wojox@wojox-desktop:~$ uname -r
2.6.28-15-generic
```

---

### Post by NoaHall on 2009-09-22
They are safe to remove, but I wouldn't use Computer Janitor. It tries to remove anything you've installed which is outside of the repo's

---

### Post by Saurabhdua on 2009-09-23
That's exactly what I got in over here:

saurabhdua@saurabhdua-desktop:~$ uname -r
2.6.28-15-generic

So..should I go ahead with the deletion of .deb packages?

---

