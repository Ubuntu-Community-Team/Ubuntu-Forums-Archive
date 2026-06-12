---
title: "How to set the Timezone properly?"
date: 2009-08-23
forum: General Help
---

### Post by pauliem on 2009-08-23
Hello,

I have just started using Ubuntu server edition (8.04 LTS), I have successfully managed to work my way through everything that I was trying to achieve but I have a final problem that I am sure is really simple to sort.

I am England, and although I was sure I set the right options the time reported from the "date" command is always an hour out.

After having run "dpkg-reconfigure tzdata" it shows:

Current default timezone: 'Europe/London'
Local time is now:      Sun Aug 23 10:35:05 BST 2009.
Universal Time is now:  Sun Aug 23 09:35:05 UTC 2009.

Right now the output of date shows:

Sun Aug 23 10:37:30 BST 2009

But it is actually only 09:37.  Anyone have any ideas?

The installation is running on top of VMWare ESXi 4.0

---

### Post by slakkie on 2009-08-23
You can change TZ per user or on a system wide basis.

System wide:
$ echo "Europe/Amsterdam" | sudo tee /etc/timezone

User:
export TZ="America/Aruba"

```

cat /etc/timezone; date ; export TZ=America/Aruba ; date ; unset TZ; date
Europe/Amsterdam
Sun Aug 23 10:49:20 CEST 2009
Sun Aug 23 04:49:20 AST 2009
Sun Aug 23 10:49:20 CEST 2009

```

---

### Post by pauliem on 2009-08-23
Thank you.  Sorted.

---

