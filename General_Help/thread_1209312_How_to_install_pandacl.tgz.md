---
title: "How to install pandacl.tgz"
date: 2009-07-10
forum: General Help
---

### Post by kyqinqiqin on 2009-07-10
I just download a software for anti-virus. This is have problems when I want to install it, and I can't found the application for Install. I open and open those folders, and is not found the file in the end. I can't to solve this problem.

---

### Post by wojox on 2009-07-10
Open your terminal and go to the directory it is in:

```
tar xvzf pandacl.tgz
```

---

### Post by kyqinqiqin on 2009-07-14
I tried to many times and tried to find others. It is I faulted in the final. I taking a picture for you, and you and me to fine what is the wrong. Maybe was my wrong, I can't fine this truly wrong.
[ATTACH]121060[/ATTACH]

---

### Post by nikhilk on 2009-07-14
I can many "No such file or directory" error messages. Are you sure you have got the right path for the ".tgz" file?
I also see this error message at the very end
```
mv: target `Files/Kotori/Install/linux/pandacl_linux.tgz' is not a directory
```
It seems that is where the file is. Try this command
```
tar zxvf Files/Kotori/Install/linux/pandacl_linux.tgz
```

---

### Post by kyqinqiqin on 2009-07-14
It was my .tgz is wrong, maybe is it. I don't know the Pandacl_linux.tgz. I tried to pull it any ways and tried agained. But it does have error messages too. I don't understand the software. Could you tell me where how can get it like you.

---

