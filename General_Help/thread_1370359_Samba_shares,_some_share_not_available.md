---
title: "Samba shares, some share not available"
date: 2010-01-02
forum: General Help
---

### Post by marquart on 2010-01-02
Hi there

Im trying to set up Samba.

Ive put in two shares in smb.conf

[test1]
	path = /media/sdb/test
	writeable = yes
;	browseable = yes
	valid users = nikolaj

[test2]
	path = /home/nikolaj/Desktop/test2
	writeable = yes
;	browseable = yes
	valid users = nikolaj

They works perfect on other Ubuntus and some XP Pro :-)

But some XP Pro machines and my XBMC live HTPC goes :share not available when trying to access test1. Meanwhile test2 is always works.

The only difference is the path of the share? what am I missing?

Any Ideas

Thx in advance

Nikolaj

---

### Post by marquart on 2010-01-02
It was due to folder permissions

Nikolaj

---

