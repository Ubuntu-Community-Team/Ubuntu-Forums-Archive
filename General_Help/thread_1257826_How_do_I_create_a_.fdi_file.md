---
title: "How do I create a .fdi file"
date: 2009-09-04
forum: General Help
---

### Post by Monomaniac on 2009-09-04
I've been trying to install an aiptek drawing tablet following the advice given in a howto which quite blithely tells me to create a .fdi file in the HAL folder.

I've had no problem finding the folder but don't have a clue how to create and fill a .fdi file. Can anyone help.....and easy please, I'm pretty much a complete noob.

---

### Post by cariboo on 2009-09-04
Have you tried:

```
sudo touch <filename>.fdi
```

---

### Post by Favux on 2009-09-04
Hi Monomaniac,

Welcome to Ubuntu Forums!

We fooled around with Aiptek .fdi's on this thread:  [http://ubuntuforums.org/showthread.php?t=1191826](http://ubuntuforums.org/showthread.php?t=1191826)  There might be some useful information there for you.  The "final" version we came up with is in post #50.  Depending on your tablet things will vary of course.

To answer your question you want to enter into a terminal:
```
gksudo gedit /etc/hal/fdi/policy/10-aiptek.fdi
```
gedit (gnome editor/Text Editor) will pop up.  Enter the .fdi contents in it and save and close.  The file 10-aiptek.fdi will be created.

Both sudo and gksudo make you root/super user.  You have to be root to have permission to create or edit system files, ie those not in /home or /home/yourusername/.  You use gksudo with graphical programs like gedit.

Hope this helps.

---

### Post by Monomaniac on 2009-09-06
Many thanks, took a couple of goes but eventually worked like a dream!

---

### Post by Favux on 2009-09-06
Hi Monomaniac,

Great!  Nice job.  Glad you've got the tablet set up.

---

