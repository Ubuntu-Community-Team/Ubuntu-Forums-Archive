---
title: "can't install quake 4 on 9.04"
date: 2009-07-20
forum: General Help
---

### Post by BennyLZ on 2009-07-20
when I try to execute quake4-linux-1.4.2.x86.run by ```
sudo ./quake4*.run
``` or ```
sudo sh quake4*.run
``` I get:
```
quake4-linux-1.4.2.x86.run: 1: Syntax error: "(" unexpected
```

if I execute it without "sudo", I get:
```
bash: ./quake4-linux-1.4.2.x86.run: impossibile eseguire il file binario
```
(in english is: *bash: ./quake4-linux-1.4.2.x86.run: can't execute the binary file*)

I followed all the instructions in the official faq: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

what can I do?

PS: the installer has the executing permission

---

### Post by dexter on 2009-07-20
Do you have the 32bit or 64bit jaunty installed?

I'm not sure if quake4-linux-1.4.2.**x86**.run is supposed to run on a 64 bit linux installation.

---

### Post by xamox on 2009-08-15
> **BennyLZ said:**
> when I try to execute quake4-linux-1.4.2.x86.run by ```
sudo ./quake4*.run
``` or ```
sudo sh quake4*.run
``` I get:
```
quake4-linux-1.4.2.x86.run: 1: Syntax error: "(" unexpected
```

if I execute it without "sudo", I get:
```
bash: ./quake4-linux-1.4.2.x86.run: impossibile eseguire il file binario
```
(in english is: *bash: ./quake4-linux-1.4.2.x86.run: can't execute the binary file*)

I followed all the instructions in the official faq: [http://zerowing.idsoftware.com/linux/quake4/](http://zerowing.idsoftware.com/linux/quake4/)

what can I do?

PS: the installer has the executing permission



Well I know this is a bit late, but did you try running

```
chmod +x quake4-linux*.run
```

to set the file as an executable, then run:

```
./quake4-linux*.run
```

---

