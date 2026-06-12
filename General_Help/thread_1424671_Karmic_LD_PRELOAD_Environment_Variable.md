---
title: "Karmic LD_PRELOAD Environment Variable"
date: 2010-03-08
forum: General Help
---

### Post by pyroninja316 on 2010-03-08
I was really hoping to be able to take care of this in an automated way, but maybe it's not possible.

I'm trying to set a global environment variable LD_PRELOAD so i can use a different memory allocator.  This can be done in a session with export, and i've even had a little success automating the adding of this environment variable with .bashrc.

My problem is that i want it to be a global environment variable; not dependent on what shell i'm in, works in gnome, etc.  I've tried sticking an export command in /etc/profile, any number of . files in my home directory, i even tried setting it in /etc/environment (no export there).  The problem i run into is that it seems Ubuntu is scrubbing out that one variable.  In fact, when i added it to /etc/environment i also added a third randomly-named (yep, profanity-laced) environment variable and sure enough THAT one appeared when i restarted, but not LD_PRELOAD.

Can anyone tell me how to do this?

Thanks,

Cory

---

