---
title: "I need help using autofs with cifs shares"
date: 2010-05-27
forum: General Help
---

### Post by powerpleb on 2010-05-27
I am attempting to set up autofs on Ubuntu 10.04 so that it can automatically mount cifs shares when wifi is connected. For some reason, it isn't working. 

First of all, I know the share is accessible because doing this works fine:
```
sudo mount.cifs //192.168.0.12/share /cifs -o credentials=/etc/samba/credentials 

```

This is in my /etc/auto.master
```
/cifs /etc/auto.home --timeout=60 --ghost
```

And this is /etc/auto.home
```
share -fstype=cifs,rw,credentials=/etc/samba/credentials ://192.168.0.12/share
```

Yet, when I do *sudo service autofs reload* and navigate to */cifs* and perform *ls* nothing is there.
And if I check with *mount -l* the share isn't reported


Can anyone help me?

---

### Post by powerpleb on 2010-05-27
In case anyone is interested, I solved this myself by changing the permissions of auto.home and auto.master to 0644. I retained permissions for the credentials file as 0600 for security.

---

### Post by cj-tess on 2010-06-09
Indeed it was useful. many thanks

---

### Post by mazao on 2011-07-13
Thanks a lot , It works on natty also. Previously I had a problem with autofs and cifs on Lucid. I did update twice til find your post. You just save my life!

---

### Post by kzeouki on 2012-02-11
I think this thread needs to be tagged, solved my issue as well:popcorn:

Thanks!

---

