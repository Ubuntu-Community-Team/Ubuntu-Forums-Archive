---
title: "Catalog problem"
date: 2006-03-20
forum: General Help
---

### Post by lingon on 2006-03-20
Hi all!
I just did a really stupid thing. I deleted my /home/carl (my acount name)
folder! Dont know what i was thinking. I'm usually not very n00bish but this is just unbelivable. So, what do I do now, is there any terminal command to create it again? Thx.
/lingon

---

### Post by gnu2tux on 2006-03-20
yeah,

log into the terminal - it'll complain about not having anything like a home dir, and put you in / instead. That's ok for now.

Become root by doing:

$sudo bash
Password: <your own pwd>

#userdel carl 

(the reason you should delete your account is because if you have deleted all the files from the folder, you can use useradd to re-create the basic files like .bash_profile and such like)

#mkdir /home/carl

creates your home dir again

#useradd -d /home/carl -s /bin/bash carl

this creates your account again.

#chown carl /home/carl -Rf

changes the ownership of /home/carl to you (carl).

Hopefully that should get you going again. All your prefs and such like are all zapped, so they will be back to defaults.

Take care!

Al

---

### Post by lingon on 2006-03-20
Sweet dude! Thanks alot :)

---

