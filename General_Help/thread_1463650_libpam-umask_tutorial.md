---
title: "libpam-umask tutorial"
date: 2010-04-27
forum: General Help
---

### Post by oshirowanen on 2010-04-27
Dear Community,

Can someone please point me towards a good online tutorial which will help me setup my box properly to use libpam-umask global settings so all new files and folders are created with specific permissions as I do not like the default permissions.

Thanks
Oshiro

---

### Post by QLee on 2010-04-27
[QUOTE=oshirowanen]Dear Community,

Can someone please point me towards a good online tutorial which will help me setup my box properly to use libpam-umask global settings so all new files and folders are created with specific permissions as I do not like the default permissions.

Thanks
Oshiro[/QUOTE]

Since I know nothing about your technical ability and experience I want to apologise if you are a knowledgable user. It may, or may not be a good idea to do what you intend. It would likely be easier for someone to judge that if you mentioned what you don't like about the defaults and specifically what goal you have in mind. Most of the permissions are like they are for a good reason, sometimes it's for accountability.

Edit:There may be a better way to accomplish the goal.

This might be what you are looking for:
[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html)

---

### Post by oshirowanen on 2010-04-27
> **QLee said:**
> Since I know nothing about your technical ability and experience I want to apologise if you are a knowledgable user. It may, or may not be a good idea to do what you intend. It would likely be easier for someone to judge that if you mentioned what you don't like about the defaults and specifically what goal you have in mind. Most of the permissions are like they are for a good reason, sometimes it's for accountability.

Edit:There may be a better way to accomplish the goal.

This might be what you are looking for:
[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_umask.html)

I have been using Linux for some years now, but still consider myself a beginner.  The reason why i want to change the default permissions is because each time a new user is created, this new users files and folders are available for all other users to see.  I then have to manually change the permissions.

---

### Post by oshirowanen on 2010-04-27
Nevermind, worked it out.

Thanks for the link.

---

