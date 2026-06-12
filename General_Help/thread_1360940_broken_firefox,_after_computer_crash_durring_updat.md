---
title: "broken firefox, after computer crash durring update"
date: 2009-12-21
forum: General Help
---

### Post by JohnsShadow on 2009-12-21
i was just chilling out hunting for an image on google
listening to music, with totem and editing a picture for this chick (with gimp) i saw the updater i was barly at 75% cpu and i started the update

then right when it went to install the program(s) the entire computer crashed

now when i launch firefox (from terminal) i get this error, if i launch fire fox from any other way nothing happens

```
johnsshadow@JsX-Evil-PC-Ubuntu:~$ firefox
Could not find compatible GRE between version 1.9.1 and 1.9.1.*.
```

---

### Post by justin.rixx on 2009-12-21
Try installing Google Chrome, it's what I use.

[http://google.com/chrome](http://google.com/chrome)

Justin.Rixx

---

### Post by JohnsShadow on 2009-12-21
well im useing Opera... and i have about 3 more browsers that i couldnt remember by name

but firefox worked yesterday

and it is my favorite and i want it back

i fixed it i figured out it was a problem with Xlrunner 1.9.1 completly removed everything and reinstalled from source

---

### Post by wasteyourammo on 2009-12-21
Have you tried removing and reinstalling firefox?

---

### Post by lovinglinux on 2009-12-21
Close Firefox, then go to "System >> Administration >> Synaptic Package Manager" then search for firefox, right-click on the following packages and mark them for re-installation, then click "Apply":

```
firefox
firefox3-5
firefox3-5-brading
xulruner-1.9.1
```

---

### Post by Crosbie on 2009-12-21
Thanks lovinglinux, I had a similar issue and your recommendations for reinstall did the trick for me. :)

---

### Post by samlown on 2010-01-08
I too had the same problem after a sudden system lock-up and subsequent reboot. Reinstalling xulruner-1.9.1 did the trick.

Thanks lovinglinux et. al.!

---

### Post by powerismine on 2010-02-18
Hello all, 

That fix isn't working for me. I am getting the same error.

"could not find compatible GRE version 1.9.1 and 1.9.1*"

---

### Post by powerismine on 2010-02-18
Quick workaround was to install chrome, but I need to get my girlfriends firefox fixed. Thanks to everyone for any help. :D

---

### Post by powerismine on 2010-02-20
Anyone?

---

### Post by lovinglinux on 2010-02-20
> **powerismine said:**
> Anyone?

Install Firefox 3.6. It doesn't depend on xulrunner package, so it might work.

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by powerismine on 2010-02-20
Yep that seemed to do it, thanks much for the info and help. Now I am not sure what one she will use, she has both options for firefox and chrome.


Thanks again!:D

---

### Post by lovinglinux on 2010-02-20
> **powerismine said:**
> Yep that seemed to do it, thanks much for the info and help. Now I am not sure what one she will use, she has both options for firefox and chrome.


Thanks again!:D

You are welcome.

---

### Post by nos09 on 2010-02-20
why dont you just remove it and then reinstall it. 
by the way i like firefox the most though

---

### Post by lovinglinux on 2010-02-20
> **nos09 said:**
> why dont you just remove it and then reinstall it. 
by the way i like firefox the most though

The OP already done that, I guess.

---

