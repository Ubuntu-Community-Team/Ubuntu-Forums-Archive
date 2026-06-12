---
title: "Samba Share Issues"
date: 2012-03-04
forum: General Help
---

### Post by Muhnamana on 2012-03-04
Frustration with this issue is mounting and I'm fairly new when it comes to Samba and Ubuntu in general but I have 2 users setup on my Ubuntu box, user1 and user2. These same two users are added within Samba as well.

user1 is currently logged in on the machine and has an external hdd mounted.

I have a current share setup within Samba as the following:

[music]
comment = Music
browseable = yes
path = /media/MyPassport2/Music
read only = no
public = yes
guest = yes
create mask = 0777
directory mask = 0777

When connecting to this share from Windows 7, user1 can connect fine. user2 cannot access this share.

Does this have something to do with user1 having the drive mounted? Permissions issue possibly?

Any and all suggestions are welcome. As I said, I'm pretty much stuck.

Thanks!

---

### Post by freebeer on 2012-03-04
Maybe a typo when listing your permissions here, but you show "directory mas**h**" when it should be "directory mas**k**".

The thing to remember about Samba is that it's permissions don't over-ride Linux permissions.  Linux permissions take precedence.  So if the Linux level permissions don't grant access to the share, Samba can't over-ride it.

---

### Post by Muhnamana on 2012-03-04
Yeah that would've been a typo on my part..hahaha.

I have a feeling its a permission issue at the Linux level but I'm not familiar with changing that.

I have run from the terminal the following command: sudo chmod 0777 /media/MyPassport2/Music
but that didn't seem to do anything.

---

