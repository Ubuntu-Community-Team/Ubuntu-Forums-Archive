---
title: "stuck at the login screen!!!!!"
date: 2011-06-28
forum: General Help
---

### Post by evilheart on 2011-06-28
i have Lubuntu 11.04 , now i gets stuck at the login screen , when i enter the login info, it just blinks and open it again , 
i can login normally on the command line interface , sudo is working normally too , i tried running "fix broken packages" from the recovery mode as it worked before , it downloaded about 40 MB , most about codeblocks that i recently installed , but nothing was fixed ,
 
"checking system files" option in the recovery mode did nothing , also the safe mode graphical interface didn't work. it seems the graphical interface of the desktop environment can't start at the first place!! , i don't know , did someone met something like that on Lubuntu before ?

---

### Post by Dooobro on 2011-06-29
I have same problem, I found this [http://ubuntuforums.org/showthread.php?t=1787815&highlight=Can%27t+get+past+lUbuntu+11.4+login+screen](http://ubuntuforums.org/showthread.php?t=1787815&highlight=Can%27t+get+past+lUbuntu+11.4+login+screen)
but it not worked for me. Probably reinstall :(

---

### Post by evilheart on 2011-06-29
> **Dooobro said:**
> I have same problem, I found this [http://ubuntuforums.org/showthread.php?t=1787815&highlight=Can%27t+get+past+lUbuntu+11.4+login+screen](http://ubuntuforums.org/showthread.php?t=1787815&highlight=Can%27t+get+past+lUbuntu+11.4+login+screen)
but it not worked for me. Probably reinstall :(

LOL , that was my thread too !!!! , it seems like a common problem even in previous versions of ubuntu , the graphical desktop manager gdm -is that right??? - fails for some reason , 

i don't want to reinstall Lubuntu , it took a lot of time in the first time , but i may reisntall openbox - that is the gdm here ,right?- , any one knows a script for that?

---

### Post by Habitual on 2011-06-30
```
sudo apt-get --reinstall -f gdm
```

---

### Post by evilheart on 2011-07-01
[http://ubuntuforums.org/showthread.php?t=783479&page=2]("http://ubuntuforums.org/showthread.php?t=783479&page=2")

the method here worked for me

 ```
sudo /etc/init.d/gdm restart
```

---

