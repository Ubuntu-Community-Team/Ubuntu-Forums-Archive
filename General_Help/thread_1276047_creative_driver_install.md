---
title: "creative driver install"
date: 2009-09-26
forum: General Help
---

### Post by Lttman on 2009-09-26
Hello,

I am very new to using linux (as in I installed it 2 days ago, but I did figure out how to update to 9) I am trying to install a creative driver and I have the file downloaded.  The instructions in the readme say:

Quick install


=============

In terminal,


1) Goto source directory

2) Execute make command as root

   make

   make install 			 		

I have set the source directory in the terminal... My question is how do you execute "make command as root"?

thanks

---

### Post by StuartN on 2009-09-26
> **Lttman said:**
> I have set the source directory in the terminal... My question is how do you execute "make command as root"?

"Root" is the superuser. To do something as the superuser, you use the sudo command, so you would need to open the terminal and navigate to the directory where your source is and then:

```
sudo make
sudo make install
```

You will be prompted to confirm with your password.

---

