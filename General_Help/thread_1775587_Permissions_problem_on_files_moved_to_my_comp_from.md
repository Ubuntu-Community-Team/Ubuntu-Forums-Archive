---
title: "Permissions problem on files moved to my comp from smb share."
date: 2011-06-04
forum: General Help
---

### Post by detroit/zero on 2011-06-04
I have Ubuntu 10.10 running here and a Windows 7 desktop. I'm using samba to share files and folders. I have full read/write access to the 7 box, and vice versa. However, whenever a user of the 7 box drops a file on my Desktop, for example (it could be any of my shared directories), it always has a padlock on it and I have to chown it before I can move or delete it.

Can anyone tell me how to get myself permanent ownership of these files? I'm pretty sure I had this problem once before, and it was an issue of adding myself to a particular group, but I forget.

---

### Post by papibe on 2011-06-04
Probably they are accessing the share without user authentication, and that's mean that they are mapped to a predefined user. By default that user is 'nobody'.

In order to change that to, let's say your user, use the 'guest account' option in the /etc/samba/smb.conf:
```
$ gksudo gedit /etc/samba/smb.conf
```
Add a line like this to your share:
```
 guest account = youruser
```
Then restart samba:
```
$ sudo service smbd restart
```
Hope it helps.

---

### Post by mikewhatever on 2011-06-05
Here is a somewhat similar problem that's been resolved to the OP's satisfaction.
[http://ubuntuforums.org/showthread.php?t=1774670](http://ubuntuforums.org/showthread.php?t=1774670)

---

### Post by detroit/zero on 2011-06-05
> **papibe said:**
> Probably they are accessing the share without user authentication, and that's mean that they are mapped to a predefined user. By default that user is 'nobody'.

In order to change that to, let's say your user, use the 'guest account' option in the /etc/samba/smb.conf:
```
$ gksudo gedit /etc/samba/smb.conf
```Add a line like this to your share:
```
 guest account = youruser
```Then restart samba:
```
$ sudo service smbd restart
```Hope it helps.

I had an option *security = share* as opposed to *security = user* under, I believe, the Authentication heading. That was supposed to keep all this from happening in the first place, if I remember what I read those many, many moons ago.

In any event, I changed it to *security = user* and added the *force user = myname* as you suggested and it works like a charm.

If it didn't, I was prepared to just add myself to the nobody group, as was first suggested in the thread linked by mikewhatever.

Got it all covered, now, guys. Thanks so much!

---

