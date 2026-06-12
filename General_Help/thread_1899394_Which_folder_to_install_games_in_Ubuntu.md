---
title: "Which folder to install games in Ubuntu"
date: 2011-12-23
forum: General Help
---

### Post by Quatrix on 2011-12-23
Where do people typically install stand-alone games that don't come from a repository?  I used sudo to put a couple in /bin, but I'm sure that's not how it's supposed to be done.  Archive Manager (without root) didn't have permissions to put anything in /usr/bin or /usr/games either.

---

### Post by mike555 on 2011-12-23
if your the only user of these games you might want to put them in your /home folder so not to need permissions..

---

### Post by crashed111 on 2011-12-23
/usr/local/games is another but I believe to write there you need to be root. 

I think unless you want to install as root you either need to put them in your home folder (or /tmp ;) )

---

### Post by boast on 2011-12-23
maybe [/opt](http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html) ?

---

### Post by audiomick on 2011-12-23
Put it in your /home/user folder. If you want to be really neat, create a folder in your /home/user just for games you have installed. Then you will also be able to find them all easily. ;)

---

### Post by collisionystm on 2011-12-23
> **boast said:**
> maybe [/opt](http://www.linuxtopia.org/online_books/linux_beginner_books/linux_filesystem/opt.html) ?

yeah /opt or your /home

/opt because its already empty and ready for you

---

### Post by Quatrix on 2011-12-24
I need root permission to /opt too, so I stuck them in /home/______/bin, as strange as that seems to me.  But I'm the only user and I guess it doesn't matter.  Thanks.

---

### Post by Quatrix on 2011-12-25
For what it's worth, I looked inside the Super Meat Boy archive, and it has the binaries under /usr/local/games with some additional stuff in /usr/share/.

---

