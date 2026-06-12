---
title: "Deleted User, need help getting them back"
date: 2012-04-30
forum: General Help
---

### Post by Derek Karpinski on 2012-04-30
I accidentally deleted the system user that comes with ubuntu named 'backup'.  I restored the user by using the 'update-passwd' command which worked great.  But now 'backup' only shows up in /etc/passwd, and not /etc/shadow.

```
derek@home-pc:~$ cat /etc/passwd | grep 'backup'
backup:*:34:34:backup:/var/backups:/bin/sh
```

The asterisk '*' in the second field tells me the password is not in the /etc/shadow file.

And this confirms it:

```
derek@home-pc:~$ sudo cat /etc/shadow | grep 'backup'
derek@home-pc:~$ 
```

I'm super anal, and would like to make things right, however meaningless user 'backup' is.  How do I get that user back to fresh install configuration?

---

### Post by Derek Karpinski on 2012-05-01
Bump.

---

### Post by Derek Karpinski on 2012-05-03
```
sudo pwck -q
```added the missing user 'backup' to /etc/shadow

```
derek@home-pc:~$ cat /etc/passwd | grep 'backup'
backup:x:34:34:backup:/var/backups:/bin/sh
```

```
derek@home-pc:~$ sudo cat /etc/shadow | grep 'backup'
backup:*:15463:0:99999:7:::
```

SOLVED!

---

