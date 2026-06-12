---
title: "mercurial workflow &amp; encryption advice needed"
date: 2010-01-22
forum: General Help
---

### Post by ieatchicken on 2010-01-22
I've just started using Mercurial for a novel writing project (just me, no other users), and was hoping for some workflow advice.

I've got two laptops I write on and an account on a CentOS server that I'd like to use for the repository where I pull from one laptop to the next. I've setup/cloned Mercurial repositories on each and things seem to be working well.

But more importantly, I'd like to encrypt the files so no curious admins on the server are able to read them and was wondering what the best way/workflow to do this would be...

I'm doing my writing in PyRoom so there's no built-in encrypt/decrypt function, so I figured maybe I'll just write a bash script that: pulls, decrypts via openssl, launches PyRoom. Then I guess I'd save/exit PyRoom and write another bash script to encrypt via openssl, commit, and push to my repository on the server.

Does this sound decent or can anyone recommend a better way? 

Thanks!

---

