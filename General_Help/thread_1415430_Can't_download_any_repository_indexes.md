---
title: "Can't download any repository indexes"
date: 2010-02-24
forum: General Help
---

### Post by new 2 linux on 2010-02-24
hey evrybody, i have a problem with the synaptic package manager. I can't refresh it

---

### Post by 3rdalbum on 2010-02-24
My god, change your system font back to something more readable, and to a smaller size.

If all the repositories are throwing this error, then try changing your Ubuntu mirror in System > Administration > Software Sources

But I can only see one repository that's giving the error - the Hardy Backports. Probably not worth worrying about if your main and universe repositories are working.

---

### Post by new 2 linux on 2010-03-23
well i don't know how change my Ubuntu mirror and i tried sudo apt-get update and got this in the terminal  can someone help me with this

---

### Post by tommynz1975 on 2010-03-23
In Terminal could you please try and give feedback.

```
sudo dpkg --configure -a
```

you may not get a responce to this command
then follow it up with

check for issues with dpkg
```
sudo dpkg --audit 
```

update sources lists and update files on the same command line
```
 sudo apt-get update && sudo apt-get dist-upgrade 
```

---

