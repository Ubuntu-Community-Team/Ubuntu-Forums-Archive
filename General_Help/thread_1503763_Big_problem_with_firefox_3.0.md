---
title: "Big problem with firefox 3.0"
date: 2010-06-07
forum: General Help
---

### Post by pieman711 on 2010-06-07
All of a sudden my firefox has stopped working completely. Every time I load it up it looks fine for about 5 seconds then it goes dark and unresponsive. After about a min it comes back up but if you try and go on any website it just crashes again. While it's crashed it makes my whole computer really unstable and all the programs keep crashing and coming back to life and the desktop can be really un-responsive. According to some system monitor icons I have in my top panel one of my CPU cores is being used 100% while firefox is open. When I force it to quit everything else runs fine again. I've tried installing it through synaptic and reinstalling it but it didn't make any difference. When I did reinstall it it kept all my themes and home page so perhaps I didn't manage to get rid of it completely.
In order to type this I had to install SeaMonkey which is working fine as long as firefox isn't running.
Any suggestions?
I'm running 8.10 on a desktop with 2gb of ram and an intel dual core processor and it's been almost trouble free until now...

---

### Post by nemilar on 2010-06-07
Try running it from a terminal and see if it produces any useful debugging output.

Open a terminal and run:
```
firefox
```


Also try it in safe mode.  Open a terminal and run:
```
firefox -safe-mode
```

---

### Post by wojox on 2010-06-07
Why don't you update? 8.10 (Intrepid Ibex) is no longer supported. Security updates ended April 2010.

---

### Post by pieman711 on 2010-06-07
I'm definitely going to update soon, I'm currently facing some pretty heafty exams so didn't want the hassle before then. As soon as they're over I'll go for it.
Running in safe mode didn't help and it hasn't given any errors in the terminal. Is there anywhere I can find a log of the errors?

All I got was

pieman@pieman-desktop:~$ firefox -safe-mode
Killed
pieman@pieman-desktop:~$

---

### Post by Irony on 2010-06-07
Save your bookmarks then close firefox and rename your ~/.mozilla folder to ~/.mozilla1 then start firefox.

If it works then something in your ~/.mozilla folder was the problem.

---

### Post by pieman711 on 2010-06-07
That's done it thanks :)
I haven't changed anything recently so I've no idea what could have upset it all of a sudden. Oh well it's back to normal now. 

Thanks a lot everyone :)

---

