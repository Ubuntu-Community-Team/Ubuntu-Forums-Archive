---
title: "Updating Busybox on router...read-only filesystem?"
date: 2010-02-25
forum: General Help
---

### Post by loicloicloicloic on 2010-02-25
Hello everyone,
I am not sure if this is the right section for this question.
I have a Linksys WRT54G with the Tomato firmware on it.
So the system running on the router is Busybox 1.14., which as far as I know is Linux-based.
I want to update the busybox to the newest version, using ipkg which is the only package manager it has installed on it.
So I use # ipkg install [http://ipkg.nslu2-linux.org/feeds/optware/mss/cross/unstable/busy](http://ipkg.nslu2-linux.org/feeds/optware/mss/cross/unstable/busy)
box_1.5.0-1_mipsel.ipk
but at some point it stops and says: 
mkdir: cannot create directory '//opt/usr/': Read-only file system
so what can I do? How can I make the filesystem read-write?
Can anyone help ? That would be really helpful!
Thanks a lot,
Loic

---

### Post by dcstar on 2010-02-25
> **loicloicloicloic said:**
> Hello everyone,
I am not sure if this is the right section for this question.
........

No it isn't.

This is NOT a generic Linux/whatever forum - it is solely for people running **Ubuntu Linux** so other Ubuntu users can assist them - as is stated at the top of the forum.

---

