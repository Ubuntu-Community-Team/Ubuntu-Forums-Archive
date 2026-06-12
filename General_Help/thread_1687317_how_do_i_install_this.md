---
title: "how do i install this?"
date: 2011-02-13
forum: General Help
---

### Post by xrc6 on 2011-02-13
downloaded a driver, clicking it opens in archiver...how the heck do install this?

---

### Post by dabl on 2011-02-13
Before installing something you downloaded, and guestimating you are new to Linux (but not to installing downloaded stuff... ), what driver problem are you attempting to resolve?

---

### Post by xrc6 on 2011-02-14
> **dabl said:**
> Before installing something you downloaded, and guestimating you are new to Linux (but not to installing downloaded stuff... ), what driver problem are you attempting to resolve?

creative labs xfi driver for linux. its a .tar file. there are files inside of it.
I know some downloadable files are executable like how it is in Windows and will just install, but for this driver i don't know what file here is executable or basically how i get the files to go where there suppose to.

*edit. ok i found instructions but need help. they say this:
> In terminal,

1) Goto source directory
2) Execute make command as root
   make
   make install

those are the most noob unfriendly instructions i'v ever seen. So my driver .tar file is located in download folder, i know how to open terminal, i just don't get what to type.

---

### Post by jbiggs12 on 2011-02-14
cd to the directory that the files are in:
```
cd /path/to/dir
```
and then type
```
sudo make
```
enter your password, and then type
```
sudo make install
```
and pray. if you have all of your dependencies, it should work. if not, you should get a compile error and it should say some mean things about how you don't have certain dependencies installed.

---

