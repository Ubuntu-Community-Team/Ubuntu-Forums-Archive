---
title: "Sharing /home and .config files"
date: 2009-08-20
forum: General Help
---

### Post by rootless on 2009-08-20
Hey,I just decided to dual boot Ubuntu with Gentoo. I think I just did something bad-

I have a user on each / with the same name. I just started Firefox, and my bookmarks have been obliterated... I suspect that this is the reason. Is there any way I can have two profiles that share the same .config files and /home and allow them to coexist peacefully?

---

### Post by michy99 on 2009-08-20
Are you trying to share a /home directory between Ubuntu and Gentoo? You should know that Ubuntu starts numbering new users at 1000 and Gentoo may start at some other number. I know some distros start at 500.

---

### Post by rootless on 2009-08-20
O___o

Uh oh. I'll have to do some research into this. The user numbers have to be the same?

---

### Post by ibutho on 2009-08-20
I personally think its not a good idea to share the same home directory between different distros. Anyway, you need to make sure that the user id and group id for your user on both Gentoo and Ubuntu match (most distros start assigning uids and gids for non system user from 500, but Ubuntu starts from 1000). Its not guaranteed that simply having a user with the same uid and gid will make things work perfectly because running different versions of certain software may mess your config files.

---

### Post by rootless on 2009-08-21
What if I want to share my public directory? If I set the uuid and group id is that all I need to do?

---

