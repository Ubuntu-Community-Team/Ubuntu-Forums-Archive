---
title: "access to filesystem in 10.04"
date: 2012-04-07
forum: General Help
---

### Post by rcbfour on 2012-04-07
So, I'm a total beginner at Linux, and was trying to move a folder from the desktop to a directory, but it doesn't let me because I don't have the right permissions. I set myself as an admin in people and profiles (or whatever it's called) but it still won't work. Please help.

---

### Post by Gremlinzzz on 2012-04-07
gksu nautilus
type in terminal makes you root:popcorn:

---

### Post by claracc on 2012-04-08
> So, I'm a total beginner at Linux, and was trying to move a folder from the desktop to a directory, but it doesn't let me because I don't have the right permissions. I set myself as an admin in people and profiles (or whatever it's called) but it still won't work. Please help.

What folder do you want to copy to filesystem?. If it is not part of ubuntu file system, I mean user's data (music, video, documents, games,...) it is better in your /home/name_of_user/ folder where you have all permissions to copy it.

If this is not the case you'll have to be root as Gremlinzzz has pointed.

---

