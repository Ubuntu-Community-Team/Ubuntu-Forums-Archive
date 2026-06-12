---
title: "Aufs selective branch writing?"
date: 2010-04-29
forum: General Help
---

### Post by thepolishkid on 2010-04-29
I'm not sure if I am posting this in the right place, but here goes.

I have a dell mini 10v netbook running ubuntu 9.10 x32 server. I am using a script called rootaufs to erase my filesystem changes every reboot. I was wondering if anyone knew whether it was possible to create a union mount using aufs in which I would have two rw branches and the OS on a ro branch.

The two read write branches would be separated in such a way that all writes made by three specific users go to branch one and all writes made by everything else on the system go to branch two. Is this possible?

Thanks in advance,
Matt

---

