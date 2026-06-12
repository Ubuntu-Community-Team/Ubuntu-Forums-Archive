---
title: "multiple drives"
date: 2010-04-22
forum: General Help
---

### Post by k7faq on 2010-04-22
Another Rookie looking for direction...

I have 2 drives. I was hoping to have the primary drive for boot and applications. I want the larger drive to be data storage, i.e. /home

can someone be kind enough to direct me to documentation or at least offer the term I need to search by to restructure?

Thank you.

---

### Post by eMJayy on 2010-04-22
I haven't personally done this myself, but I had this page bookmarked just in case I ever needed to use it. Hope this is what you're looking for. 

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2010-04-23
I used this to move home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

But then I decided to move all data to a data partition, primarily because I wanted the same data in several different installs and you should not share /home:
How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I now have three root partitions, old, current, beta just for testing until I install it. I alternate old & current so I have my previous as a backup & a way to go back and find some setting in case I forgot to move it.

---

