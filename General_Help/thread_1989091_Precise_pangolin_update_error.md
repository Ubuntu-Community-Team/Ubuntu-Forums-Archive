---
title: "Precise pangolin update error"
date: 2012-05-28
forum: General Help
---

### Post by chebre on 2012-05-28
I have an error message when i trying to update or install some software, and it's appears something warning red symbol in my ubuntu. the message is

an error ocurred, please run package manager from the rigth click menu 
or apt-get in a terminal to see what is wrong. The error message was:
'Error : BrokenCount>0'. This usually means that your installed package
have unmet dependencies 

and I try use the apt-get -f install to fix it but, it resolves nothing

---

### Post by philinux on 2012-05-28
> **chebre said:**
> I have an error message when i trying to update or install some software, and it's appears something warning red symbol in my ubuntu. the message is

an error ocurred, please run package manager from the rigth click menu 
or apt-get in a terminal to see what is wrong. The error message was:
'Error : BrokenCount>0'. This usually means that your installed package
have unmet dependencies 

and I try use the apt-get -f install to fix it but, it resolves nothing

Post the output errors of sudo apt-get update and sudo apt-get upgrade

---

### Post by js6seaj on 2012-06-05
> **philinux said:**
> Post the output errors of sudo apt-get update and sudo apt-get upgrade I'm somewhat new to Ubuntu, how do you do that?

---

### Post by fantab on 2012-06-06
> **js6seaj said:**
> I'm somewhat new to Ubuntu, how do you do that?

Open TERMINAL (you will find this along with your other applications) and run the following commands:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

---

### Post by js6seaj on 2012-06-06
> **fantab said:**
> Open TERMINAL (you will find this along with your other applications) and run the following commands:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

I did sudo apt-get update, and it worked fine. I did sudo apt-get upgrade and this is what I get after I do that. Guessing I did something wrong. Thanks for the help, kinda reminds me of DOS, but different enough to be a challenge.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1) but 2.15-0ubuntu10 is installed
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.3-4ubuntu2 is installed
E: Unmet dependencies. Try using -f.
I tried using sudo -f apt-get libc-bin and sudo -f apt-get libnih1, but that didn't seem to do anything.

---

### Post by fantab on 2012-06-07
No, you have to run:

```
$ sudo apt-get -f install
```

Dont try to install any packages with this command. It is to fix broken packages.

---

### Post by js6seaj on 2012-06-14
> **fantab said:**
> No, you have to run:

```
$ sudo apt-get -f install
```

Dont try to install any packages with this command. It is to fix broken packages.

Just left me at a $ prompt after installing and the error isn't listed any more, so guess it worked. Thanks.:)

---

