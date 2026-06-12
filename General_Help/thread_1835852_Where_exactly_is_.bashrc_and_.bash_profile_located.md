---
title: "Where exactly is .bashrc and .bash_profile located?"
date: 2011-08-30
forum: General Help
---

### Post by padfootpak on 2011-08-30
I have been trying to learn bash scripting from linuxcommands.com and in one lesson they ask me to edit .bash_profile. They tell me that it will be located at home. but even after 

> 
cd /home
ls


i do not see the file there. 

One more thing. How do i open .bash_profile in pico or gedit?
Will this suffice?

> pico .bash_profile

Or should I leave the dot out?

---

### Post by eentonig on 2011-08-30
Try again with ```
ls -al
```, this will show hidden files as well.

---

