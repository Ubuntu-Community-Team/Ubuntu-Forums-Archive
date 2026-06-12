---
title: "configuring conkyrc"
date: 2009-08-28
forum: General Help
---

### Post by mulligan on 2009-08-28
hi am trying to configure conkyrc. when i do it comes up with this message.

morgan@morgan-desktop:~$ ~./conkyrc
bash: ~./conkyrc: No such file or directory
morgan@morgan-desktop:~$ ~/.conkyrc
bash: /home/morgan/.conkyrc: Permission denied
morgan@morgan-desktop:~$ sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
morgan@morgan-desktop:~$ sudo su
root@morgan-desktop:/home/morgan# 

do you know how to get me in to change my conky config.

thank you.

---

### Post by Tibuda on 2009-08-28
You are trying to execute it like a script. To edit it, open it with your text editor.
```
gedit .conkyrc
```

---

### Post by alindgr1 on 2009-08-28
Try 'gedit .conkyrc' (with no slash)

You can do it either in terminal, or hit Alt-F2 and type it in the box that comes up.  .conkyrc is the name of the file, if it does not exist at that time, it will be created.  Conky does not automatically put a .conkyrc file in your home directory, but if there is one there, that is where it looks.  Also, you may want to check out this thread: 

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

There are MANY on that one, and you can great ideas.  Thats where I got most of my ideas.

---

### Post by mulligan on 2009-08-28
hi i had a look at that link. that was the link i was using to start with. the problem i have now is that when i try to display the conky it is behind the background (i think) it shows on start up but when the background shows it is not there. i have only managed to get one working which was the first one on that link you showed me. do you know how to fix the problem.

thanks for your reply so far. it was very useful.

---

### Post by alindgr1 on 2009-08-28
Can you put your .conkyrc up here so we can check it out?  Thanks

---

### Post by mulligan on 2009-08-28
it's alright i did another one and it works. thanks any way for your time. i appreciate your help.

thank you.

---

