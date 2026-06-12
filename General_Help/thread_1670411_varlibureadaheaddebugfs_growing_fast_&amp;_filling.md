---
title: "/var/lib/ureadahead/debugfs growing fast &amp; filling up disk space"
date: 2011-01-18
forum: General Help
---

### Post by Jslh on 2011-01-18
Hi,

While I was looking at df-h

I notice this

none 23G 14G 7.6G 65% /var/lib/ureadahead/debugfs

I tried ls, see nothing, tried vi the "debugfs" noting much too except a few description lines.

1) Is this important?
2) How do I delete it?
3) If it is not importing, How do turn it off?

Please help!

Thanks.

Regards / Joseph

---

### Post by Jslh on 2011-01-21
well, after more research on the Internet and it seems to be a "bug" from Ubuntu 10.04

I checked on my other machines which hold Ubuntu 9.04 and 10.04 but they don't have such issue.

The only differences is both machines were using everything default whereas the machine having such issue was having 2 mappers. The default "root" and owned created "store".

Hm..shall I ignor it or what?

---

### Post by piquat on 2011-01-21
I have the same problem, kind of.  It kind of looks like, to my newbie eyes, that debugfs IS my file system.  I have 5.9G used for Linux and debugfs is exactly 5.9G.  If I have a file system OUTSIDE of debugfs, it must not be very big.  Or, more likely, I just don't understand what's going with this at all.

What the heck am I looking at here?!?!

---

### Post by psusi on 2011-01-21
Like /proc, debugfs is not a disk filesystem, so ignore it.  Also there seems to be a bug where it is unmounted, but not removed from /etc/mtab, so df thinks it is mounted, but when it checks the size, it gets the size for / instead.  If you compare the numbers to /, you will probably find they are the same.

---

### Post by piquat on 2011-01-21
Ahhh, Thanks for the explanation!


System works fine, I'll just ignore it then.  :)

---

### Post by Jslh on 2011-01-21
That was what I'm doing now. Ignore it for the time being! :(

---

