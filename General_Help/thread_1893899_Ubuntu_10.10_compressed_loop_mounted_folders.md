---
title: "Ubuntu 10.10 compressed loop mounted folders"
date: 2011-12-11
forum: General Help
---

### Post by Mahkoe on 2011-12-11
I have 10.10 on my USB stick, I can't stand the school computers without it. I read an article about compressing and loop mounting /usr. I have it all figured out, but the problem is that this system allows the addition, editing, and deleting of *new* files, but it does not allow editing or deleting of the ones in the compressed read-only fs. This is no big deal because I have all the software I want on my USB stick, but I haven't applied this technique permanently because I don't know how often files are edited in /usr.

So, getting to the point, does anyone know how to track which files are *edited* by the user or the system, or does anyone know which files on your filesystem are never edited unless you expressly edit them yourself or do something freaky?

P.S. I'm very aware of lsof and fuser, but if I wanted to track files I would need something that would track files from the startup to shutdown.

---

