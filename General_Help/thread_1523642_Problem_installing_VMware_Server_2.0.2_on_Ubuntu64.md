---
title: "Problem installing VMware Server 2.0.2 on Ubuntu64 10.04"
date: 2010-07-03
forum: General Help
---

### Post by mchoo on 2010-07-03
Hi all... I want to use my new HP ProBook 6540b to run Ubuntu64 and VMware. Ubuntu installed without a glitch, but VMware won't.... After a bit of googling, I found an article on Ubuntu help section ([https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)) on how to install VMware on 10.04 and other versions. I downloaded the script that the article suggested, and followed the instructions to run it. But, the script won't run (see below)

/tmp/vmwareinst$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh ./VMware-server-2.0.2-203138.x86_64.tar.gz 
./vmware-server-2.0.x-kernel-2.6.3x-install.sh: 3: Syntax error: Unterminated quoted string

What did I do wrong?

---

### Post by derekshaw on 2010-07-04
I just did this, to, but it worked perfectly for me.  ubuntu 10.04, 64 bit, vmware server 2.0.2

I have the vmware tar archive and script set up like this:

```
rrti@2010JUL-01:/0data/vmware$ ls -l
drwxrwxrwx  raducotescu-vmware-server-linux-2.6.3x-kernel-592e882
-rw-r--r--  VMware-server-2.0.2-203138.x86_64.tar.gz
```

I cd into the directory raducotescu-vm.... 
then I execute (as root)
 ./vmware-server-2.0.x-kernel-2.6.3x-install.sh ../

Hope that helps.  

Still not quite functional, though, as I can't access the VM's console w/ firefox on the server host.

---

### Post by dcstar on 2010-07-04
> **mchoo said:**
> Hi all... I want to use my new HP ProBook 6540b to run Ubuntu64 and VMware. Ubuntu installed without a glitch, but VMware won't.... After a bit of googling, I found an article on Ubuntu help section ([https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)) on how to install VMware on 10.04 and other versions. I downloaded the script that the article suggested, and followed the instructions to run it. But, the script won't run (see below)

/tmp/vmwareinst$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh ./VMware-server-2.0.2-203138.x86_64.tar.gz 
./vmware-server-2.0.x-kernel-2.6.3x-install.sh: 3: Syntax error: Unterminated quoted string

What did I do wrong?
Just do one command:
```
sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
```
and post **all** VM issues in the Virtualization forum.

---

