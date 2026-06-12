---
title: "Console cannot execute exexutables"
date: 2011-01-23
forum: General Help
---

### Post by gkaykck on 2011-01-23
Hi there,
It is rather a strange problem that i am facing. I don't know when or why it started but now my console cannot execute anything if i don't enter the entire executable path.
Some other executables that i included in bashsc is working.
But if i go into any folder that includes any executables, i cannot execute that files UNLESS i give a full path.
Example
{
gkaykck@ubuntu:~/Desktop/mongo$ mongo
The program 'mongo' is currently not installed.  You can install it by typing:
sudo apt-get install mongodb-clients
gkaykck@ubuntu:~/Desktop/mongo$ '/home/gkaykck/Desktop/mongo/mongo' 
MongoDB shell version: 1.6.5
connecting to: test
}

I really cannot see any obvious reason, so i need your help guys...

---

### Post by corncob on 2011-01-23
My understanding is that Ubuntu does not search the entire drive for executables.  If you don't specify the path it only looks in those directories specified in the $PATH variable.  Here is mine which, as I haven't messed with it, I'm sure is typical:
```
corncob@eeebox:~$ echo $PATH
/home/corncob/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
corncob@eeebox:~$ 
```
/home/corncob/Desktop is not on the path.

---

### Post by CharlesA on 2011-01-23
You can run a executable from the current directory by typing this:

```
./executable
```

---

