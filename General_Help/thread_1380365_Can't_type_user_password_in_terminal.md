---
title: "Can't type user password in terminal"
date: 2010-01-13
forum: General Help
---

### Post by lokino on 2010-01-13
(its my first post so i've no clue what the prefix is for, sorry if its wrong)

I've been having problems whenever I'm asked for my password inside the Terminal. The most recent one happens when I type this
```
ben@ben-desktop:~$ sudo apt-get install flashplugin-installer
```It says this
```
[sudo] password for ben:
```But then I can't type anything. I try to but nothing happens. Please help.

---

### Post by jmcgovern on 2010-01-13
> **lokino said:**
> (its my first post so i've no clue what the prefix is for, sorry if its wrong)

I've been having problems whenever I'm asked for my password inside the Terminal. The most recent one happens when I type this
```
ben@ben-desktop:~$ sudo apt-get install flashplugin-installer
```It says this
```
[sudo] password for ben:
```But then I can't type anything. I try to but nothing happens. Please help.

Working as intended.  when you type your password in terminals, you get no feedback but it IS entering. just type the password and hit enter and it will go through even though nothing appears.

---

### Post by sisco311 on 2010-01-13
There is no visual feedback when you type your password. So don't worry, just type in the password then press Enter.

  [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by uidb4056 on 2010-01-13
> **lokino said:**
> (its my first post so i've no clue what the prefix is for, sorry if its wrong)

I've been having problems whenever I'm asked for my password inside the Terminal. The most recent one happens when I type this
```
ben@ben-desktop:~$ sudo apt-get install flashplugin-installer
```It says this
```
[sudo] password for ben:
```But then I can't type anything. I try to but nothing happens. Please help.

Even you can't get any feedback as you type (normal behavior) you have to key in your password and then return key

---

### Post by cavh on 2010-01-13
When you type the sudo password, you don't get asterisk (or some other masking character) marks like you usually get in other environments. Just type your password and hit the enter key.

---

### Post by lokino on 2010-01-16
thanks, "problem" solved

---

### Post by sisco311 on 2010-01-16
Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

