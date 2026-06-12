---
title: "File search index build"
date: 2010-11-07
forum: General Help
---

### Post by AkiraBergman on 2010-11-07
I noticed that Ubuntu takes some time in building the file search index. It seems to do it overnight while my PC is powered down :))

Is there a way to build the index by a command so that I could do searches whenever I wanted, specially immediately after installing a new program?

---

### Post by cipherboy_loc on 2010-11-07
Are you talking about the Nautilus file search index, or apt-xapian-index, which is used by Synaptic and other programs when searching packages?


Thanks,
Cipherboy

---

### Post by AkiraBergman on 2010-11-07
I am talking about the utility on the upper-left system tray;

Places-Search for files...

---

### Post by cipherboy_loc on 2010-11-08
From the help text:

> Search for Files uses the find, grep, and locate UNIX commands.  By default, when performing a basic search Search for Files first uses the locate command, and then uses the slower but more thorough find command.


After looking around in the man pages of find and grep, I found:

1) Find does not use a database (I think). If there is one, I cannot find it. ;)
2) Locate uses a database, and it is located in /var/lib/mlocate/mlocate.db
3) To update the locate database, use "sudo updatedb.mlocate" without the quotes.




Cipherboy

---

### Post by AkiraBergman on 2010-11-08
Great, thanks. I should have been as diligent as you.

---

