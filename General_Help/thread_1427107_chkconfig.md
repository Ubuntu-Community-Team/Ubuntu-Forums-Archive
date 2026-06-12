---
title: "chkconfig"
date: 2010-03-11
forum: General Help
---

### Post by Drenriza on 2010-03-11
doesn't the chkconfig command exists for ubuntu? or is it only for red hat systems?

Thanks on advance.

---

### Post by lupinx on 2010-03-11
If it exist. You must install the package: 
```
sudo apt-get install chkconfig
```

---

### Post by Drenriza on 2010-03-11
E: Couldn't find package chkconfig

Does this mean that the option/command/program is not avaliable in ubuntu at all?

---

### Post by lupinx on 2010-03-11
No, this means that it does not find the package. Check this link: [http://packages.ubuntu.com/search?keywords=chkconfig&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=chkconfig&searchon=names&suite=karmic&section=all)

---

### Post by wojox on 2010-03-11
Try updating:

```
sudo apt-get update && sudo apt-get install chkconfig
```

---

### Post by Drenriza on 2010-03-11
I cant find an chkconfig package. Anyone know if $sudo apt-get install sysv-rc-conf

commands are the same as in chkconfig? or anyone know where i can download a package from a website?

Thanks on advance

---

### Post by Drenriza on 2010-03-11
it's a mistake that it says i use 9.10.

i use 8.04 LTS hardy heron

---

### Post by wojox on 2010-03-11
> **Drenriza said:**
> I cant find an chkconfig package. Anyone know if $sudo apt-get install sysv-rc-conf

commands are the same as in chkconfig? or anyone know where i can download a package from a website?

Thanks on advance

That'll work for enable or disable system services. Yeah the 9.10 kind threw us off there. ;)

---

### Post by Drenriza on 2010-03-11
Okey, so they both work with the same commands?

Is it possible to get the package for 8.04?

---

### Post by wojox on 2010-03-11
Sure:

```
sudo apt-get update && sudo apt-get install sysv-rc-conf
```

---

### Post by wojox on 2010-03-11
Then:

```
sudo sysv-rc-conf
```

---

### Post by Drenriza on 2010-03-11
Lovely, i found an deb file.
[http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/chkconfig/](http://ubuntu2.cica.es/ubuntu/ubuntu/pool/universe/c/chkconfig/)

Installed with 0 problems, Thanks for all the help guys.

---

