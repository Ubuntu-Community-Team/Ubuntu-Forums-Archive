---
title: "piano booster"
date: 2010-09-20
forum: General Help
---

### Post by xdweaver on 2010-09-20
I need a easy to follow guide to help me install piano booster on ubuntu 10.04. I have tried to add to the software sources and nothing i am lost. So if anyone might have the time to help me that would be great. Thanks

---

### Post by marshag63 on 2010-09-20
[http://sourceforge.net/apps/mediawiki/pianobooster/index.php?title=Piano_Booster_User_Manual](http://sourceforge.net/apps/mediawiki/pianobooster/index.php?title=Piano_Booster_User_Manual)

Copy this line by line into a terminal (you will have to give your password to use sudo - its the same one you use to login to ubuntu):

sudo apt-repository ppa:racb/extra
sudo apt-get update
sudo apt-get install pianobooster

Hope this helps!

MarshaG.

---

### Post by xdweaver on 2010-09-20
okay so i did what you posted but got this am not sure how to fix it:

wendy@ubuntu:~$ sudo apt-repository ppa:racb/extra
[sudo] password for wendy: 
sudo: apt-repository: command not found
wendy@ubuntu:~$ sudo apt-get install pianobooster
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/racb-extra-lucid.list
E: The list of sources could not be read.
wendy@ubuntu:~$

---

### Post by xdweaver on 2010-09-20
I tried to open the synaptic package manager i get this :

E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/racb-extra-lucid.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by marshag63 on 2010-09-20
I should have verified the first command.  It should be "add-apt-repository".  

sudo add-apt-repository ppa:racb/extra
sudo apt-get update
sudo apt-get install pianobooster


I guess someone needs to let the pianobooster wiki people know the command needs changing.  

I now have pianobooster installed, but I don't have a midi keyboard....

Cool program.

Hope this helps.

MarshaG.

---

