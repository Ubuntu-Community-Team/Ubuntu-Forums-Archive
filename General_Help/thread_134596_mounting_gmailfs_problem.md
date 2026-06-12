---
title: "mounting gmailfs problem"
date: 2006-02-22
forum: General Help
---

### Post by bonjun on 2006-02-22
i install gmailfs thru apt-get, then mount my gmailfs, and i got this...

> pc@server:~$ sudo mount.gmailfs none /mnt/gmail -o username=username@gmail.com,password=*******,fsname=zOlRRa pc@server:~$ gmailfs.py:Gmailfs:mountpoint: '/mnt/gmail'
gmailfs.py:Gmailfs:unnamed mount options: []
gmailfs.py:Gmailfs:named mount options: {'username': 'username@gmail.com', 'password': '*******', 'fsname': 'zOlRRa'}
Traceback (most recent call last):
  File "/usr/share/gmailfs/gmailfs.py", line 1117, in ?
    server = Gmailfs()
  File "/usr/share/gmailfs/gmailfs.py", line 603, in __init__
    self.ga.login()
  File "/usr/lib/python2.4/site-packages/libgmail/__init__.py", line 281, in login
    raise GmailLoginFailure
libgmail.GmailLoginFailure


what seems to be the problem,,,
TIA

---

### Post by sanjose on 2006-02-24
* mount -t gmailfs /usr/local/bin/gmailfs.py /path/of/mount/point -o username=gmailuser,password=gmailpass,fsname=zOlRRa *

---

### Post by bonjun on 2006-02-24
thanks for the reply, 

i still got the same problem, bro

---

