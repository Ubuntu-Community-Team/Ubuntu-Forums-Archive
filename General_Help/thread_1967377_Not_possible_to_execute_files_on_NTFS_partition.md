---
title: "Not possible to execute files on NTFS partition"
date: 2012-04-28
forum: General Help
---

### Post by sirbender on 2012-04-28
Hi,

I tried to execute a file on a NTFS partition and it tells me Permission denied.

This is the file I want to execute:
-rwxrwxrwx 1 root root 5064 Jan 17 09:47 mvn*

This is the entry in the /etc/fstab file for the partition:
/dev/sda5                                  /media/Work  ntfs nls=iso8859-1,users,umask=000,user 0  0  

I cannot see why I shouldn't be able to execute files on this partition?

Thanks,
sb

---

### Post by xyzzyman on 2012-04-28
**IGNORE THAT**

jerome1232 caught it.

---

### Post by jerome1232 on 2012-04-28
> **sirbender said:**
> Hi,

I tried to execute a file on a NTFS partition and it tells me Permission denied.

This is the file I want to execute:
-rwxrwxrwx 1 root root 5064 Jan 17 09:47 mvn*

This is the entry in the /etc/fstab file for the partition:
[COLOR="Red"]/dev/sda5                                  /media/Work  ntfs nls=iso8859-1,users,umask=000,user 0  0[/COLOR]  

I cannot see why I shouldn't be able to execute files on this partition?

Thanks,
sb

It's because your mounting it with the users option, which throws in noexec.

Adjust that fstab entry to look like this. (addition in blue)

```
/media/Work  ntfs nls=iso8859-1,users,umask=000,user,[COLOR="RoyalBlue"]exec[/COLOR] 0  0
```

---

### Post by sirbender on 2012-04-28
Thanks a lot!!!

Is there some good tutorial you know where I learn what all those commands in the fstab mean and maybe a little more about mounting, etc.?

Cheers,
sb

---

### Post by jerome1232 on 2012-04-28
There's a write up on the Ubuntu Wiki [HERE]("https://help.ubuntu.com/community/Fstab") It's not all inclusive but it covers the common stuff and gives usage examples. It's seems a bit dated but still relevant.

---

