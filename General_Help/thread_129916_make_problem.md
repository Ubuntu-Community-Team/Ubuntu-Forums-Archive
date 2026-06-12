---
title: "make problem"
date: 2006-02-14
forum: General Help
---

### Post by Bakerconspiracy on 2006-02-14
How do I install the make command, and why didn't it come standard with ubuntu?

root@homeNet:/home/andrew# make
bash: make: command not found

I need this command in order to install ndiswrapper for my wireless card and it appears as if it does not exist with my installation.

Im new, sorry if my mistake is completely obvious.

---

### Post by Sutekh on 2006-02-14
You need the build-essential package, which comes with make, and gcc
```
sudo apt-get install build-essential
```

ndiswrapper? so you currently have no internet in any form?

Make sure that you have the install CD, and that it is a repository for apt-get to install packages from
```
sudo apt-cdrom add
sudo apt-get update
```
otherwise you won't be able to install build-essential

-make does come standard with Ubuntu, just not installed by default-

---

### Post by heimo on 2006-02-14
```
sudo apt-get install make
```

You probably also need gcc and some libraries. I usually just install package called 'build-essential' even though it's for compiling debian packages.

---

