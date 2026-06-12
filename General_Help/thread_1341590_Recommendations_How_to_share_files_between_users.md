---
title: "Recommendations: How to share files between users"
date: 2009-11-29
forum: General Help
---

### Post by ian2112 on 2009-11-29
All,

Looking for some options / ideas on ways to share files between two different users on the same system.  Background: I'd like to share music and photos between two desktop users.

Note: I've been unsuccessful creating a link on one user's desktop, pointing to the other user's "Pictures" folder... despite help from this forum.  However, there must be other ways to do this :-)  I'm all ears...

Thanks,
Ian.

---

### Post by Meskarune on 2009-11-29
I have all of my "global media" on a seperate partition. This partition is mounted in /media which all users can access.

You could also try changing the permissions of the folders you want to share, so all users in the "users" group can access them.

---

### Post by lykwydchykyn on 2009-11-29
I created the directory /home/shared, and set the permissions for global read/write/execute.  I then link the folder back to everyone's home directory.

---

### Post by ian2112 on 2009-11-29
Thx for the ideas... a couple things to try out.

Much appreciated!

Ian.

---

