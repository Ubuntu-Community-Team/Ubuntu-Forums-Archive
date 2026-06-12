---
title: "Something like system restore"
date: 2012-06-15
forum: General Help
---

### Post by SreckoMicic on 2012-06-15
I am planning to install CUDA drivers toolkit. Right now I have working nvidia drivers and I am concerned that something might go wrong and mess my system. 
How can I easily revert to previous state, state before installing CUDA drivers? Is there something I can do to revert, like Restore point on Win? Any advises? 

Thank you!

---

### Post by Megaptera on 2012-06-15
There's no system restore in Ubuntu but you could use Clonezilla.
"Clonezilla live is suitable for single machine backup and restore."  [http://clonezilla.org/](http://clonezilla.org/)

or Remastersys. A tool that can be used to do 2 things with an existing Debian,  Ubuntu or derivative installation.

    It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
    It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.
[http://www.remastersys.com/](http://www.remastersys.com/)

---

### Post by SreckoMicic on 2012-06-15
Thanks, I think Clonezilla will work. Remastersys does not take into account propriety drivers, and I need exactly that :D

---

### Post by Megaptera on 2012-06-16
You're welcome!

---

