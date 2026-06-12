---
title: "Can't Install/Uninstall anything"
date: 2010-09-03
forum: General Help
---

### Post by lawson_akira on 2010-09-03
Hi everyone, im new to ubuntu so i may not understand some answers so please bare with me. For a university thing i needed to run java so i installed sun java 6.0. I got an error half way though so i thought nothing of it and went off to do other things. Now when i try and install or uninstall anything i get this message

The package system is broken
If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

and the details read 

sun-java6-plugin

Could anyone please help me. It would be greatly appreciated :D
Thankyou for your time

---

### Post by ba_saish on 2010-09-04
Hi, 
did you try running the command mentioned on the terminal ? 
If can launch your package manager you can try fixing the broken packages from 
edit->fix broken packages

---

### Post by juil on 2010-09-04
More specifically, go to Synaptic.
Then left bottom will show Custom filters. Click on that.
Then choose broken and it will show any broken packages.

---

### Post by Dustin2128 on 2010-09-05
you might also try 
```
sudo apt-get purge whatever java package you installed
```

---

### Post by Sef on 2010-09-05
How did you install java originally?

---

