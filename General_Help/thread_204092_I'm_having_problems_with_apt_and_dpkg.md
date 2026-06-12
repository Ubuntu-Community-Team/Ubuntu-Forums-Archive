---
title: "I'm having problems with apt and dpkg"
date: 2006-06-26
forum: General Help
---

### Post by Johnsie on 2006-06-26
I wanted to install xchat but I got:
> 
john@st2:~$ sudo apt-get install xchat
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


So then I did:
> 
john@st2:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 5563 package `ubuntu-standard':
 `Depends' field, invalid package name `
john@st2:~$



Anyone know how to fix my problem? Thanks in advance :-)

---

### Post by Johnsie on 2006-06-26
please help... I don't want to have to go back to windows :.(

---

### Post by JoWilly on 2006-06-26
Run synaptic, in the menu select fix broken packages (you can then see them by selecting the personal filter) and then click apply.

---

