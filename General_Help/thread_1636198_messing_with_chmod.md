---
title: "messing with chmod"
date: 2010-12-02
forum: General Help
---

### Post by private_click on 2010-12-02
hi.
i was trying to move xampp's root directory from /opt/lampp/htdocs to /home/private/htdocs (in order to use Ubuntu One) but when i restarted apache i got "permission denied" when i tried to load the index page.so i said to my self...hey..let's chmod
i entered this three commands in terminal:
```

sudo chmod -R 755 /home/private/htdocs
sudo chmod 755 /home/private
sudo chmod 755 /home

```
('private' is my username)

after a couple of seconds everything begun to disapper, shortcuts on my desktop, my wallpaper...all.i even tried to execute another command with sudo but i got a nice error message that said i don't have permissions to execute bla bla.now i can't even log into my user.any ideas (besides reinstalling the whole OS) ?

thanx.

---

### Post by AlphaLexman on 2010-12-02
Why would you choose 'private' as a $USERNAME ?

---

### Post by sisco311 on 2010-12-02
755 are the default permissions for /home and /home/username so I don't see why running **chmod 755** on /home and /home/username caused any problems. 

Anyway, try ro restore the default permissions: [thread]976610[/thread]

---

### Post by private_click on 2010-12-03
> **AlphaLexman said:**
> Why would you choose 'private' as a $USERNAME ?

because that's my nickname, duh :)

thank's again for support sisco, everything is back to normal

---

### Post by sisco311 on 2010-12-03
Cool!

Don't forget to mark this thread as [SOLVED]. At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

