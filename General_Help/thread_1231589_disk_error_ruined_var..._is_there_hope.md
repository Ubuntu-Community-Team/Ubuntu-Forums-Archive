---
title: "disk error ruined /var... is there hope?"
date: 2009-08-04
forum: General Help
---

### Post by Xorlium on 2009-08-04
Hi,

So my laptop (Asus G50) has been working fine for about a year, running kubuntu 9.04 x86_64 now.

Today I turned it on and it gave me many errors, and said "stale NFS file handle /var ..." and things like that, and I couldn't do anything. 

So I started in recovery mode and it did a disk check for the root system because it had errors. It told me to do a manual check. So I did, and it fixed many 'inodes' and cleaned stuff. Since I don't know what all that means, I just said yes whenever it asked me a question like "inode 812848148 should be ",," Fix(y)?" (and it asked a few dozen times)

Then I restarted, and it appears everything inside /var is broken. I couldn't even type stuff in grahpical mode. So I restarted in recovery mode again, and now I can't even start apt, because it says "could not open lock file /var/lib/dpkg/lock, no such file or directory". It says the same with many, many things that use /var. Anything I try to do fails, and it always says things like "can not open '/var/lib/mlocate/mlocate.db': No such file or Directory."

Is there anything I can do to save the system? Or will I need to do a full clean up?

I can see the file inside home, so I guess I could somehow try to save my data.

Thanks!

---

### Post by dcstar on 2009-08-05
> **Xorlium said:**
> Hi,

So my laptop (Asus G50) has been working fine for about a year, running kubuntu 9.04 x86_64 now.

Today I turned it on and it gave me many errors, and said "stale NFS file handle /var ..." and things like that, and I couldn't do anything. 

So I started in recovery mode and it did a disk check for the root system because it had errors. It told me to do a manual check. So I did, and it fixed many 'inodes' and cleaned stuff. Since I don't know what all that means, I just said yes whenever it asked me a question like "inode 812848148 should be ",," Fix(y)?" (and it asked a few dozen times)

Then I restarted, and it appears everything inside /var is broken. I couldn't even type stuff in grahpical mode. So I restarted in recovery mode again, and now I can't even start apt, because it says "could not open lock file /var/lib/dpkg/lock, no such file or directory". It says the same with many, many things that use /var. Anything I try to do fails, and it always says things like "can not open '/var/lib/mlocate/mlocate.db': No such file or Directory."

Is there anything I can do to save the system? Or will I need to do a full clean up?

I can see the file inside home, so I guess I could somehow try to save my data.

Thanks!

Boot up off a Live CD, rename your hard disk /var to /var.save (or whatever) and copy the /var off the running system to your hard disk - that might get some functionality back but a reinstall will properly fix everything.

A separate /home will make reinstalls much easier (search out the HOWTOs).

---

