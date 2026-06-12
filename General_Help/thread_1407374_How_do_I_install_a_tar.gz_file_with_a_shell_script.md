---
title: "How do I install a tar.gz file with a shell script?"
date: 2010-02-15
forum: General Help
---

### Post by hurtstotalktoyou on 2010-02-15
Hi, guys.

So, I have to install a program from a tar.gz file.  I have extracted it using fileroller, and it contains an installation "shell script" file.

I have no idea what scripts are, or how they work.  I tried sudo make/sudo make install, with no luck.

Does anyone know how I install this program using the shell script file?

Thanks!

---

### Post by pmlxuser on 2010-02-15
read through readme file usually accompy such kind

or try 
```
chmod +x script file 
``` to make it executable
then 
```
./scriptfile 
``` to run it.

---

### Post by hurtstotalktoyou on 2010-02-15
Thanks man!

The program still failed to install, but the shell script ran like a champ using the commands you provided.  I appreciate the help.

I guess I'll have to abandon hope of installing this program.  Oh well.

---

### Post by elliotn on 2010-02-15
In most cases installing for tarballs just wont work as dependencies are likely not to be met.

---

