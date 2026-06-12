---
title: "Changing permission on Lampp .conf files"
date: 2011-04-14
forum: General Help
---

### Post by flint0131 on 2011-04-14
How can modify httpd-xampp.conf's permission on my opt/lampp/etc/extra/ directory?
I tried chmod-ing it on terminal, there's no error message whatsoever on the terminal but it still can't be modified.
Help? I'm a newbie. :o

---

### Post by seawolf167 on 2011-04-14
You'll need to use sudo, and unless you have the -v switch you won't see any output

Example chmod to add the executible bit

```
sudo chmod +x /path/to/folder/filename
```

Then you can use ls to check that it worked

```
ls -l /path/to/folder
```

---

