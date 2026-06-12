---
title: "How should I temp remove a HDD?"
date: 2009-12-19
forum: General Help
---

### Post by HomeworkGotInfected on 2009-12-19
Hello,

I need to temporary remove the 2nd HDD in my system, and that HDD is set to be auto-mount at bootup.

My question is that, do I have to change any setting before I take it out?


Thank you.

---

### Post by x33a on 2009-12-19
comment out the fstab entries, just to be sure.

though, even if you don't, i don't think there'll be a problem.

---

### Post by cenzorrll on 2009-12-19
does it contain any system dependent directories (/home, /etc, /var. etc.) or is it the MBR is located?  if not then you should be just fine, you'll most likely get a warning that it can't mount the drive, but beyond that you're fine so long as there isn't anything important on there.  if you don't know then you'll still be ok removing it, you just wouldn't be able to boot.

one way to check would be to find what partitions on the drive are mounted and try to unmount them.  if it's busy (important files and such), then you won't be able to unmount it.

as for the MBR, if you pull out the drive and nothing boots, then it was on the drive and putting it back in won't hurt a thing (just don't try doing it with the computer on)

---

### Post by HomeworkGotInfected on 2009-12-19
Hi x33a & cenzorrll,

Thanks for the replies, as I am stuck. :eek:

I am using that HDD for storage, so it doesn't have any system dependent directories, nor it is used for the MBR.

I guess then I can just temporary take it out, and install it back later.

Good to know before hand about the possible system complain on not being able to mount the HDD. I will comment out the fstab entries to see if it would make the system happy.
------------------

By the way, got one more question to ask.

I have been having issues with the path lengths on my Windows XP, and I am moving my files from it to my Ubuntu storage HDD (which is using ext3). For Windows, I read a safe max path is below 260 char ([link]("http://msdn.microsoft.com/en-us/library/aa365247%28VS.85%29.aspx#maxpath")), anyone knows the length for ext3 (or ext4)?


Thanks.

---

### Post by sisco311 on 2009-12-19
> **HomeworkGotInfected said:**
> 

By the way, got one more question to ask.

I have been having issues with the path lengths on my Windows XP, and I am moving my files from it to my Ubuntu storage HDD (which is using ext3). For Windows, I read a safe max path is below 260 char ([link]("http://msdn.microsoft.com/en-us/library/aa365247%28VS.85%29.aspx#maxpath")), anyone knows the length for ext3 (or ext4)?


Thanks.

There is no limit defined for ext3/ext4 partitions, but by default, Linux has a maximum path name limit of 4096 chars.

---

