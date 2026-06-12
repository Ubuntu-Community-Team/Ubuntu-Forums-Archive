---
title: "Problem with gksudo."
date: 2011-05-01
forum: General Help
---

### Post by Charlski on 2011-05-01
Ok, I tried installing Gnome 3 to replace Unity on Ubuntu 11.04. I used the guide in this thread : [http://ubuntuforums.org/showthread.php?t=1742343]("http://ubuntuforums.org/showthread.php?t=1742343"). Two code lines didn't want to work : ```

gksudo apt-get dist-upgrade
gksudo apt-get install gnome-shell
```

They would ask me if I wanted to continue with [Y/n] and I'd type Y, but nothing would happen. I decided to use sudo instead of gksudo, and it worked. After rebooting, I realised I shouldn't have done that since I broke my iceauthority file (could not update bla bla) It's not really a problem since I'm new to Linux and I've been re-installing it non-stop for the past week (I try different things hahaha) and had no data at all on the PC. 

Do you guys know how I can get gksudo to work for these two parts of the code ?

Thanks !

---

### Post by oldos2er on 2011-05-01
'gksudo' is for graphical applications; use 'sudo' for terminal apps like apt-get.

---

### Post by Charlski on 2011-05-01
Ok, but the guide uses gksudo, and with sudo I break my ICEauthority file ? It installed Gnome 3 and all, but I could'nt login.

Thanks for the reply

---

### Post by oldos2er on 2011-05-01
I see you asked this question in the thread you linked to, since I was going to suggest that. All I can think of is that Gnome 3 has changed the behavior of gksudo/sudo in some manner I'm not aware of.

---

