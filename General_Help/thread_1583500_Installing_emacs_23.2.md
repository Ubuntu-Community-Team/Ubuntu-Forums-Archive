---
title: "Installing emacs 23.2"
date: 2010-09-27
forum: General Help
---

### Post by ngungu on 2010-09-27
How can I compile and install emacs 23.2?
I tried ./configure and got an error message said no X-Windows support

---

### Post by mjneil.81 on 2010-09-27
in terminal sudo apt-get install emacs.

---

### Post by andrewthomas on 2010-09-28
> **mjneil.81 said:**
> in terminal sudo apt-get install emacs.
That's emacs 23.1

```
sudo apt-get install build-essential checkinstall
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by ngungu on 2010-09-28
> **andrewthomas said:**
> That's emacs 23.1

```
sudo apt-get install build-essential checkinstall
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Is that how you installed emacs 23.2? I'm new to Ubuntu. Can you show me step by step how to get emacs installed?

Thanks

---

### Post by andrewthomas on 2010-09-28
> **ngungu said:**
> Is that how you installed emacs 23.2? I'm new to Ubuntu. Can you show me step by step how to get emacs installed?

Thanks
if you want emacs-23.1 you can install with

```
sudo apt-get install emacs
``` otherwise you have to compile & build the package yourself.

---

### Post by ngungu on 2010-09-28
> **andrewthomas said:**
> if you want emacs-23.1 you can install with

```
sudo apt-get install emacs
``` otherwise you have to compile & build the package yourself.

Emacs 23.1 is too buggy. I was having problem with the font size though I used (set-face-attribute 'default nil :height 100)
in .emacs. It would get bigger again whenever I maximized emacs. FYI, I was running emacs 23.1 in Ubuntu 10.04

---

### Post by andrewthomas on 2010-09-28
> **andrewthomas said:**
> 

```
sudo apt-get install build-essential checkinstall
```[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
  
So read the link, install the packages ......

EDIT: here is a ppa, much easier just follow the instructions

[https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

---

