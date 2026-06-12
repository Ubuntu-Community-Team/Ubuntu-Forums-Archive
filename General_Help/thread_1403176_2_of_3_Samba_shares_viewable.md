---
title: "2 of 3 Samba shares viewable"
date: 2010-02-09
forum: General Help
---

### Post by rm06 on 2010-02-09
I have Samba sharing set up on my server (Karmic) on which I've created three shares. Two of them I've had for a while and the third I just added. My wife's computer (XP Home) can view the original two but not the one most recently created.

I simply copied the other share in the smb.conf file and changed the path but it is not seen on her computer. I've restarted the Samba services and even gone so far as to reboot the server, all without effect. I've also run "testparm" and everything checks out fine.

The new share I created (/Share/wife/Music) is actually just a subset of the original (/Share/wife/). I understand this is unnecessary and I've actually made the new directory of the original share accessible, I'm just trying to learn from my mistakes and the reason it is not working.

Here are my shares are set up in smb.conf:

```
[Wife's_Stuff]
	comment = Shared Folder
	path = /Share/wife
	read only = No
	create mask = 0755
	guest ok = Yes

[Wife's Music]
	comment = Shared Folder
	path = /Share/wife/Music
	read only = No
	create mask = 0755
	guest ok = Yes

[DVD-ROM Drive]
	comment = DVD Drive
	path = /media/cdrom1
	guest ok = Yes

```

---

### Post by cariboo on 2010-02-10
Do you get any errors when you run:

```
testparm
```

---

