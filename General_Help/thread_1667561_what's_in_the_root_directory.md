---
title: "what's in the /root directory?"
date: 2011-01-15
forum: General Help
---

### Post by tjk on 2011-01-15
I've used ubuntu for many years.  I always thought that /root contained other files and directories, but I'm unsure what should be there.  AND, I just did an ls /root/* and got the message "no such command".  Same thing with sudo ls /root/*.  Has something happened to the contents in my /root directory?  If so, is there a way that I can get it back?  And... maybe it's related to this problem that I'm having: [http://ubuntuforums.org/showthread.php?t=1666761](http://ubuntuforums.org/showthread.php?t=1666761)

---

### Post by Copperblade on 2011-01-15
Can you ls in any directory?  What about `which ls` ?

Anyway, /root/ is root's home directory.  Special treatment for a special user...

---

### Post by tjk on 2011-01-15
> **Copperblade said:**
> Can you ls in any directory?  What about `which ls` ?
I had no problems using ls in other directories... tried /,/etc,/home,/boot,/usr and maybe others.

---

### Post by marin123 on 2011-01-15
how about:

```
sudo bash
cd /root
ls
```

maybe you should be root while listing directory contents :)

---

### Post by Dave_L on 2011-01-15
You don't need the "*":

```
sudo ls -al /root
```

You *do* need sudo, since /root is readable only by root:

```
stat /root
```

---

### Post by Zimmer on 2011-01-15
[http://www.linuxnewbieguide.org/content/chapter-11-files-directories-and-linux-filing-system](http://www.linuxnewbieguide.org/content/chapter-11-files-directories-and-linux-filing-system)

Might be of interest to you...

---

