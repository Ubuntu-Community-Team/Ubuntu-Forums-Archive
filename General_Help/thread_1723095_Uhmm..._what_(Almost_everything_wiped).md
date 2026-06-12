---
title: "Uhmm... what? (Almost everything wiped)"
date: 2011-04-06
forum: General Help
---

### Post by 23Andrew on 2011-04-06
Ubuntu 10.10 Netbook

So my internet went down. This happens a lot. So I clicked connect again, and it acted like it forgot my WEP key. This happened often too. So I unplugged, went downstairs with my laptop, to get the key, and input it. I entered it wrong (typo) and then Ubuntu froze. This is NOT normal, and has never happened to me before.

So I restarted my computer.

When I logged on, my Wallpaper was missing, (just purple screen) and all of my files were missing. (Well, my Home folder had been set to default, except my "Documents" were left untouched, and another folder was left.)

All of my programs are here, and in the right places, (on the quick launch bar along the left) but everything was default. (Chromium forgot my homepage, passwords, favourites etc... and Empathy forgot everything about me)

Does anybody know what has happened? Or what I should do?

I'm freaking out here, I made no backups or anything.

Even if it's just a "You're screwed," any information is good.

---

### Post by wojox on 2011-04-06
Try a file system check. In the terminal run this:

```
sudo touch /forcefsck
```

```
sudo reboot
```

---

### Post by 23Andrew on 2011-04-06
Tried 

```
sudo touch /forcefsck
```

Nothing happened, went back to 
```
andrew@computer:~$
```

Is this right? Do I reboot now?

---

### Post by wojox on 2011-04-06
> **23Andrew said:**
> Tried 

```
sudo touch /forcefsck
```

Nothing happened, went back to 
```
andrew@computer:~$
```

Is this right? Do I reboot now?

Yes reboot now.

---

### Post by 23Andrew on 2011-04-06
The disc check ran, came up with nothing. Everything still bad.

---

### Post by Joe of loath on 2011-04-06
What are the permissions of your home folder?

```
ls -la ~/
```

---

### Post by 23Andrew on 2011-04-06
I assume it's the first line "." that is the useful one?

```

drwxr-xr-x 37 andrew andrew    4096 2011-04-06 21:45 .
drwxr-xr-x  3 root   root      4096 2010-12-05 16:51 ..

```

---

### Post by ajgreeny on 2011-04-06
How many lines were there?  There should be one for each file and folder in your  home folder or partition (not recursively) including any hidden files and folders.  If they appeared at least you can see that the files are still there.

I suggest you try the following from recovery mode if needed, (which does not need sudo), or from your command line if you are logged in as normal user, (does need sudo).
```
chown -R <username>:username> /home/<username>
chmod -R 755 /home/<username>
```then try logging in again as normal.  Use your username where I show <username> of course.

---

### Post by Thewhistlingwind on 2011-04-06
Honestly, if your stuff is ACTUALLY wiped. (Not hidden/etc but deleted.) Then you could always try a forensic recovery utility like testdisk to get it back. (Never used testdisk myself, so be forewarned that you can probably severely damage your system with this kind of stuff.) What the other users here are asking you to do is run commands to try and determine if your "stuff" is still there but has permissions issues/etc. Normally that's it and you can fix things with a little command line magic, but just in case, that's always an option.

---

