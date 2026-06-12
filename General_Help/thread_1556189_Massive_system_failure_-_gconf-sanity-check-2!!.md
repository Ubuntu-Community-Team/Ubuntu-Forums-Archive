---
title: "Massive system failure - gconf-sanity-check-2!!"
date: 2010-08-19
forum: General Help
---

### Post by jimstar79 on 2010-08-19
I'm suffering, as the title describes, from 'Massive System Failure'.

this is the root of my problem: gconf-sanity-check-2 exited with status 256

Last thing i did last night was install Skype. Tried restarting the machine and this is what i get. 

Then, tried to follow a couple of instructions on how to repair it and now all i get is a grey screen with a blinking image. 

Gutted! is there any way to sort this out. Looking at having to reinstall Ubuntu from scratch and lose tons of data!

Any help will be appreciated, 

peace

---

### Post by jimstar79 on 2010-08-19
OMG - problem solved!!!!


found the answer posted here by Xaegis (my Hero!)

     Originally Posted by xaegis  View Post
    I used the same chown and keep getting the message:

   chown: cannot access `/home/$USER/.gvfs': Permission denied

   How do I work around this?
   I just migrated to 9.04 and now it wont accept my permissions.

   Thanks in advance.

   -e

Nevermind I used:
**sudo aptitude reinstall gvfs gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0**

Found over on this page: [http://ubuntuforums.org/showthread.php?t=971110&page=2](http://ubuntuforums.org/showthread.php?t=971110&page=2)

YES, YES, YES!! ):P

---

