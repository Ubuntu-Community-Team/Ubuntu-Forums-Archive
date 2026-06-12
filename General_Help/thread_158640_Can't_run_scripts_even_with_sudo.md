---
title: "Can't run scripts even with sudo"
date: 2006-04-11
forum: General Help
---

### Post by Laterix on 2006-04-11
I have quite fresh install of Ubuntu breezy and I keep getting this error. What does this mean? In this example I tried to run script as root (sudo -s -H), but same error comes with sudo **./install.sh** and it's not only this script, but basicly all executions I try to run with **./**. Sometimes it works if I run for example **sh example-script.sh**.
```

root@laterix:/home/late/downloads/secure-0.3# ./install.sh
bash: ./install.sh: /bin/sh: bad interpreter: Permission denied

```

---

### Post by Enfenion on 2006-04-11
Has the script got permission to run?

If not, you have to use chmod to give the script permission...

---

### Post by JoeMetal on 2006-04-11
You can check permissions with 
```
ls -l
```

---

### Post by Laterix on 2006-04-11
Yes, script has permissions to run. I'm not complete noob with linux, but this is something I don't understand. Hopefully someone can help me, because this "bug" restricts my usage alot.

EDIT: Okay, I was wrong. It didn't have execution permissions for root. But still scripts doesn't work if I don't use **sh** command to execute them. Before I could just write **./script.sh**.

---

### Post by Laterix on 2006-04-11
Not anyone?! Please, This is really bugging me. Here is an example:
```

[late@laterix azureus]$ sudo chmod 777 azureus
[late@laterix azureus]$ ./azureus
bash: ./azureus: /bin/bash: bad interpreter: Permission denied

```

---

