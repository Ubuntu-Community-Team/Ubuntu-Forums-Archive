---
title: "Java Binaries not istalling"
date: 2011-07-13
forum: General Help
---

### Post by melmantheman on 2011-07-13
hi im very new to the forum and im not sure if this is in the right spot, but im having a very complicated problem. Ive looked and ive seen many tuts on how to do this but ive never seen a specific answer to my problem. 

Specs:
-Kubuntu 11.04

Problem:
every time i use KPackageKit to try to install something it always tries to install sun-java6-bin which is already installed. ive added repositories, ive used restricted-extras, ive done the update and installs in terminal. java works fine for me in the browser and for terminal commands. i have set sun-java6 as the default java and updated it again.

the error code is:
```
subprocess installed post-installation script returned error exit status 2
```

thanks in advance. i dont know what to do. all my installations fail. and i cant do anything. i hope ive provided ample information.

---

### Post by Gyokuro on 2011-07-13
Hi,

can you type in a terminal (KTerminal) following command:

sudo apt-get clean && apt-get update && apt-get upgrade

and post the output.

---

