---
title: "Cant install/compile a tar.gz file and cant figure out why..."
date: 2011-12-01
forum: General Help
---

### Post by pottsiex5 on 2011-12-01
Hi,
Im trying to install/compile a tar.gz file, but cant figure out why its not working.
This is the file im trying to install: [http://sourceforge.net/projects/corewar/](http://sourceforge.net/projects/corewar/) 
and these are the instructions im using: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
Everything goes fine up until i run "./configure"

Any advice,
x5

---

### Post by crazy bird on 2011-12-01
What kind of errors you get? Can you put the errormessages here as well since this might help us providing you with a solution.

---

### Post by haqking on 2011-12-01
[http://ubuntuforums.org/showthread.php?t=1509565](http://ubuntuforums.org/showthread.php?t=1509565)

it is in the repos [https://launchpad.net/ubuntu/hardy/+package/corewars](https://launchpad.net/ubuntu/hardy/+package/corewars)

though old version.

you can get a .deb file.

Also in the source did you read the readme file as there are some dependency requirements.

---

### Post by pottsiex5 on 2011-12-01
Hi, the error i get is:
```
pottsie@Pottsie-Pavilion:/usr/local/src/pmars-0.9.2$ ./configure
bash: ./configure: No such file or directory

```

---

### Post by 3rdalbum on 2011-12-01
Let's back things up a little.

Firstly, you DON'T want the 'pmars' directory inside the /usr/local directory. You want it somewhere convenient in your home directory. Otherwise, you'll only be able to compile the software as root.

Secondly, check that the pmars-0.9.2 folder contains a file called "configure" and that it has execute permission. If it doesn't have a "configure" file, is it in a subfolder? And some software doesn't need a configure script; does the documentation in the folder have any instructions of what to run?

You're doing okay up to this point, just remember that "./configure" means "run a program called 'configure' in this folder.

---

### Post by pottsiex5 on 2011-12-01
There is a folder called config in it with the following files:
94x.opt
icws.opt
mw.mac
pmars.mac
x.opt
Are any of these the ones i should run?

---

### Post by haqking on 2011-12-01
we could backup even more to my first post.

just use the .deb file

[https://launchpad.net/ubuntu/hardy/i386/corewars/0.9.13-1build1](https://launchpad.net/ubuntu/hardy/i386/corewars/0.9.13-1build1)

a little older a version though

and in the source download there is not configure file, there is a makefile

---

