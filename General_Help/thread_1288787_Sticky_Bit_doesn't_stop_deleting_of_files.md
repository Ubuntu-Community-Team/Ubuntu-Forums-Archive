---
title: "Sticky Bit doesn't stop deleting of files?"
date: 2009-10-11
forum: General Help
---

### Post by KlinerDraken on 2009-10-11
Not sure if i misunderstand sticky bit or it's not working like it should. But i am able to delete files with the sticky bit set that i am not the owner of. Am i missing something?



```
ben@UbuntuHome:~/test$ [COLOR="DarkGreen"]ls -l[/COLOR]
total 0
[COLOR="Blue"]-rwxrwxrwx[/COLOR] 1 ben ben 0 2009-08-02 15:51 file1
-rw-r--r-- 1 ben ben 0 2009-08-02 15:51 file2
ben@UbuntuHome:~/test$ [COLOR="DarkGreen"]chmod 1777 file1[/COLOR]
ben@UbuntuHome:~/test$ [COLOR="DarkGreen"]ls -l[/COLOR]
total 0
[COLOR="Blue"]-rwxrwxrwt[/COLOR] 1 ben ben 0 2009-08-02 15:51 file1
-rw-r--r-- 1 ben ben 0 2009-08-02 15:51 file2
ben@UbuntuHome:~/test$ [COLOR="DarkGreen"]sudo chown root:root file1[/COLOR]
[sudo] password for ben: 
ben@UbuntuHome:~/test$ ls -l
total 0
-rwxrwxrwt 1 [COLOR="Blue"]root root[/COLOR] 0 2009-08-02 15:51 file1
-rw-r--r-- 1 ben  ben  0 2009-08-02 15:51 file2
ben@UbuntuHome:~/test$ [COLOR="DarkGreen"]rm file1[/COLOR]
ben@UbuntuHome:~/test$ [COLOR="DarkGreen"]ls -l[/COLOR]
total 0
-rw-r--r-- 1 ben ben 0 2009-08-02 15:51 file2
ben@UbuntuHome:~/test$ 
```

---

### Post by wdaniels on 2009-10-11
You can still delete the file if you are the directory owner.

---

### Post by KlinerDraken on 2009-10-11
> **wdaniels said:**
> You can still delete the file if you are the directory owner.

ahhhh.. ok, thanks :)

---

