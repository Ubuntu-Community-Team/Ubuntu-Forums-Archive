---
title: "Help! Problem with restrictions"
date: 2006-01-31
forum: General Help
---

### Post by Da Cosmonaut on 2006-01-31
Hi,

I'm trying to configure my modem and everything is going right since I'm following the steps in the wiki of the ubuntu page but a step requires me to add to file to the  /etc/udev/rules.d/ but I have no access to it at all. A messages appears telling me I have not enough permissions to move the file there. I'm still using the user I created during the installation but I still can't. What can I do?

Thanks in advance

---

### Post by Gcool on 2006-01-31
You'll have to do this as root. So just put "sudo" in front of the command you're entering.

---

### Post by Da Cosmonaut on 2006-01-31
But the problem is I don't know how to do it using a command, I'm using the text editor. Could you tell me how? I have to create a file named 10-local.rules in the /etc/udev/rules.d/ directory with the following commands:

#ltmodem 
KERNEL="ttyLTM0", SYMLINK="modem"

tia

---

### Post by Gcool on 2006-01-31
You can do it as follows:

* sudo nano /etc/udev/rules.d/10-local.rules
* paste your text/code
* ctrl-x -> press "y" to  save the changes

---

### Post by Da Cosmonaut on 2006-01-31
thanks a lot, I'll try it and let you know

---

