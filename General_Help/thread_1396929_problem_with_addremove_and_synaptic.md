---
title: "problem with add/remove and synaptic"
date: 2010-02-02
forum: General Help
---

### Post by aviramof on 2010-02-02
i don't know why it a new linux installion and i didn't do much except what i saw in the thread i wrote here
but when i tried to add url support it was writen there to enter add remove and to install something 
i tried to do that and all of a sudden i get this messege the search for install and available application fail 
any way i need to use this command in synaptic dpkg --configure -a but i can't it said i need superuser 
priviliges when i'm the sole user in this computer so why don't i have superuser priviliges and how can 
i get them?

thanks in advance.

---

### Post by wilee-nilee on 2010-02-02
> **aviramof said:**
> i don't know why it a new linux installion and i didn't do much except what i saw in the thread i wrote here
but when i tried to add url support it was writen there to enter add remove and to install something 
i tried to do that and all of a sudden i get this messege the search for install and available application fail 
any way i need to use this command in synaptic dpkg --configure -a but i can't it said i need superuser 
priviliges when i'm the sole user in this computer so why don't i have superuser priviliges and how can 
i get them?

thanks in advance.

Run in the terminal,
sudo dpkg --configure -a
the sudo gives you superuser priv. Just input password when asked it wont show in terminal when typing, but is there.

---

### Post by aviramof on 2010-02-02
ok thank you very after playing with it a little it look like broken pacage of java with this guide:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

i'll to reinstall java again in a much later time.

---

