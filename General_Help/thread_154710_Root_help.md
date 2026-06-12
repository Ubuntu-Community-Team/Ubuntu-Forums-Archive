---
title: "Root help"
date: 2006-04-03
forum: General Help
---

### Post by thenewone on 2006-04-03
Ok i am login as root but when i try to install something from terminal i get"ERROR:  Must Be Run As ROOT" so i open Root Shell and  type in my password and with no warning it just closes i am new to linux and cant figure this one out

---

### Post by gingermark on 2006-04-03
Am I right in thinking that you've created a root account? As [this page](https://wiki.ubuntu.com/RootSudo) explains, this isn't the default behaviour in Kubuntu.

What command are you trying to use? (EDIT: Just re-read - you're installing, so "apt-get install"?)

If you prefix the command with "sudo" and then enter your user password, does this work?

---

### Post by thenewone on 2006-04-03
I am trying to install  Linux Display Driver - IA32 It tells me to type "sh NVIDIA-Linux-x86-1.0-8178-pkg1.run"

---

### Post by thenewone on 2006-04-03
I got it "sudo -i" thanks

---

### Post by aysiu on 2006-04-03
So instead of logging in as root, go to a **regular** Konsole terminal and type ```
sudo sh NVIDIA-Linux-x86-1.0-8178-pkg1.run
``` enter your **user** password.

---

