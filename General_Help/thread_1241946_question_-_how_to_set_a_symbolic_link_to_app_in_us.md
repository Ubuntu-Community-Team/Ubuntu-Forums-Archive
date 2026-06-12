---
title: "question - how to set a symbolic link to app in usr/local/bin"
date: 2009-08-16
forum: General Help
---

### Post by Micronaut on 2009-08-16
Hi,

I have the repository package of clustalx installed (in /usr/bin).  I have compiled the latest version from the web in /usr/local/bin.  Is it possible to set a symbolic link to the new version of the application in /usr/local/bin so that when i execute "clustalx" from the command line it launches this version, rather than the old version from the repository?

I am quite new to linix and still getting to grips with user permissions and links.  

Thanks for any assistance.

---

### Post by michy99 on 2009-08-16
First, rename /usr/bin/clustalx (in case you want to change back.)```
sudo mv /usr/bin/clustalx /usr/bin/clustalx.old
```Then make the link.```
sudo ln -t /usr/local/bin/clustalx /usr/bin/clustalx
```

---

### Post by lswb on 2009-08-16
Actually, unless you have changed it, /usr/local/bin is before /usr/bin in the path, so the /usr/local/bin version would run anyway. You can determine for sure with the "which" or "type" command

# demonstrating with "find" since I don't have clustalx on my system.
$ which find 
/usr/bin/find

---

