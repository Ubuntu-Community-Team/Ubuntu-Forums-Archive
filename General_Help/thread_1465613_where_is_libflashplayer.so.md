---
title: "where is libflashplayer.so?"
date: 2010-04-29
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-04-29
i installed the restricted extras
which includes flash
i wanted to update it to the rc but i cant find the file any one know where it is?
i tried ```
locate libflashplayer.so
```it did not find it
how to i have it update the database the locate command uses?

---

### Post by no2498 on 2010-04-29
i do not know
but you need to make it and save it
same as for skype or any other program that uses v4l any thing
now that the 2 are the same
cheese is to do it but as you see

---

### Post by v1ad on 2010-04-29
hidden folder like .mozilla or something. in console do ls -al and u should see a folder called .mozzilla check  there.

---

### Post by pqwoerituytrueiwoq on 2010-04-29
> **v1ad said:**
> hidden folder like .mozilla or something. in console do ls -al and u should see a folder called .mozzilla check  there.
i mean the location created by the installer in the repositories
i know how to force it to use another flash player like that but that does not work so well on 64 bit i wanted to know where the installer but the one i have so i can update that one

---

### Post by darolu on 2010-04-29
You can find it with:
```
$ find / -name libflashplayer.so
```
Will take a while but if it is in your computer, it will find it.

It won't make it work though, the 64-bits flash player needs to be installed manually; basically you have to go to adobe's site, download the RC version of flash player (64bits), extract and paste in .mozilla; you can follow tutorials like this one: [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

---

### Post by pqwoerituytrueiwoq on 2010-04-29
> **darolu said:**
> You can find it with:
```
$ find / -name libflashplayer.so
```Will take a while but if it is in your computer, it will find it.

It won't make it work though, the 64-bits flash player needs to be installed manually; basically you have to go to adobe's site, download the RC version of flash player (64bits), extract and paste in .mozilla; you can follow tutorials like this one: [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)
i do not want the 64 bit flash 10
i wanted the 10.1Rc2 32bit at least it is full functional
installing the 64bit one is a walk in the park 
remove flash
place the so file in .mozilla\plugins
and you are done

---

