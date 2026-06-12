---
title: "VirtualBox shared HD between different users"
date: 2009-07-12
forum: General Help
---

### Post by Lasombra Demon on 2009-07-12
Hey there!

First post here, first week using Ubuntu, and loving it so far!

A small question. I'm using VirtualBox to virtualize M$'s of evil OS so the rest of my family can use my comp (drones who won't move to Ubuntu yet!), and I want to be able to access the same Virtual HD from my user and from the user I made for my family. Thing is, VirtualBox demands the user who tries to access the Virtual HD to be the owner of the file, so...

What can I do? Can I set two owners to a file? Haven't seen anything like that, and searched and googled everywhere. :P

Thanks!

---

### Post by Kraut~salat on 2009-07-12
does it really have to be the same user or would being in the same group be enough? That would solve the problem easily then. Just create a group and add all users to that group.

Another way may involve su or sudo, which can run programms as different users. Never tried anything like that, but maybe it's a pointer to the right direction.

---

### Post by Lasombra Demon on 2009-07-12
Thanks for your reply!

Tried out the whole 'run as another user' thingy. And it's working! :D

sudo VirtualBox -u invitado (invitado = spanish for Guest, that's my family's account)

Thanks a lot!

---

