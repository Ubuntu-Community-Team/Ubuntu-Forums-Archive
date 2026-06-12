---
title: "Mounting GmailFS"
date: 2006-02-23
forum: General Help
---

### Post by yootje on 2006-02-23
I installed gmailfs and type:

sudo mount.gmailfs none /home/name/gmail -o username=name@gmail.com,password=password,fsname=aword

with of course my actual password on password and name on name. But when I press on enter, this message appears: 

Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure

But my password is 100% correct. Does anyone have an idea?

---

### Post by cstudent on 2006-02-23
I haven't used gmailfs, it looks interesting, I might give it a try, but according to the author's website the command is structured like this:

mount -t gmailfs /usr/local/bin/gmailfs.py /path/of/mount/point -o username=gmailuser, password=gmailpass, fsname=zOlRRa 

Your example looks to be missing some components.

---

### Post by yootje on 2006-02-24
When I do it like that, I get:

gmailfs.py:Gmailfs:unnamed mount options: ['rw']
gmailfs.py:Gmailfs:named mount options: {'username': 'name@gmail.com', 'password': 'password', 'fsname': 'word'}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure

---

### Post by bonjun on 2006-02-24
i also post a similar problem [here]("http://ubuntuforums.org/showthread.php?t=134596")

---

