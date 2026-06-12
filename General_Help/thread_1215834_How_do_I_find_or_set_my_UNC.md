---
title: "How do I find or set my UNC?"
date: 2009-07-17
forum: General Help
---

### Post by Luksion Knight on 2009-07-17
I want to be able to access my ubuntu shares using a windows CE based device. It has no network browser so I have to use UNC and type the name into the file explorer as per this [tutorial]("http://www.hpcfactor.com/support/cesd/c/0006.asp")

How do I find or change my computer's UNC name?

---

### Post by blueridgedog on 2009-07-17
Try the command

```
smbtree
```

From your Ubuntu box, for more information:

```
man smbtree
```

You can substiture your IP address for the machine name in the UNC so \\mymachine\myshare can become \\192.168.1.20\myshare for example.

---

### Post by t4thfavor on 2009-07-17
From Windows, your unc will look like this "\\ServerNameOrIpaddress\share"

---

