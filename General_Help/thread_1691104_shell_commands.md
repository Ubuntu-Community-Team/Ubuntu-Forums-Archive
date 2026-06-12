---
title: "shell commands"
date: 2011-02-19
forum: General Help
---

### Post by michaelkhan3 on 2011-02-19
Does any one know how I can get this information with shell commands in Ubuntu?

I need to get :

The user name. I know i can use whoami command for that 
The user ID
The host name
and the machine type. 

I think there might be something to get these by using the set command but I dont know how. 

Any help is appreciated and Thanks in advance

---

### Post by metalf8801 on 2011-02-19
Do you know about the man pages? When you want info about a command you put man in front of it and then it tells you about that command and about options for that command. To close and man page press q

Or are you looking for a list of the commands available for Ubuntu? 

I hope this helps 
Dan
Never mind please see what SeijiSensei said

---

### Post by SeijiSensei on 2011-02-19
User ID:  "id username"

Hostname: "hostname"

Machine type: "uname -a"

The last one reports on the current kernel.  If by "machine type" you mean i386 vs amd64, uname will tell you that.  Most of the information about the machine is stored in the /proc directory structure.

---

### Post by michaelkhan3 on 2011-02-19
Thanks I thin that works

---

