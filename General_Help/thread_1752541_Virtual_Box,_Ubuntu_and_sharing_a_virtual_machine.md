---
title: "Virtual Box, Ubuntu and sharing a virtual machine"
date: 2011-05-07
forum: General Help
---

### Post by Dobly on 2011-05-07
I'm not sure if this is a Virtualbox question or a Ubuntu question. Despite that I reckon the gurus here will have an answer to this one. 

I my laptop I have just installed 11.04. So far so good. I love it. 

On this lap top I have two users. Myself and my wife each have out own logins. 

I installed VirtualBox and in no time flat I had a Windows XP virtual machine running. This I installed so my wife can use Excel (she is not keen on Open Office's Calc). This VM I created in my login, not my wifes .

Now, when my wife logs  and runs VirtualBox, the Windows XM virtual machine I created in my login, is not there. 

I sort of suspect this is correct and proper behavior, however, I want it changed. I want my wife to be able to use the Win XM VM i created from her login. I don't what to have to install it there as well (or again)

---

### Post by ~Plue on 2011-05-07
If you don't need the virtual machine machine to be synchronized with both users, move/copy the harddisk.vdi file from the 'VirtualBox VMs' folder in your home directory (or .VirtualBox if you're using an older version) (you also might need to change the ownership of the file to the other user) and while creating a new machine, specify the .vdi file to use as a harddisk.

Else, instead of copying the .vdi file, change the permissions of your home directory/move the file to somewhere accessible from both users

---

### Post by Thewhistlingwind on 2011-05-07
Install Virtualbox on your wifes login then copy the installed disk image to her .virtualbox file in home directory?

(Delete old image to account for licensing issues.)

---

