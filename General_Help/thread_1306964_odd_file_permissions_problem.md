---
title: "odd file permissions problem"
date: 2009-10-30
forum: General Help
---

### Post by Rob Campbell on 2009-10-30
Hi,

I have added a second user to my system and want to share data with them. I have therefore added both of us to the group "users". Stuff isn't working the way I'd expect, however:

Say I create a directory such that it has permissions:
drwxrwxr-x  2 me users 

I can read and write to it and so can the other user. However, if I make:
drwxrwxr-x  2 otheruser users 

Then I /can't/ write to it but the other user can. /etc/groups tells me that I am in group users 

I can't work out what's going on and why this weird asymmetry exists. Does anybody have any ideas?

Rob

---

### Post by Rob Campbell on 2009-10-31
Ah. I had to log in and out. Now it works.

---

