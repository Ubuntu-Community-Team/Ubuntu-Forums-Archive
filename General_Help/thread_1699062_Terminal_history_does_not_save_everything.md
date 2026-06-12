---
title: "Terminal history does not save everything"
date: 2011-03-03
forum: General Help
---

### Post by damike2k on 2011-03-03
Hi everybody,

the terminal history does not save commands starting with "./"
Any idea?

Thanks :)

---

### Post by damike2k on 2011-03-03
Problem solved :)


vi .bashrc in home/$user:
[PHP]HISTCONTROL=ignoredups:ignorespace
[/PHP]

i typed in commands like " ./blah" - see the space... its ignored by default in .bashrc :)

---

### Post by biozshock on 2011-08-15
Another reason is ~/.bash_history is not writable by your user

---

