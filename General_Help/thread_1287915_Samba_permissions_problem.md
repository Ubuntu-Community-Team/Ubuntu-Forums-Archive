---
title: "Samba permissions problem"
date: 2009-10-10
forum: General Help
---

### Post by Skerit on 2009-10-10
Hi everyone,

My backend has users skerit, griet and barabas.
Most files are owned by user barabas and by group users.

Every user is a member of the users group, btw.

I then mount several folders, passing uid as skerit.

And I try to rename a file which belongs to uid barabas and guid users.

Now, with Debian running the backend, this worked without a hitch. I had all the rights I needed, I could rename files, create them, ...

With Ubuntu on the backend, however, I can't do anything. For some reason it does not recognize skerit as being part of the user group, I believe.

Can anyone recognize where this is going wrong?

---

