---
title: "How to uninstall all of the GUI and start a fresh"
date: 2009-11-10
forum: General Help
---

### Post by connel on 2009-11-10
I have installed Ubuntu 9.10 on my PS3. I would like to use LXDE as my desktop environment. I have installed it along side gnome, how ever now my menu is full of gnome programs ill never use. GDM is also used and but i think LXDE has its own session manager now (at least i think so) :)

So my question is how do i strip back Ubuntu 9.10 to its barebones and then install LXDE on top of it on a PS3?

Sorry if i've posted this in the wrong section btw :)

---

### Post by undecim on 2009-11-10
Just uninstall all the packages you don't need, or you could just install Lubuntu

---

### Post by jnew93 on 2009-11-10
You've got a few options:

1. Backup your home directory and then reinstall with Ubuntu Server. You will boot with a command line, and can then install any packages you want from there. That is the most minimal and functional 9.10. Then, move all your files back.

2. You can attempt a purge from your current install: 

```
sudo aptitude purge gnome gnome-core gnome-destop-environment
```

That may clean up anything GNOME related for you to then install what you wish. Personally I would recommend the reinstall of the server kernel, as it will be much more of the "minimal" you are looking for.

Cheers and good luck! Have fun with that PS3. :p

---

### Post by connel on 2009-11-10
ok thanks for your help!

and yeah will do now gonna go on FIFA 10 quickly ;) lol

---

