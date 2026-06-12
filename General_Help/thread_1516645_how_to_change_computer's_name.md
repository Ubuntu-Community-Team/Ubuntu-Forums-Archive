---
title: "how to change computer's name?"
date: 2010-06-24
forum: General Help
---

### Post by neo_sharky on 2010-06-24
hi all.
 
im new to Ubuntu. can i change the computer's name after install the OS? currently it displays **neosharky - laptop** and i want to change it to **Neo Sharky**. can it be done?

---

### Post by sikander3786 on 2010-06-24
> **neo_sharky said:**
> hi all.
 
im new to Ubuntu. can i change the computer's name after install the OS? currently it displays **neosharky - laptop** and i want to change it to **Neo Sharky**. can it be done?

There are already many threads on the topic.

[http://ubuntuforums.org/showthread.php?t=31852](http://ubuntuforums.org/showthread.php?t=31852)

Type in terminal 

```

sudo gedit /etc/hostname

```

Name your system and reboot.

Simple.

HTH.

---

### Post by efflandt on 2010-06-24
You also need to edit /etc/hosts to your changed computer name.  I don't think you can have a space in a hostname, but you could use a hyphen instead.

---

### Post by neo_sharky on 2010-06-24
many thanks to all of u. i am newbie to Ubuntu ;)

---

