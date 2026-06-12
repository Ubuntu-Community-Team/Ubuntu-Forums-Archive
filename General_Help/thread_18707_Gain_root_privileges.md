---
title: "Gain root privileges"
date: 2005-03-08
forum: General Help
---

### Post by luis1975 on 2005-03-08
Hi, Linux patners

I am new in the linux world. 
And I did install my ubuntu Linux yesterday. 
I would like to know, how to get the root privileges. The reason of my question is this, when I installed the Operating System, it never asked me the password about root. Somewhere in the instalation appeared a message about the "sudo" command to get root privileges. 
Can somebody help me?
Thank you.

luis1975

PD: Sorry for my English, is not very good.

---

### Post by Kimm on 2005-03-08
well, I dont remember being asked for a root password eighter... I think its the same password as the password for the user that you create...

if you want to use the sudo command... ehm, imagine you want to delete a file that you must have root privelages to delete (perhaps a .deb packages converted from rpm to .deb using alien), you type this in console:

> 
sudo rm -f yourfile.deb


of if you want to run synaptic...

> 
sudo synaptic


the computer will ask for the root password when you run this command.
If you want to manage files in nautilus as root, you can type:

> 
sudo nautilus


I dont recommend doing that unless you know what your doing though...


Have fun :)

PS.
I dont think this was the right forum for this topic...

---

### Post by krusbjorn on 2005-03-08
when executing a sudo command, you are asked for your own password.

if you want to be able to enter "su"-mode, i think you can just set a root password in Computer->System Configuration->User and Groups (or something like that).

if i remember correctly, this is how i did it. could be wrong though.

---

### Post by GrapeApe on 2005-03-08
The root account is disabled when you first install Ubuntu. The first user created during the installation has administrative rights on the system, and can run programs as root with sudo, using only their normal user password. For example: sudo apt-get update.

If you wish to use the root account in more traditional UNIX fashion, you can set the root password by typing sudo passwd root. This will allow you to use su or login as root on the console.

If you need a shell with root privileges, run **sudo -s**.

All uses of sudo will require the user's password.

From: [http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

---

