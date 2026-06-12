---
title: "OpenOffice Slow"
date: 2010-07-26
forum: General Help
---

### Post by malel on 2010-07-26
I have OpenOffice 3.2 installed on Ubuntu 10.04 but it is so slow when opening any document and when saving documents that I would like to go back to an older version of OO. Can someone help with advice as to how I can do this. There was never any trouble with older versions of OO. Thank you in advance

---

### Post by DeMus on 2010-07-26
> **malel said:**
> I have OpenOffice 3.2 installed on Ubuntu 10.04 but it is so slow when opening any document and when saving documents that I would like to go back to an older version of OO. Can someone help with advice as to how I can do this. There was never any trouble with older versions of OO. Thank you in advance

Before you do that, try this:

Open Writer
Open menu Tools --> Options.
In the left column look for Java, in the right field de-select the tick-box saying to use a Java runtime environment.
This should make it faster.

---

### Post by malel on 2010-07-26
Thank you DeMus . I switched that off earlier but it still makes no difference. It is still very slow to load any documents and also saving any document. cheers

---

### Post by Hagar Delest on 2010-07-26
Better keep JRE anyway, OOo needs it for some feature (especially wizards).

First try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If no change, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by hawthornso23 on 2010-07-26
I don't think it has anything to do with the JRE. I have the same problem (very slow to open - everything greys out). When openoffice does this to me I see the following showing up in dmesg

```

[12324.377826] soffice.bin[4289]: segfault at 7ffd2dcc9ed9 ip 00007ffd2dcc9ed9 sp 00007ffd20306bd0 error 14 in libglib-2.0.so.0.2400.1[7ffd2df6a000+db000]

```

It is a segfault = a bug. And the bug doesn't seem to be in the JRE. It seems to be in libglib-2.0.so.0.2400.1.

---

### Post by malel on 2010-07-26
Thanks for your replies everybody. These are things that make Linux so frustrating. I will now go back to an older version.

---

### Post by elarson3 on 2010-08-06
Try this:

Edit the file /etc/hosts (back it up first just in case!) to add a line that says
127.0.0.1 mylaptopname localhost mylaptopname.(none)

where mylaptopname is the name of your laptop.

Or equivalently, execute these commands

sudo su
cp /etc/hosts/ /etc/hosts.backup
echo 127.0.0.1 `hostname` localhost `hostname`.\(none\) >> /etc/hosts
exit

---

### Post by David006 on 2010-08-06
The issue raised here is an 'unwanted feature' (or Bug) in OOo caused when you attempt to open an existing OOo document (thereby starting OOo).  There is an approx. 23 second timeout (with no use of memory or CPU) vainly looking for a lost URL within the document.

example: (under otherwise identical conditions)

Applications >> Office >> OpenOffice.org Word Processor
  (starts in 2.5 seconds)

(double-clicking) on {myfilename}.odt
  (starts in 24.6 seconds)
 

See the following link, for further discussion:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176/comments/11](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/592176/comments/11)

SOLVED (?) by previous post.

---

### Post by worksofcraft on 2010-08-06
running AMD quad core 64 bit here

Starting OpenOfice word processor from apps menu takes under 2 seconds.
Opening LiVES_manual.odt by double clicking takes 47 seconds.

I tried editing /etc/hosts as that article suggests but it made absolutely no difference... still 47 seconds!

edit:
ok sussed it... you need a . in there

127.0.0.1	localhost
127.0.1.1	hostname
127.0.0.1	hostname.localhost hostname.(none)

I didn't touch the IPv6 info that followed

---

### Post by satish_j on 2011-03-29
That /etc/hosts trick also worked for me..
Thanks a lot..:P

---

