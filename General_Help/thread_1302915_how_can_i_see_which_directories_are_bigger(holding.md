---
title: "how can i see which directories are bigger(holding more mbs)?"
date: 2009-10-27
forum: General Help
---

### Post by chriskin on 2009-10-27
i have seen a command some months ago that would check the disk and tell me which folders are the biggest

---

### Post by alphaniner on 2009-10-27
Every directory on the system?  I don't know how to do that.  If you just have one directory in mind you can use:

```
testing@caddywompus:~/bin$ du -sh /usr/*
229M	/usr/bin
2.6M	/usr/games
15M	/usr/include
837M	/usr/lib
12K	/usr/lib32
92K	/usr/lib64
360K	/usr/local
20M	/usr/sbin
878M	/usr/share
364M	/usr/src
4.0K	/usr/X11R6
testing@caddywompus:~/bin
```

there's also the **--max-depth** flag for **du** if you want to search deeper.

---

### Post by chriskin on 2009-10-27
> **alphaniner said:**
> Every directory on the system?  I don't know how to do that.  If you just have one directory in mind you can use:

```
testing@caddywompus:~/bin$ du -sh /usr/*
229M	/usr/bin
2.6M	/usr/games
15M	/usr/include
837M	/usr/lib
12K	/usr/lib32
92K	/usr/lib64
360K	/usr/local
20M	/usr/sbin
878M	/usr/share
364M	/usr/src
4.0K	/usr/X11R6
testing@caddywompus:~/bin
```

there's also the **--max-depth** flag for **du** if you want to search deeper.

thank you , this one seems to work for what i wanted :)

---

### Post by konqueror7 on 2009-10-27
the command above is suffice enough, but may take too long for the whole directory...have you tried using the Disk Analzer instead?

---

### Post by chriskin on 2009-10-27
> **konqueror7 said:**
> the command above is suffice enough, but may take too long for the whole directory...have you tried using the Disk Analzer instead?

it's not needed anymore, but i will give it a try when/if i need this kind of thing again, thank you :)

---

### Post by oldfred on 2009-10-27
If you want all folders or files:

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

---

### Post by chriskin on 2009-10-27
thanks for your answer, my issue is already solved though, as i already said :)

---

