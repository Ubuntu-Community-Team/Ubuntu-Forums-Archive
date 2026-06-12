---
title: "Synaptic does not recognize my password &amp; Add/remove programs not showing up"
date: 2010-02-03
forum: General Help
---

### Post by octaedro7 on 2010-02-03
Hi pals,
I've just did a fresh install of Xubuntu 9.10 x86 in a 4 gig pendrive.
Just one ext4 partition for / and /home and a swap partition. Only one user created during installation.
Everything's fine so far except for two things:

-If I launch synaptic from the start menu, it asks for my password which I type in or even copy-paste to be sure. Strangely it always comes back saying incorrect password. If I open a terminal and call "sudo synaptic" and type in my password when prompted, the application shows up fine. Again if I do the same via the Run dialog (alt+F2), that is "sudo synaptic", nothing comes up. If I just type "synaptic", a pop up says that as a user I won't be able to install anything and blah-blah, and the application displays properly.

-When I launch Add/Remove programs from the start menu it simply doesn't show up.

Do you guys have a clue of what's happening?


Thanks in advance

---

### Post by shreepads on 2010-02-03
Silly question, do you have separate admin and user logins? If yes, are you logged in to the right one?

He he, come to think of it, seems like a downright stupid question now!

---

### Post by rnerwein on 2010-02-03
> **shreepads said:**
> Silly question, do you have separate admin and user logins? If yes, are you logged in to the right one?

He he, come to think of it, seems like a downright stupid question now!

hi
there are no stupid questions only stupid answers !

---

### Post by octaedro7 on 2010-02-03
It's not a stupid question except that in the description of my problem I stated that _only one_ user was created when installing.

The thing got worse currently. I installed the Linux-RT kernel and now when trying to login, after entering my password it sort of tries to log me in but then it takes me back to the very same login screen. It's not because of an incorrect password, cause in that situation it states it in red letters. This is more like it cannot pass the authentication routine.
In one of my previous installation attempts, same combination Xubuntu Karmic + RT kernel, I ended in the same place.
I guess it's a bug.

---

### Post by jken146 on 2010-02-03
In the alt+F2 run box, you need to type *gksudo synaptic* so that the GUI password prompt comes up.

---

