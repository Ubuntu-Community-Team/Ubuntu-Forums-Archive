---
title: "Turn on Auto Complete and Show File System Path"
date: 2009-08-13
forum: General Help
---

### Post by UltraDangerLord on 2009-08-13
Hello All,

I have set up ubuntu server 9.04 and my first user I created seems to have auto-complete on by using tab and it shows the filesystem path I'm currently on, However when i created other users they do not have these by default

Ex: typing /var/w + tab will show /var/www


How do I turn these on for these users ?

---

### Post by oldos2er on 2009-08-13
To change the defaults for all users, edit /etc/bash.bashrc, and uncomment these lines:

#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

 More info here: [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/)

---

### Post by UltraDangerLord on 2009-08-13
I did that, rebooted the system and still the same thing...

on my other users hitting tab will produce a blank space like normaly hitting tab

---

### Post by oldos2er on 2009-08-13
Did you check each user's .bashrc? I am unsure whether or not a user's .bashrc would override /etc/bash.bashrc.

---

### Post by prem1er on 2009-08-13
After you log into the user type 

```
bash
```

and hit return this will load bash for that user.

---

### Post by UltraDangerLord on 2009-08-13
ahhh I see, thats the problem, is there a way i can load that by default when they login ?

---

