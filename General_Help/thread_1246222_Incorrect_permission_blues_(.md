---
title: "Incorrect permission blues :("
date: 2009-08-21
forum: General Help
---

### Post by dragos240 on 2009-08-21
Hi,

I want everyone to know that I did something really dumb. I set root to be the only one to read the root directory. Now only root can login, even in the tty terminal. Hopefully the archforums will help me out here. I wish I could just reset the permissions :(. So the server will be down until I can get this straightened out.

---

### Post by jpeddicord on 2009-08-21
In your root login session:```
chmod 755 /
```ta-da.

---

### Post by dragos240 on 2009-08-21
> **jacobmp92 said:**
> In your root login session:```
chmod 755 /
```ta-da.

Didn't work, but thanks. Although, I am trying:
chmod -R 755 /

---

### Post by Slim Odds on 2009-08-21
> **dragos240 said:**
> Didn't work, but thanks. Although, I am trying:
chmod -R 755 /

That would be a HUGE mistake, don't do it!!!!

---

### Post by decoherence on 2009-08-21
> **dragos240 said:**
> Didn't work, but thanks. Although, I am trying:
chmod -R 755 /

noooooooooooooooooooooo >.<

now it'll be REALLY hard to fix :(

oh, well. curious; what exact command did you use to modify / permissions?

---

### Post by jpeddicord on 2009-08-21
> **dragos240 said:**
> Didn't work, but thanks. Although, I am trying:
chmod -R 755 /

Yikes. You probably don't want to do that to your entire filesystem, as that makes everything readable by everyone, including /etc/shadow and other system files. -R is recursive.

What's the output of: ```
ls -la /
```

---

### Post by dragos240 on 2009-08-21
> **jacobmp92 said:**
> Yikes. You probably don't want to do that to your entire filesystem, as that makes everything readable by everyone, including /etc/shadow and other system files. -R is recursive.

What's the output of: ```
ls -la /
```
total 80
and drwxr-xr-x for almost everything..... whoops.....

media, mnt, lib, etc are the ones that are not affected.

---

### Post by Slim Odds on 2009-08-21
Enjoy your reinstall.

Slow down next time........

---

### Post by dragos240 on 2009-08-21
Sure. But before I do, is there a command that lists the files besides the gnome, X11, and coreutils? The ones I installed after the initial install? That would help?

---

### Post by aldimond on 2009-08-21
"dpkg -l" will list all the packages you've installed, if that helps.  You'll probably want to back-up everything in /etc for reference (that's the big thing I forgot on a re-install once, it was a real pain to try to remember all the changes I'd made in there).

---

### Post by dragos240 on 2009-08-21
This is arch. Not debian.

---

### Post by -grubby on 2009-08-21
```

pacman -Q

```

---

### Post by dragos240 on 2009-08-21
> **-grubby said:**
> ```

pacman -Q

```

Thanks

---

