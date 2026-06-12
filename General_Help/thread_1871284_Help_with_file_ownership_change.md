---
title: "Help with file ownership change"
date: 2011-10-28
forum: General Help
---

### Post by w1av on 2011-10-28
Hi,

I just installed the latest UBUNTU as a dual boot and everything is fine except I don't seem to remember how to change a files ownership (root owns it) to be able to delete it and replace it with another file. I am running conky, and I have a better conky.conf file I want to use. As far as I know the conky.conf file resides in /etc/conky. If I try to delete the conky.conf file that is in there  now, I get "permission denied" or some kind of warning. I have tried in a terminal to be root, using sudo su but nothing works. I have not been messing with Linux in a while and have forgotten some things I used to know. So what I am trying to do is replace the default conky.conf with my own customized one. But since root owns the default file I cant delete it and put mine in there. Please help!!!:confused:

---

### Post by ajgreeny on 2011-10-28
There is no need to delete or replace the file **/etc/conky/conky.conf.**

Simply rename the configuration file you wish to use as **.conkyrc** and put it in your home folder.  Now restart conky and that file will be used.  Don't forget the . at the start of the filename.

---

