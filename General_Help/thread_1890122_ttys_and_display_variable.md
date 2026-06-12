---
title: "ttys and display variable"
date: 2011-12-02
forum: General Help
---

### Post by Van51 on 2011-12-02
Hello,

i would like to know how i can perform the following task :
while i am on tty2 (for instance),  start a program with a gui in tty7. 
I'm thinking it has something to do with the DISPLAY variable, although i haven't managed to find out 
what yet. Or maybe it is something entirely else :oops:

Please tell me how to do this!

Thanks in advance!!

---

### Post by The Cog on 2011-12-03
```
export DISPLAY=:0.0
xeyes
```
You can even do this over ssh. But you have to be logged in with the same user on both the tty and the GUI, or you won't have permission to open the GUI display.

---

