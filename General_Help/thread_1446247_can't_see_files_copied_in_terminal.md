---
title: "can't see files copied in terminal"
date: 2010-04-03
forum: General Help
---

### Post by gorlop on 2010-04-03
I copied several folders over to a thumbdrive in Terminal, but I can't see the folders when I view the thumbdrive on any other system (tried a machine with xp and another with Ubuntu). I went back to the original machine where I did the coping and viewed the thumbdrive's contents in Terminal, and it shows everything to be there that I had copied. Is there a step I'm missing? I copied using cp -r. 

The reason I'm doing this is that the Ubuntu installation on the original machine is freezing up and I just want to backup some of the files before reinstalling Ubuntu.

---

### Post by Brandon Williams on 2010-04-03
Are you absolutely certain that the files were copied onto the thumbdrive? Is it possible that they were copied into a directory that appears to be on the thumbdrive, but in fact is not? Maybe it's a symlink to a directory on another HDD? Use stat to view the details of one of the problem files and another file on the thumbdrive, one that it showing up on other machines. Do they both indicate the same Device value?

---

