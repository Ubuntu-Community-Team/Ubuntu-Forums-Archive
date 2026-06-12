---
title: "not able to copy file in /usr/bin"
date: 2010-09-02
forum: General Help
---

### Post by nishant29 on 2010-09-02
hi..i am new to ubuntu 

i have to copy file from download folder to /usr/bin
when i right click on it and select copy option and in /usr/bin the paste option is not coming.

---

### Post by Autodidact on 2010-09-02
You do not have sufficient privileges to copy files.

Open terminal (Applications menu -> Accessories -> Terminal).

1. Type: "sudo chmod 77 /usr/bin/" (without the quotes)
2. Hit enter
3. Enter your password
4. Hit enter again

Now you should have sufficient privileges to copy files to /usr/bin/.

---

### Post by silverglade00 on 2010-09-02
You need elevated privileges to copy into /usr/bin. You can type into a terminal "gksudo nautilus" and then copy and paste the file within that window.

---

### Post by nishant29 on 2010-09-02
:popcorn: thank you

---

