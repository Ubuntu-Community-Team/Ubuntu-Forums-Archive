---
title: "firefox bugs"
date: 2010-01-29
forum: General Help
---

### Post by scorpio803 on 2010-01-29
i finally got my linux os to recognize my wireless adapter, hooray! But a number of bugs have plauged my internet experience.
-one, from the get go, the back, forward, and history buttons don't work.
-two, after installing flash player, the browser closes whenever i see any flash related content (or just at random sites, can't tell) youtube, facebook, etc. etc.
- in system monitor, only my cd/dvd drives are showing up as filesystems, not my hard drive. So whenever i download something, it says i'm out of room!

-oh and i'm running ubuntu 9.04

---

### Post by Megafag on 2010-01-29
> **scorpio803 said:**
> i finally got my linux os to recognize my wireless adapter, hooray! But a number of bugs have plauged my internet experience.
-one, from the get go, the back, forward, and history buttons don't work.
-two, after installing flash player, the browser closes whenever i see any flash related content (or just at random sites, can't tell) youtube, facebook, etc. etc.
- in system monitor, only my cd/dvd drives are showing up as filesystems, not my hard drive. So whenever i download something, it says i'm out of room!

-oh and i'm running ubuntu 9.04

Try re-installing firefox maybe?

```
sudo apt-get remove firefox
```

then

```
sudo apt-get install firefox
```

---

### Post by lidex on 2010-01-29
You may just need to delete your history:
"Edit>Preferences>Privacy"
For flash issues go here:
[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")
For your HDD, go to a terminal and enter this command
```
sudo fdisk -l
``` (Applications>Accessories>Terminal)
Then post the output in your next post.

---

### Post by lovinglinux on 2010-01-29
> **scorpio803 said:**
> -one, from the get go, the back, forward, and history buttons don't work.

Make a backup of your profile then follow the instructions from the troubleshooting section [of my tutorial](http://lovinglinux.megabyet.net/?page_id=220#Back-and-forward-buttons-are-greyed-out-or-doesn%27t-work-2). Your problem is listed and solved there.

> **scorpio803 said:**
> -two, after installing flash player, the browser closes whenever i see any flash related content (or just at random sites, can't tell) youtube, facebook, etc. etc.

See [Flash Optimization](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section.

---

