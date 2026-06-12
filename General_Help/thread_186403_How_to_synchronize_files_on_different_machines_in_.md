---
title: "How to synchronize files on different machines in different locations"
date: 2006-06-01
forum: General Help
---

### Post by endokrin on 2006-06-01
Hi,

Let's say I have two computers.  One is running Dapper.  The other is running Windows XP.  They are not in the same location.  They are about 100 miles apart.

I need to find a way to achieve synchronization for certain folders and files.
I searched and found [this thread]("http://ubuntuforums.org/showthread.php?t=170050&highlight=synchronization") but there was no resolution to the problem that I could gather.

Anyone got an idea?

---

### Post by garyng on 2006-06-02
sync as in master slave or two way ? master slave is relatively easy, try rsync.

---

### Post by endokrin on 2006-06-02
Well, I would prefer two way with password protection or some sort of permissions rule set..
Is that possible or is only one way possible?

I'll research rsync.

Thank you.

---

### Post by garyng on 2006-06-02
I am not aware of free two way sync package as that is a pretty complex thing that is very sellable(and hard to implement). The best I know of is Lotus Notes but that is not on file.

---

### Post by stimpsonjcat on 2006-06-02
I use [unison]("http://www.cis.upenn.edu/~bcpierce/unison/") for that (it's in the repos, apt-get unison-gtk for a graphical front-end). it takes a while to configure but works great, even cross-platform!

You need to set up ssh first, and if your computers don't have static IP addresses you probably want to use something like [www.dyndns.com](www.dyndns.com) or [www.no-ip.com](www.no-ip.com)

---

### Post by endokrin on 2006-06-09
gotcha...

as soon as I get my wirless card working................

I'll try this.

Thank you!

---

