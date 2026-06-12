---
title: "bash script help"
date: 2011-07-21
forum: General Help
---

### Post by Keypel on 2011-07-21
I have no idea how to make a bash script but I'm trying.

My bash script goes something like this:

#/bin/bash
sudo mkdir /media/5gb
sudo mount /dev/sdc3 /media/5gb

I made it executable, put in /usr/local/bin and updatedb

Then I made a launcher pointing to the bash script.

The problem is, If I use the launcher, it never asks for your admin password so, the folder doesn't get created.

--

---

### Post by papibe on 2011-07-21
I would go this way: the shell will assume you have privileges to run it:
```
#!/bin/bash
mkdir /media/5gb
mount /dev/sdc3 /media/5gb
```
Then I would use sudo to call it:
```
$ sudo myscript.sh
```
Or if you want the password to be asked graphically:
```
$ gksudo myscript.sh
```
Regards.

---

### Post by Keypel on 2011-07-21
Thank You, works perfect now.

--

---

