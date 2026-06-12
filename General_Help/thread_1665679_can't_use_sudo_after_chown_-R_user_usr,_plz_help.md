---
title: "can't use sudo after chown -R user /usr/, plz help"
date: 2011-01-12
forum: General Help
---

### Post by borderblu on 2011-01-12
title says it all. I know, I know, a recursive chown, what was I thinking. It was late. 

I just straight up:

sudo chown -R user /usr/ 


Now I can't `sudo', error is "authentication failure".

---

### Post by sisco311 on 2011-01-12
In theory, you could boot a LiveCD and manually go through every file and directory in /usr and set the proper permissions, but that's very time consuming.

It's much easier and faster to backup your data and reinstall Ubuntu.

---

