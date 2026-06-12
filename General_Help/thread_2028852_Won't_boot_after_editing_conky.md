---
title: "Won't boot after editing conky"
date: 2012-07-18
forum: General Help
---

### Post by cyberhood on 2012-07-18
Ok, so I was playing around with my Conky config file and now my computer won't boot into the username/password screen. Don't know if it's Conky related or not, but that was the last change I made to the system before I started having problems.

Using Crunchbang Waldorf (based on Debian 6.0). I'm currently using the live cd.

Thanks in advance for any help.

---

### Post by cyberhood on 2012-07-19
NEW DEVELOPMENT:
OK, so I got it to boot in a shell and I immediately got the following message:

```
/dev/sda1: UNEXPECTED INCONSISTENCY run fsck MANUALLY
(i.e., without -a or - options)
fsck died with exit status 4
failed (code 4)
```

So I ran fsck and everything's ok now.

Thanks again.

---

### Post by Habitual on 2012-07-19
> **cyberhood said:**
> ...Don't know if it's Conky related or not..

not.

---

### Post by cyberhood on 2012-07-19
Computer is working fine now. Seems to be hard drive-file system check related.

---

