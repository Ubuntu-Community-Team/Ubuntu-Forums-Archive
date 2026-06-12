---
title: "error stating file: no such file or directory"
date: 2011-06-09
forum: General Help
---

### Post by misterbreadcrum on 2011-06-09
I'm trying to setup a keyboard-command to open my downloads folder.  Simple enough.
To get things started off I did $ gnome-open /home/user (my name where user is) and it opens my user home directory.  But when I get to adding downloads to the end of it it gives me this:
$ gnome-open /home/user/downloads
Error showing url: Error stating file '/home/User/downloads': No such file or directory

As far as I can tell there is most obviously a downloads directory in my user folder.  I also get this error when trying to open any other home folder, like music, or pictures.  So what gives?

---

### Post by TeoBigusGeekus on 2011-06-09
Linux is case sensitive.
Make your command
```
gnome-open /home/user/Downloads
```
(Notice the capital D in Downloads)

---

### Post by misterbreadcrum on 2011-06-09
*facepalm*
Thanks!

---

### Post by TeoBigusGeekus on 2011-06-09
You're welcome mate!
Don't forget to mark the thread as solved.

---

