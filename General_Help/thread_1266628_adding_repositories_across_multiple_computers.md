---
title: "adding repositories across multiple computers"
date: 2009-09-14
forum: General Help
---

### Post by gforster on 2009-09-14
I have 30+ computers that I regularly update using the [sshsudo]("http://code.google.com/p/sshsudo/") script. I would like to add a new repository for packages to all of these computers, but cannot figure out how to do so via the terminal. If I pipe a command to append a line using sshsudo like: 
```
echo "[some repository]" | sudo tee -a /etc/apt/sources.list
```
I run into a problem, because the second part requires a second sudo command and apparently sshsudo does not work this way.

should I write a script and use sshsudo to execute the script? Should I set up private/public keypairs and then use a script that would look akin to this:
```
#!/bin/bash

ipaddy=1
until [ $ipaddy -eq 30 ]
do
ssh 10.0.201.$ipaddy 'echo "[some repository]" | sudo tee -a /etc/apt/sources.list' &
ipaddy=$(($ipaddy +1 ))
done
```

am I on the right track with either of these options? Should I be doing something completely different?

---

### Post by lswb on 2009-09-14
not sure I undersand all the details here, but can you just

sudo /bin/echo "some repository" >> /etc/apt/sources.list

Also fyi for several versions now there is a /etc/apt/sources.list.d/ directory and any files in this directory are treated as if their text was part of sources.list

---

### Post by gforster on 2009-09-14
I would have to ssh into each computer individually and I would like to simply issue a single command from a single computer to accomplish this. That method you describe does not work via sshsudo.

---

