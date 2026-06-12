---
title: "File wont open ??"
date: 2010-06-15
forum: General Help
---

### Post by vlada92 on 2010-06-15
why i cant open one file (the one with X mark above it)
it says that i dont have permisions...
ps. im on trying version of ubuntu

here is the picture..

[IMG]http://img266.imageshack.us/img266/6863/pictureq.png[/IMG]

---

### Post by TheStroj on 2010-06-15
Wrong permissions are set. Open terminal, navigate to the folder and do this. 
```
chmod 777 FileName
```

This will set read/write/execute permission to everyone accesing that folder.

---

### Post by vlada92 on 2010-06-15
it says this

> ubuntu@ubuntu:~$ chmod 777 World of Warcraft Wrath of the Lich King
chmod: cannot access `World': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `Warcraft': No such file or directory
chmod: cannot access `Wrath': No such file or directory
chmod: cannot access `of': No such file or directory
chmod: cannot access `the': No such file or directory
chmod: cannot access `Lich': No such file or directory
chmod: cannot access `King': No such file or directory
ubuntu@ubuntu:~$ 


what i have to do??

---

### Post by TheStroj on 2010-06-15
Space isn't recognized as space here. 

Type first word of the file then hit 'tab' key so it auto-completes and adds slashes and backslashes needed to get the correct file name. After that, it will work :) 

Oh, btw, if more files got same word in the begining of their name, just watch how the computer adds slashes and backslashes and add them yourself.

---

### Post by vlada92 on 2010-06-15
it doesnt work.. can u enter that code becouse it wont work when i enter ..

---

### Post by TheStroj on 2010-06-15
First you need to navigate to that location keeping the file (by using 'cd' command, which means change directory).

Once you are in, use this command:
(I modified it for you)

```
chmod 777 World\ of\ Warcraft\ Wrath\ of\ the\ Lich\ King/

```

---

### Post by nothingspecial on 2010-06-15
First go the parent directory in the terminal. To do this easily just drag the icon of the external drive into the terminal. Then 

```
sudo chmod -R 777 "World of Warcraft Wrath of the Lich King"
```

or
```

sudo chmod -R chmod 777 World/ of/ Warcraft/ Wrath/ of/ the/ Lich/ King
```

---

### Post by nothingspecial on 2010-06-15
> **TheStroj said:**
> First you need to navigate to that location keeping the file (by using 'cd' command, which means change directory).

Once you are in, use this command:
(I modified it for you)

```
chmod 777 World\ of\ Warcraft\ Wrath\ of\ the\ Lich\ King/

```

If it is a directory I assume it contains stuff. Use the -R flag to change the permissions of everything in it too.

---

### Post by TheStroj on 2010-06-15
> **nothingspecial said:**
> If it is a directory I assume it contains stuff. Use the -R flag to change the permissions of everything in it too.

He was refering to opening a directory so I just put the basic code which enables that. Further process could also be done by chmod-ing *.* in that specific directory.

---

