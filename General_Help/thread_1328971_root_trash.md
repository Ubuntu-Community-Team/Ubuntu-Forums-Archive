---
title: "root trash"
date: 2009-11-16
forum: General Help
---

### Post by groovomata on 2009-11-16
Okay I now I should know the answer to this but... I deleted a game from the /usr/local/games directory. It was pretty large (some gigs) but I can't see the space freed up from my system partition. Where would those files have gone? There must be some root trash directory, but I don't know where it is. 
Does anyone know the answer to this?
THanks,
Erik.

---

### Post by zaphod777 on 2009-11-17
check this location of the user you were logged in as:

user@computer:~$ cd .local/share/Trash
[email]user@computer:~/.local[/email]/share/Trash$ pwd
/home/user/.local/share/Trash
[email]user@computer:~/.local[/email]/share/Trash$

---

### Post by groovomata on 2009-11-17
That's exactly what I was looking for. Thank you Zaphod. Two heads are better than one! 
By the way, to delete files from /root/.local/share/Trash you need to press shift + delete, or they keep coming back.

---

