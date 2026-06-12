---
title: "Not able to FTP between Ubuntu guest and Windows XP Host"
date: 2010-06-28
forum: General Help
---

### Post by charles_pty on 2010-06-28
Hi All

I am using virtualbox 3.2.4 (virtualbox host only network (NAT)) on Windows XP Host and an ubuntu 10.04 guest.

Recently installed vsFTPd on ubuntu guest and I am able to FTP from ubuntu to localhost.  But when I try from the windows host I got an unknown connect error.  I try with anonymous users enabled too.

Could someone please give me an advice on how to proceed or where to look?

thanks in advance

---

### Post by dcstar on 2010-06-28
> **charles_pty said:**
> Hi All

I am using virtualbox 3.2.4 (virtualbox **host only** network (NAT)) on Windows XP Host and an ubuntu 10.04 guest.

Recently installed vsFTPd on ubuntu guest and I am able to FTP from ubuntu to localhost.  But when I try from the windows host I got an unknown connect error.  I try with anonymous users enabled too.

Could someone please give me an advice on how to proceed or where to look?

thanks in advance

**Host Only** is **not** NAT, it is what it says it is.

Use Bridged networking.

---

### Post by charles_pty on 2010-06-28
Thanks very much for the reply, and sorry for my misunderstanding I have been using both (virtualbox and ubuntu virtual machine) for just a month ago.

If Bridge networking will let me FTP between host and guest, I will configure try it, just that as I mentioned I am quite new on this, anybody can give a hand on how to configure this or just let me know a good tutorial about it.

My host IP is public, is there a problem with this and bridge networking?

---

