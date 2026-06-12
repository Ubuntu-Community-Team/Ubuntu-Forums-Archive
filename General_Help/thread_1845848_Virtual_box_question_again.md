---
title: "Virtual box question again"
date: 2011-09-17
forum: General Help
---

### Post by cowboy7305 on 2011-09-17
VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. 
I know iam stupid  but every timer i look at this in synaptic i get lost i have no idea what thy want i have tried but what ever i do ,i have made a new group called windowsxp and what ever i do it tells me its disabled ,and i have no idea about adding it or some thing else to it

---

### Post by wildmanne39 on 2011-09-17
Hi, with the new version of virtualbox you are automatically added to the user group you should install it from [http://www.virtualbox.org/](http://www.virtualbox.org/)
and also install guest additions and extension packs then you will be good to go, also read the directions at the link before you install virtualbox it will answer almost all your questions.
Thank you

---

### Post by lensman3 on 2011-09-17
You need a line in /etc/group that looks like "vboxusers:x:501:xxx"  where xxx is you login name.  When you type in the command "groups xxx" you should see the group you are in as well as vboxusers. I notice in my install that the dot file for xxx is  vboxusers but the files in my home directory are xxx.  So a "ls -lan" to see the numbers used in /etc/passwd and /etc/group and are used for the group and user text names.  

You might try changing your group to vboxusers using the "newgroup vboxusers" command.  That would change the bash winto into vboxusers group.   If you can't get into the vboxusers group then the /etc/group file is still wrong.

When I type "groups" at the prompt it  dumps "Users vboxusers".  I have changed  default for what owner-group-world does.  My group is a real group not a single user which seems the default of the security people.  I limit file access with chmod and umask (my machine is a single user machine and I know who the "groups" are).

---

### Post by howefield on 2011-09-18
Go to System > Administration > Users and Groups, click on Manage Groups, scroll down to and highlight vboxusers, then click the Properties button, place a check mark against your user name and ok your way back out. You will be prompted for your password at some stage and may need a reboot for the change to take effect.

You can also do this via a terminal window. Applications > Accessories > Terminal, using the following command


```
sudo adduser username vboxusers
```

substituting username with the actual user name.

---

