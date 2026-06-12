---
title: "Disc Full... Can't Login."
date: 2006-05-14
forum: General Help
---

### Post by ephman on 2006-05-14
hi,

i noticed that my disc was full, i should have over 20gig though???  and so i rebooted, whatever, and now i can't login because i get a message saying that the "gdm can't write because the disc is full"?

any ideas would be great!

ciao!
ephman

---

### Post by az on 2006-05-14
[QUOTE=ephman]hi,

i noticed that my disc was full, i should have over 20gig though???  and so i rebooted, whatever, and now i can't login because i get a message saying that the "gdm can't write because the disc is full"?

any ideas would be great!

ciao!
ephman[/QUOTE]


Is that the exact message or is it something like "no other user should have write access to your home drive..."  In which case you need to change the permissisons of your home drive back to not allow another user write access....

---

### Post by louis_nichols on 2006-05-14
Try loging in console (press ctrl+alt+f1) after a boot and receiving such a message and do a little cleaning. Start with

sudo apt-get clean

to delete debs that you've already installed. And maybe even a

sudo rm -rf /tmp/*

to empty the temporary directory. Then try again.

---

