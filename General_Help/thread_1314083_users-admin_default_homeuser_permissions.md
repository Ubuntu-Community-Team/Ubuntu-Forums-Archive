---
title: "users-admin default /home/user permissions"
date: 2009-11-04
forum: General Help
---

### Post by jodgi on 2009-11-04
I'm on edubuntu 8.04.3 which is continually updated.
The system runs as an LTSP server and has about 120 users.

When I use the users-admin tool to make new users the newly created user's home folder gets these permissions: drwxr-xr-x.

I find it strange that others has r and x permissions and I definitely don't want that in our environment.

I've read and searched around without finding any way to get users-admin to change it's default behaviour.

I've set the umask from 022 to 007(:tongue:), that works for general dir and file behaviour, but it didn't affect users-admin.

Anyone in the know on this?

Dagfinn

---

