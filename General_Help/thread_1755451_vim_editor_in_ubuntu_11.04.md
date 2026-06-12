---
title: "vim editor in ubuntu 11.04"
date: 2011-05-11
forum: General Help
---

### Post by zobayer1 on 2011-05-11
Recently I have switched to ubuntu 11.04. VIM has always been my favorite editor, but in Natty, I am still unable to install vim (also gvim). If I try to use apt-get, all the suggested packages seems broken, I also tried with software center, there it shows failure to resolve dependencies.

What can I do? :confused: Please give me some hints. Thanks in advance,

---

### Post by TeoBigusGeekus on 2011-05-11
Have you tried changing your server?
What are the exact messages you get?

---

### Post by zobayer1 on 2011-05-11
> **TeoBigusGeekus said:**
> Have you tried changing your server?
What are the exact messages you get?

No, I haven't changed it. (Not sure how to do that as I never did that before)

And for the message from terminal
```

zobayer@zobayer:~$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vim : Depends: vim-common (= 2:7.3.035+hg~8fdc12103333-1ubuntu2) but 2:7.3.035+hg~8fdc12103333-1ubuntu7 is to be installed
E: Broken packages
zobayer@zobayer:~$ 

```

And this is from software center:
```

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details:
The following packages have unmet dependencies:

vim: Depends: vim-common (= 2:7.3.035+hg~8fdc12103333-1ubuntu2) but 2:7.3.035+hg~8fdc12103333-1ubuntu7 is to be installed
     Depends: vim-runtime (= 2:7.3.035+hg~8fdc12103333-1ubuntu2) but 2:7.3.035+hg~8fdc12103333-1ubuntu2 is to be installed

```

These are what I get, can you please tell me more about changing the server ?

---

### Post by zobayer1 on 2011-05-11
By the words "changing the server" did you mean changing the server from where software center downloads? I am from Bangladesh, and the default server is selected one from Bangladesh, the 2 options left are, usa servers and main server. which one should I select?

---

### Post by WorMzy on 2011-05-11
When is the last time you updated your package information?

```
sudo apt-get update
```
```
sudo apt-get install vim
```

---

### Post by zobayer1 on 2011-05-11
Thanks **WorMzy, **updating the cache solved the problem :D
:guitar:

---

