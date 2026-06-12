---
title: "'Error: Incorrect path to installation script' error while running install.sh"
date: 2010-08-03
forum: General Help
---

### Post by Vinnare on 2010-08-03
Hello,

I'm trying to install Intel Fortran Compiler Professional Edition for Linux IA-32 and am getting the following error:

> 
root@p-comp:~/Documents/fortran compiler/l_cprof_p_11.1.072_ia32# ./install.sh
Error: Incorrect path to installation script. Installation can not be started
if the path contains space symbols.

Quitting! Press "Enter" to terminate install.



I've tried after downloading fresh files from intel's site but the problem persists. The install.sh file exists in the folder. I don't understand what to do! I leave no spaces anywhere as the error message says

Please help. It is URGENT!!!

---

### Post by prodigy_ on 2010-08-03
> **Vinnare said:**
> /fortran compiler/
Maybe you indeed should use a folder without whitespaces in its name.

---

### Post by Vinnare on 2010-08-05
Thanks it worked. :guitar:

Can you tell me why does it happen so? what is the problem with spaces? this problem occurred only when I tried installing this, at no other time have I faced any such problem.

---

### Post by chmurillor on 2011-01-06
Hello

Please, help me because I have the same problem. I have checked and I don't have a folder with spaces

The path of the install.sh folder is
/home/carlos/Documents/fortrancompiler/lfcompxe20111107/.


carlos@carlos-laptop:~/Documents/fortrancompiler/lfcompxe20111107$ sh install2.sh
Error: Incorrect path to installation script. Installation can not be started
if the path contains space symbols.

Quitting! Press "Enter" to terminate install.
read: 290: arg count
exit: 290: Illegal number: -1

Thanks in advance for your help

---

### Post by return 0 on 2011-03-08
mkdir /home/yourname/something
tar xzvf intel....tgz in your folder
delete space symbols in untared folder
come in folder using command cd and execute ./install.sh at non-root privileges.
:)

---

### Post by rnerwein on 2011-03-08
hi
if you haven't solved your problem already then try:
insert ( at the beginning ) into your script: set -x
this will cause a trace of the script and you will see where your problem sits.
ciao

---

