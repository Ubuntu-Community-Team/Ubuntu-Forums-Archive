---
title: "Unusual error when trying to execute shell script"
date: 2010-01-14
forum: General Help
---

### Post by akromm on 2010-01-14
so i downloaded the netbeans installer (which is a shell script) and tried to run it and i get the following error:

```

adam@adam-laptop:~/Downloads$ ./netbeans-6.8-ml-cpp-linux.sh 
bash: ./netbeans-6.8-ml-cpp-linux.sh: /bin/dash: bad interpreter: Permission denied

```

i also tried the same thing with the vuze setup script with the same error.  Also i already did chmod +x <script>.  and set the permissions.

any other ideas?

EDIT:: it seems that if i use /bin/bash instead of /bin/sh (ubuntu default?) it works.

---

### Post by iponeverything on 2010-01-14
The first line should be the shell interpreter that the script was written for:  

```
#!/bin/sh
```

file should be executable by user running it. 

```
chmod 755 
```

will make it executable by everyone.

Also run dos2unix on it in-case you have mucked EOL's  

```
sudo apt-get install tofrodos

dos2unix netbeans-6.8-ml-cpp-linux.sh 

```

---

### Post by akromm on 2010-01-14
does the 

#!/bin/bash

mean that the file needs to be interpreted by that shell, or that it will switch to that shell in order to interpret it?

vuze was /bin/bash and netbeans was /bin/sh  but, ubuntu uses dash.  So i got it to work but doing /bin/bash <script>

But shouldnt it switch automagicaly to the required shell to interpret a script?

---

### Post by iponeverything on 2010-01-14
> **akromm said:**
> does the 

#!/bin/bash

mean that the file needs to be interpreted by that shell, or that it will switch to that shell in order to interpret it?

vuze was /bin/bash and netbeans was /bin/sh  but, ubuntu uses dash.  So i got it to work but doing /bin/bash <script>

But shouldnt it switch automagicaly to the required shell to interpret a script?

Scripting varies for differing interpreters. The hash bang at the top of the file clues the system in to as what interpreter to use.

---

### Post by akromm on 2010-01-14
ok, so the hash bang thing isnt working on my computer then.  Cause is till have to explicitly state which interpreter to use (eg. bash script.sh)  but if a script has a call to another script, it wont work unless, i edit the script so that the line explicitly says bash <new_script>.sh

anyideas how to fix this?

---

