---
title: "./ doesn't work?!"
date: 2005-02-08
forum: General Help
---

### Post by kurisutofaa on 2005-02-08
I'm trying to install vmware. I went to the folder where is vmware install file. All files/folders in this folder are 

bin                etc                installer          man
doc                FILES              lib                vmware-install.pl

then I enter command:
$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found
doesn't work   :confused: 

then I do like this:
$ sudo -s
# ./vmware-install.pl
bash: ./vmware-install.pl: Permission denied

did I do something wrong?  :confused:

---

### Post by RichardA on 2005-02-08
Do 'ls -l' to see permissions.

You're trying to execute something you downloaded, but the executable attribute needs setting first (chmod u+x <filename>).

---

