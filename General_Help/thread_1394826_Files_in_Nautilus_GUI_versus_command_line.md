---
title: "Files in Nautilus GUI versus command line"
date: 2010-01-31
forum: General Help
---

### Post by Slates on 2010-01-31
Could somebody please explain or point me to some documentation that will explain the relationship between the Ubuntu (9.1) GUI file browser and what I see on the command prompt using ls -a ?

If I look in the GUI under root I see a dozen or so directories and a few files.

If I do ls -a at the command prompt I see these dozen directories, but also a good two dozen more. Ive checked show hidden files etc in the GUI, so I dont understand what Im missing here !

In particular, Ive been following some notes on how to implement SSH keys. To store them I created a directory called ~/.SSH (what does the  mean, root ?). So I can see the directory at the command prompt under ls -a, but not via the GUI.

Any education would be welcomed !

---

### Post by rnerwein on 2010-01-31
hi
you can even see it in the GUI --> type ctrl h and then you will see the doted files
dit you create die file .SSH with capital letter then you have to edit your /etc/ssh config files. linux is case sensitive.
to implement ssh keys see: man ssh-keygen, man sshd_config and ssh_config
ciao

---

