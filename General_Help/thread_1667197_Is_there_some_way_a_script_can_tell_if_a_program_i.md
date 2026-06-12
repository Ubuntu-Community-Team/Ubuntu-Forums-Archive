---
title: "Is there some way a script can tell if a program is running?"
date: 2011-01-14
forum: General Help
---

### Post by canam101 on 2011-01-14
Is there a file that can be opened and a program name searched for? If it is there, the program is running, else it is not.

Something like that?

I have a program that stops periodically. If I could run a script every 30 minutes or so to check the hypothetical file, it could re-start the program if the program had stopped running.

---

### Post by Gillingham on 2011-01-14
Well you can use ps to find details of a current process, so you can use that.  But you may find there is an easier mechanism to restart your program.  I used a program called monit to restart mythtv when I went through a stage of having a lot of problem with it quiting on me.

---

### Post by hawkmage on 2011-01-14
Here is a link to the duplicate of this post where there are more responses: [http://ubuntuforums.org/showthread.php?t=1667189](http://ubuntuforums.org/showthread.php?t=1667189)

---

