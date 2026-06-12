---
title: "Aiglx/Compiz problems..."
date: 2006-06-20
forum: General Help
---

### Post by siriusnova on 2006-06-20
Well i followed the first page howto to the letter here - 
[http://ubuntuforums.org/showthread.php?t=145068&highlight=aiglx](http://ubuntuforums.org/showthread.php?t=145068&highlight=aiglx)

however i have a big problem, after gnome loads the screen turns white. Funny thing is that i can click menus but the ENTIRE screen is white. Also i cant seem to resize windows much at all.

[http://web.umr.edu/~taknnc/Screenshot.png](http://web.umr.edu/~taknnc/Screenshot.png)


is what i get.. any ideas? Im using X.org Radeon driver on a radeon 7500 mobility.

Interestingly enough i can do all the Effects and switch screens with the cube etc.. but it's all white, the windows cant be resized, and the window of an app will not refresh until i hit the resize button (it stays the same size)

---

### Post by olsonar on 2006-06-21
i get a similar problem when my computer comes back from sleep. easiest fix for me is to run these commands:

killall compiz-start
/usr/bin/compiz-start

just use alt + F2 to get the 'run' dialog, and type the command. you could also just kill compiz and switch to metacity with the command:

metacity --replace

---

