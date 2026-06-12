---
title: "Run program on ssh login"
date: 2009-09-09
forum: General Help
---

### Post by PurposeOfReason on 2009-09-09
Pretty self explanitory, I'm trying to run:
```
ssh shawn@192.168.1.113 'slurm -i eth0'
```and nothing happens. I can put 'sleep x' instead of slurm and it will sleep for x seconds. The goal is to spawn a new terminal running slurm for my server.

---

### Post by eric3_14159 on 2009-10-08
Try putting a & at the end of the command inside the quotes?

---

### Post by kevdog on 2009-10-08
Can you just add this command to either your .bashrc or .bash_profile or .profile file?  I'm not sure if this assumption is correct, however the way you wrote the command -- I thought the command was executed once logged in and then the connection was dropped. You could try:

ssh shawn@192.168.1.113 && 'slurm -i eth0'

---

