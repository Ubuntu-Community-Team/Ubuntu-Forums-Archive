---
title: "where's Make command?"
date: 2006-01-23
forum: General Help
---

### Post by Dod on 2006-01-23
Hi everyone! I'm totally new to Linux and to be honest I don't know anything about anything... So, I was trying to install some stuff and following the installing instructions, after (or before?) the ./configure i had to do the command Make, when i typed Make in the terminal i got back the following message: bash: make: command not found. My question is, as the title says, where's the make command? can someone help me whenever possible?

---

### Post by o_fortuna on 2006-01-23
[QUOTE=Dod]Hi everyone! I'm totally new to Linux and to be honest I don't know anything about anything... So, I was trying to install some stuff and following the installing instructions, after (or before?) the ./configure i had to do the command Make, when i typed Make in the terminal i got back the following message: bash: make: command not found. My question is, as the title says, where's the make command? can someone help me whenever possible?[/QUOTE]
Make sure that you have build-essential installed. Open up synaptic, click on search, and type in build-essential. Then make sure it is installed. Installing it will install everything you need to do basic compilation. (You could also do
```
sudo apt-get install build-essential
``` at the command line, Applications-->Accessories-->Terminal) This will let you build stuff. In my experience, though, compiling stuff is just a last resort since so many binary packages can be installed more easily with Synaptic/Add Applications.

---

