---
title: "how to use unison after manual copy?"
date: 2009-08-17
forum: General Help
---

### Post by buuh83 on 2009-08-17
hi everyone.
i'm trying to set up unison to sync my desktop and laptop. evrything looks fine so far and the sync itself works.

now my problem is, that i have a folder containing a lot of data (music) and it's quite slow copying everything via ssh. so i initially copied the folder manually using my external drive.
but when i now start unison-gtk it gives me a "?" for every file within that folder. is there any way to tell unison to treat all these file as "equal" on both machines so that i dont get the list of all the files at the next run? skipping hasn't this effect.

probably it's just an option i haven't seen/tried so far...

hope i made clear what i wanna know :)

thanks,

buuh

---

### Post by buuh83 on 2009-08-18
ok, now it works fine!

my fault: the files were shown as changed because of different permissions. doing a chmod on one side resolves the "problem"...

---

