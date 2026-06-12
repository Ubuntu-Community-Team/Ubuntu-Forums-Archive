---
title: "How Do I open executable files not .exe files"
date: 2010-06-27
forum: General Help
---

### Post by alperkayisi on 2010-06-27
Hey guys I just installed the nmap for port scanning and then run ./configure , make , make install command respectively. It works and then I successfully installed nmap under /usr/local/bin .  nmap is a executable file not .exe . so my question is how can I open it . 

thanks a lot

---

### Post by GreenN00b on 2010-06-27
Just try typing:
```
nmap
```
in a terminal. If that does not work try full path:
```
/usr/local/bin/nmap
```
If still does not work post the error message here.

---

### Post by alperkayisi on 2010-06-27
both of works. but when I type this command, the interface did not come to my screen. according to output, when I type nmap, I suppose to type something in terminal. what can I do for using interface

---

### Post by GreenN00b on 2010-06-27
nmap is a command line based utility. For example typing
```
nmap localhost
```
will scan your computer. In order to use a graphical user interface you have to install one. Use Synaptic Package Manager from System\Administration menu to install a nmap Gui like zenmap or nmapsi4. This will appear in synaptic when doing a quick search for "nmap gui"

---

### Post by alperkayisi on 2010-06-27
I appreciate . I am gonna try to do that. and I will let u know whether I install nmapsi4 or not :)

---

### Post by alperkayisi on 2010-06-27
Thanks a lot it works :)

---

### Post by prodigy_ on 2010-06-27
In Linux executable files usually don't have .exe extension (unless they're Windows binaries that your run in Wine). Instead an executable is simply any file with executable permission set. (More about Linux file permissions, for example, [here](http://www.freeos.com/articles/3127/).)

---

### Post by pskt on 2010-06-27
i have a dhcp server running so i use 

```
 nmap 10.1.1.0/24
```to figure out which computers grabbed what and what they got open...



> 
Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-06-27 17:45 CDT
Interesting ports on 10.1.1.1:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Interesting ports on 10.1.1.38:
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
the usage of 

./   is the current directory, to run an executable you type its name to execute from your PATH variable, but if it's in the current directory, you need to specify explicitly that you're talking bout the current directory



.exe is the extension given to DOS/WIN executable files.

---

### Post by GreenN00b on 2010-06-27
You're welcome.
Please mark thread as solved from thread tools menu.

---

