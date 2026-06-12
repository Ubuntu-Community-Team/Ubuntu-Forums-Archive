---
title: "Samba permission problem"
date: 2011-07-06
forum: General Help
---

### Post by wrybread on 2011-07-06
I'm having trouble accessing my samba share from a Windows box. I have a feeling its going to be solved with chmod, but for the life of me I can't figure out the command.

Here's my line in smb.conf

```
[streams2]
	comment = streams2
	read only = no
	locking = no
	path = /media/New1/streams
	guest ok = yes
	writable = yes

```

That directory, /media/New1/streams, is on a USB harddrive, if it matters.

I then chmod 777 /media/New1/streams

This setup works when sharing a folder in my home directory, but not this one.

The "streams" folder appears on the Windows box, but I can't enter it, I get permission denied.

Any tips?

---

### Post by clblanchard on 2011-07-06
I can't recall right off hand, but I believe I had a problem with this before as well.  If I remember right, I used the chown command to take ownership of the directory and then chmod to change permissions.  Maybe someone else has a more elegant solution and can chime in though.

cheers!

---

### Post by wrybread on 2011-07-06
Thank you sir! Problem solved.

I'm not sure exactly which part of this fixed it, but here's all the steps I did:

```
sudo chown -R wrybread /media/New1
chmod 777 /media/New1
chmod 777 /media/New1/streams

```

In the above example, my username is "wrybread".

Also you probably shouldn't use 777 in your chmod command if you're worried about security on that computer.

---

