---
title: "lost privilleges in my own account"
date: 2011-02-01
forum: General Help
---

### Post by xasapakos on 2011-02-01
I don't know why but i did something and can't be an su in my account. I can't even delete a file from my home folder unless if i sudo it with terminal. This also crashed my sound card (can't update an ICE authority)
If i add another account it s everything normal including sound

Can anyone help me
Thank you very much

---

### Post by tredegar on 2011-02-01
You do not tell us what distro / version you are running. Please advise.

Please open or login to a terminal and tell us the output of the following:
```
groups
who
ls -l /home
```

---

### Post by xasapakos on 2011-02-02
i use 10.4
these was the results..

kostas@toumpano:~$ groups
kostas adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin netdev admin sambashare
kostas@toumpano:~$ who
kostas   tty7         2011-02-02 08:43 (:0)
kostas   pts/0        2011-02-02 08:44 (:0.0)
kostas@toumpano:~$ ls -l /home
total 16
drwxr-xr-x 57 1016 1016 12288 2011-01-02 13:20 kostas
drwxr-xr-x 31 user user  4096 2011-01-31 08:45 user

I meant ICE authority in my first message

---

### Post by Vaphell on 2011-02-02
you have a borked ownership, what's that 1016?
[http://ubuntuforums.org/showthread.php?p=9451345](http://ubuntuforums.org/showthread.php?p=9451345)

i guess you need to run chown on /home/kostas with kostas:kostas as owner:group to fix the problem

```

sudo chown -R kostas:kostas /home/kostas

```

---

