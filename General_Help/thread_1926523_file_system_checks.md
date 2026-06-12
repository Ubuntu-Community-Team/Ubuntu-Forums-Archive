---
title: "file system checks"
date: 2012-02-16
forum: General Help
---

### Post by whvw on 2012-02-16
Help! Every few days, the system keeps doing the "file system checks in progress" thing. How can I decrease the frequency of this?

---

### Post by raja.genupula on 2012-02-16
Hi i have got a good link for you which can explain all . 
[http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://embraceubuntu.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

look at that . all the best .

---

### Post by whvw on 2012-02-16
Well... I tried the link, (it was broken) but a site search gave me a sudo command which I cut and pasted into terminal and.... it did nothing. Is there a file someplace that can be edited directly?

---

### Post by redmk2 on 2012-02-16
> **whvw said:**
> Well... I tried the link, (it was broken) but a site search gave me a sudo command which I cut and pasted into terminal and.... it did nothing. Is there a file someplace that can be edited directly?

I assume that you mean that fsck is running every few days.  This is determined by the number of boot up or reboots you are doing.  See ```
man tune2fs
```  Specifically the -c option.

See if [**_[COLOR="DimGray"]this [/COLOR]_**]("http://www.webupd8.org/2009/05/how-to-change-periodic-disk-check-in.html")helps.

---

