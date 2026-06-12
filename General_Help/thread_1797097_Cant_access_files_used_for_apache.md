---
title: "Cant access files used for apache"
date: 2011-07-04
forum: General Help
---

### Post by Zendon on 2011-07-04
Yo,

Sounds a bit odd but I'll try explain.My files I want to use in my apache folder now tell me I dont have permission to access them. When I change the permissions again, they just go back to blocked again.

I have Ubuntu 11.04

---

### Post by gordintoronto on 2011-07-04
I think the files are in /var/www? That's a system folder, and by default, you do not have access.

I think there are three options:
 - change where Apache wants its files,
 - change the ownership of /var/www,
 - use sudo nautilus to move things into /var/www

Then again, I could be wrong.

---

