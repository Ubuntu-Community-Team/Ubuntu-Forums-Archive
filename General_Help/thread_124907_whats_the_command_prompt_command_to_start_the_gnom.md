---
title: "whats the command prompt command to start the gnome login screen?"
date: 2006-02-02
forum: General Help
---

### Post by gamerzl on 2006-02-02
well? read the title

---

### Post by magnusbb on 2006-02-02
The command you are looking for is:

sudo /etc/init.d/gdm restart

---

### Post by gamerzl on 2006-02-02
o ya its not default
kde's was, but that failed, and i want to use the gnome one again

---

### Post by magnusbb on 2006-02-02
You will have to use more words than that, before I am able to understand what you are talking about.

---

### Post by gamerzl on 2006-02-02
i started using ubuntu, and then installed the kde desktop and all that jazz, 
when i went to log back into linux i enabled kde as the default login screen, 
but that failed "the application kdmgreet crashed, and caused the signal (sigsgv or something) and it won't let me login to kde, i want to get the gnome login back to default so i can log back into kde. (i'm able to get back in to gnome, w/startx command) but i want the command to start kde/kdm. (i've also tried clicking system/administration/login screen startup (in gnome) and nothing happens, looks like its gonna run, but then closes randomly. 

does this make any more sense?

---

### Post by gamerzl on 2006-02-02
i also posted the error here [http://www.ubuntuforums.org/showthread.php?t=124701](http://www.ubuntuforums.org/showthread.php?t=124701) but noone replied

---

### Post by chaumurky on 2006-02-02
is **sudo dpkg-reconfigure gdm** what you're looking for?

---

### Post by gamerzl on 2006-02-02
didn't do anything

---

### Post by chaumurky on 2006-02-02
You didn't get a ncurses type config screen? No errors?

---

