---
title: "Unable to access Windows partitions"
date: 2012-06-08
forum: General Help
---

### Post by wenkey27 on 2012-06-08
Hello,

I had installed Ubuntu 10.04 in Windows 7. I was able to access the partitions created in Windows at that time.

I upgraded from 10.04 to 11.10. Now, I am unable to access the partitions. I get the following message:

[B]Could not find "/media/5EF8AE9AF8AE7047/*********".
Please check the spelling and try again.[/B]

---

### Post by wilee-nilee on 2012-06-08
> **wenkey27 said:**
> Hello,

I had installed Ubuntu 10.04 in Windows 7. I was able to access the partitions created in Windows at that time.

I upgraded from 10.04 to 11.10. Now, I am unable to access the partitions. I get the following message:

[B]Could not find "/media/5EF8AE9AF8AE7047/*********".
Please check the spelling and try again.[/B]

In windows, was this a wubi install?

Did you go from 10.04 straight to 11.10?

If this was a wubi install you might want to contact a mod to include that in the thread header to get it noticed.

---

### Post by wenkey27 on 2012-06-08
Hello wilee-nilee,

Yes. I installed Ubuntu using wubi. 

I upgraded to 11.04 first and then to 11.10.

--
wenkey27

---

### Post by wilee-nilee on 2012-06-08
> **wenkey27 said:**
> Hello wilee-nilee,

Yes. I installed Ubuntu using wubi. 

I upgraded to 11.04 first and then to 11.10.

--
wenkey27

There is really only one helper on the forum that really knows this stuff, so I would get the wubi reference in the header or post a message in the link I will put here to this thread to get their attention. I would help more if I could. ;)

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

This thread was really helpful during a time of specific problems, probably still is but I would just use ot as a refrence to this thread.

---

### Post by wenkey27 on 2012-06-10
I installed the ntfs configuration tool and managed to get the access to Windows partition. The issue is now resolved.

---

### Post by wilee-nilee on 2012-06-10
> **wenkey27 said:**
> I installed the ntfs configuration tool and managed to get the access to Windows partition. The issue is now resolved.

Cool mark the thread solved in the thread tools. ;)

---

### Post by gregzeng on 2012-06-11
> **wenkey27 said:**
> I installed the ntfs configuration tool and managed to get the access to Windows partition. The issue is now resolved.

Did all the same as above.  Only solved it by doing the equivalent to "chkdsk /f".  Or dual-boot in Win7, "Tool-Fix disk".

---

