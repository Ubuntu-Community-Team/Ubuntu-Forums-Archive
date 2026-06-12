---
title: "cd command"
date: 2010-06-22
forum: General Help
---

### Post by rashadkm on 2010-06-22
which program is responsible for showing the current directory on shell prompt.
Or Is it a feature of bash shell. but when installed bash shell it wont show the directory name when using cd command.

something like this
rashad@rashad-laptop:~$  cd Documents give a prompt like this
rashad@rashad-laptop:~/Documents$ 

but when installed bash it shows only
bash-3.0#

anyhelp will be greatly appreciated

---

### Post by Lampi on 2010-06-22
this is done in the PS1=something line of ~/.bashrc

I guess this file is missing in your installation

---

### Post by geirha on 2010-06-22
You need to set the PS1 prompt variable. See the PROMPTING section of *man bash*. This should give you a prompt like you're explaining.
```
PS1='\u@\h:\w\$ '
``` You put it in ~/.bashrc to make it permanent.

---

