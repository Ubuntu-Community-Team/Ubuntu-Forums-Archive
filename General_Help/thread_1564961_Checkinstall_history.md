---
title: "Checkinstall history"
date: 2010-08-31
forum: General Help
---

### Post by Sempfinger on 2010-08-31
Greetings!

I ran into this bug: 
[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/291262]("https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/291262")

I checked that overwrite-local was set to 1.

So I want to delete all python packages that were installed by checkinstall with the /usr prefix.

Now it has been some time since I did this and I dont really remember.

Does anyone using checkinstall know how to spot packages installed via checkinstall? I already checked the FAQ and doc of checkinstall, but no info on this.

Thanks in advance!

---

### Post by Sempfinger on 2010-09-01
memo for myself: Think before you post.

```
dpkg -l | grep checkinstall
```

assuming that one does not change the default package description: "Package created with checkinstall 1.6.1"

---

