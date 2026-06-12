---
title: "Won't let me log in."
date: 2010-08-28
forum: General Help
---

### Post by Sspankyy on 2010-08-28
I have an almost fresh install of Lucid, <updated and added a few "Necessary" programs> and I am unable to log in.  When I attempt to log in, <select my name and enter password>, the screen goes black and reloads the login screen.

The same thing happened a while ago when I put it on as a dual boot with Karmic, but I didn't care at the time because I just kept logging into Karmic.

I'm running a Dell Inspiron B130.

---

### Post by gdawg on 2010-08-29
Hi. Have you tried to log-in using the terminal window (Ctrl-Alt-F1)?

---

### Post by Sspankyy on 2010-08-29
> **gdawg said:**
> Hi. Have you tried to log-in using the terminal window (Ctrl-Alt-F1)?

Yes, It seems that I can log in there.... 

<Kinda makes me wish I had learned more command line commands..>

---

### Post by Gallows on 2010-08-29
I've seen the login process loop before when some of the permissions on Gnome control files got screwed up.

If you can login at the terminal then you may want to check the permissions on your home directory.

```
ls -al
```

If you wanted to test the theory it could be worth creating a clean home directory to see if that solves it.

```
mv /home/[username] /home/[username.moved]
mkdir /home/[username]
chown [username]:[username] /home/[username]
```

See if that sorts it, if it does and you can live with losing all your settings, login and move your data from /home/[username.moved].

---

### Post by Sspankyy on 2010-08-29
> **Gallows said:**
> If you wanted to test the theory it could be worth creating a clean home directory to see if that solves it.

```
mv /home/[username] /home/[username.moved]
mkdir /home/[username]
chown [username]:[username] /home/[username]
```

See if that sorts it, if it does and you can live with losing all your settings, login and move your data from /home/[username.moved].


OK, I gave that a shot, and now the it just hangs at the default blue background screen when I try to log in....

.

---

### Post by Gallows on 2010-08-29
Hang on, I forgot to tell you that the new directory and the permission change should be done under sudo

```
sudo mkdir /home/[username]
sudo chown [username]:[username] /home/[username]
```

Also, do you have enough free space on the partition your home directory is on? 

```
sudo du -h
```

---

### Post by Sspankyy on 2010-08-29
> **Gallows said:**
> Hang on, I forgot to tell you that the new directory and the permission change should be done under sudo

```
sudo mkdir /home/[username]
sudo chown [username]:[username] /home/[username]
```

Also, do you have enough free space on the partition your home directory is on? 

```
sudo du -h
```


I just made the assumption that all of that had to be done under sudo, and I've got PLENTY of free space right now...

---

### Post by Sspankyy on 2010-08-29
also....

---

### Post by Sspankyy on 2010-09-01
So, I'm still kinda confused about what to do here... any suggestions?   

I'm getting by using Puppy, but I still do prefer Ubuntu for daily  use...

---

### Post by Gallows on 2010-09-01
Why has your ftp user and group got rights over the /home/scott directory?

---

### Post by Sspankyy on 2010-09-01
> **Gallows said:**
> Why has your ftp user and group got rights over the /home/scott directory?


I really have no idea...  I haven't changed anything as far as that goes...  It was only like day 2 of a fresh install when I rebooted and the problem happened...

---

### Post by Sspankyy on 2010-09-05
OK, a bit of a change...

After a weekend of camping, I came back and turned on my computer,    And booted into Ubuntu for the heck of it... Now if I try to log in, It just hangs at the Default Background....

I have made NO changes to anything....

Any Ideas?

I'd just reinstall, but this is the 2nd time that I've had issues logging in, I see no reason I'd have better luck with a 3rd install....

---

### Post by Gallows on 2010-09-08
It looks to me as if your user doesn't have rights over your home directory.

```
sudo chown scott:scott /home/scott
```

---

