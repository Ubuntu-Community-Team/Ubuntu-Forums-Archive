---
title: "Red Eclipse Error"
date: 2012-09-26
forum: General Help
---

### Post by Joon Lee on 2012-09-26
I created a symbolic link (sudo ln -s) of the reclient_linux (binary?) in /opt/redeclipse-1.3.1/bin in /usr/bin, but when I run reclient_linux from my terminal (accessing usr/bin), it says that the core textures could not be found. Any ideas on how to get it to work? I can always run redeclipse.sh, but I have to cd to the pretty-long-directory and then ./redeclipse.sh. I would instead like to simply type, in terminal, reclient_linux (much faster, of course), so please help.

*The reason why I didn't get the software center package is because the center has an outdated version

---

### Post by sisco311 on 2012-09-26
You can create a little script in /usr/local/bin:
```
gksu gedit /usr/local/bin/redeclipse
```

Something like:```
#!/bin/sh
cd */very/long/path/to/dir* || exit 1
./redeclipse.sh

```

EDIT: Don't forget to make it executable :)
```
sudo chmod +x /usr/local/bin/redeclipse
```

---

### Post by Joon Lee on 2012-09-26
Worked perfectly (and beautiful humor "very-long-directory"). Thanks!

---

