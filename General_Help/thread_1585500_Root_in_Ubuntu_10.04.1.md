---
title: "Root in Ubuntu 10.04.1"
date: 2010-09-30
forum: General Help
---

### Post by Detroit_Bad_Boy on 2010-09-30
I have tried to install various programs and apps with no luck as it asks if I am 'root'. I type 'root' in a terminal but am told that there is no root. However, when I do a file search it shows root to be existing in the OS. When I try to access it, I am told that I do not have admin rights. Why do I feel like I am chasing my tail? Any help with figuring this problem out?

---

### Post by Cavsfan on 2010-09-30
> **Detroit_Bad_Boy said:**
> I have tried to install various programs and apps with no luck as it asks if I am 'root'. I type 'root' in a terminal but am told that there is no root. However, when I do a file search it shows root to be existing in the OS. When I try to access it, I am told that I do not have admin rights. Why do I feel like I am chasing my tail? Any help with figuring this problem out?

Use "sudo" as a prefix to make your userid have temp. root access.
Use "gksu" for the same reason for gui apps.

---

### Post by searchfgold6789 on 2010-09-30
When you need to be root when using a terminal, use
```
sudo <command>
```

---

### Post by kerry_s on 2010-09-30
if your the first user you should be admin.
ubuntu is a sudo/gksudo system, you use that to gain root privileges.

sudo is used in the terminal
gksudo is for graphical apps

example: root nautilus (file manager)
press-> alt+f2
type-> gksudo "nautilus --no-desktop /"

example: terminal
sudo apt-get update

ubuntu has several ways to install programs.
the main ways are "software center" or "synaptic package manager".

there's no need to use the terminal.

---

### Post by swagatmishra on 2010-09-30
In addition to sudo<command>
use sudo -s to get a root shell where you can run any of your applications.
refer man sudo for details

---

### Post by Rubi1200 on 2010-09-30
> **swagatmishra said:**
> In addition to sudo<command>
use sudo -s to get a root shell where you can run any of your applications.
refer man sudo for details
Actually, ```
sudo -i
``` is the preferred method:
[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

