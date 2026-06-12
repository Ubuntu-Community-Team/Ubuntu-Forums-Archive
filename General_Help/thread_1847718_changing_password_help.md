---
title: "changing password help"
date: 2011-09-21
forum: General Help
---

### Post by brucebruce on 2011-09-21
im having trouble accessing the windows/system32/config file within this windows 7 system using the terminal from ubuntu 9.10 so that i can change a password that has been forgotten. i can get to the hdd itself but nothing after that n im only following a guide so i have no clue as to what i could be doing wrong. any insight?

---

### Post by haqking on 2011-09-21
> **brucebruce said:**
> im having trouble accessing the windows/system32/config file within this windows 7 system using the terminal from ubuntu 9.10 so that i can change a password that has been forgotten. i can get to the hdd itself but nothing after that n im only following a guide so i have no clue as to what i could be doing wrong. any insight?

you are trying to change a windows 7 password from within Ubuntu using terminal ?

You wont reset a system password from editing a config file.

If you are trying to reset a windows password there are many resources online to download and enable you to do that.

If you need to change a Linux password then please post more information so we can help.

---

### Post by dave01945 on 2011-09-21
what program are you using to reset the password i've always found **chntpw** works well also if you can get to the windows hdd dont forget linux is *case sensitive* the file you will be looking for is in

```
/WINDOWS/system32/config/SAM
```

you need to run the program on the SAM file

also if you say you can get to the windows hdd i'm presuming you have already mounted it and you know where it is mounted

if you need any more help some more detail will be usefull and a link to the guide you are using

---

