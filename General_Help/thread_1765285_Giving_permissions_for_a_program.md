---
title: "Giving permissions for a program"
date: 2011-05-22
forum: General Help
---

### Post by salmontres on 2011-05-22
Hi everyone,

I'm running a program which needs to access some files from my folder '/usr/local/lib/grads'. I have the folder in place, but it's throwing an error when I the program tries to access them. Further, I'm not allowed to look at the folder unless I'm logged in as a super user, so I'm guessing this is the problem that the program is having. How can I give permissions on this folder?

---

### Post by linuxinstalledfromhdd on 2011-05-22
cd ~/mydirectory
chmod 755 *

---

### Post by salmontres on 2011-05-22
Thanks for the quick response!

It wasn't a problem with permissions in the end. I'm still getting the error message. Should the following create a problem: I'm running a program from an external drive which is mounted, and the program requests libraries that are inside my home directory? (I wouldn't make it so awkward, but the program is massive!)

---

### Post by linuxinstalledfromhdd on 2011-05-22
bump

---

### Post by salmontres on 2011-05-22
I just answered my question. It was a silly mistake. For anyone experiencing similar problems, just make sure your environment variables are set 'generally enough.' By that I mean if things are being moved around, don't expect 'cd ..' to take you to the same place every time! Make the path start at a fixed point; for instance, start it at '/usr/local/lib/my/library.'

---

