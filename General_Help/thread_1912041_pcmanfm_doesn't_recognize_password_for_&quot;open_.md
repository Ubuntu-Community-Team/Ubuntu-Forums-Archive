---
title: "pcmanfm doesn't recognize password for &quot;open current folder as root&quot;"
date: 2012-01-19
forum: General Help
---

### Post by scubscub on 2012-01-19
Hi, I have Lubuntu 11.10, and a love/hate relationship with pcmanfm.

When I try to open the current folder as root (a cool option!) it asks for the password, but then fails to recognize the correct password!

I'm guessing (from viewing other forums) that this has to do with the settings in the edit-->preferences-->advanced menu, but I do not know what these should be....

Thanks for any help!

---

### Post by Rodney9 on 2012-01-19
Maybe reseting might help, see how here -

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


 For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by SteveDee on 2012-01-20
> **scubscub said:**
> ...I'm guessing...that this has to do with the settings in the edit-->preferences-->advanced menu, but I do not know what these should be...

Has it ever worked? Have you been playing with these settings?

If you use gksu in a terminal with your password, does it work?
Example, in a terminal type:-
```

gksu time-admin

```
...you should be asked for your password in a GUI dialog. If successful, the time-admin GUI should appear with the padlock open.

Your PcManFM settings should look like the attached screen shot...

---

### Post by scubscub on 2012-01-20
> **SteveDee said:**
> Has it ever worked? Have you been playing with these settings?

If you use gksu in a terminal with your password, does it work?


That's a start!  gksu in terminal does not work.  Thanks for suggesting that, I had tried sudo in terminal which worked, but not gksu.

The install is only a few days old, I haven't had a chance to screw up many settings yet. ;)  My pcmanfm settings look just like in the picture.

---

### Post by SteveDee on 2012-01-20
> **scubscub said:**
> ...I had tried sudo in terminal which worked, but not gksu...


Open LXTerminal and type: whereis gksu
You should see something like this:-
```

steve@Steve-Dell-D600:~$ whereis gksu
gksu: /usr/bin/gksu /usr/share/gksu /usr/share/man/man1/gksu.1.gz

```

> 
...I haven't had a chance to screw up many settings yet...

...but you have to break things to find out how they work!

---

### Post by scubscub on 2012-01-20
Alright, whereis gksu results in:

gksu: /usr/bin/gksu /usr/share/gksu /usr/share/man/man1/gksu.1.gz

---

### Post by scubscub on 2012-01-20
So the problem was really with gksu, not pcmanfm.  And the solution is here:

[URL="http://ubuntuforums.org/showthread.php?t=1424299"]
http://ubuntuforums.org/showthread.php?t=1424299[/URL]

Thanks guys!!!

---

