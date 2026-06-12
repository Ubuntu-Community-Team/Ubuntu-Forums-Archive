---
title: "Newbie: Permissions and Root"
date: 2011-11-13
forum: General Help
---

### Post by eddo2k on 2011-11-13
Hello,

I'm an Ubuntu newbie. This one stumped me yesterday. I have a book which I'm reading that has some scripts I want to launch from the terminal. I'm pretty sure my issues are permissions related. 

I have a main account on my Ubuntu machine called "VM". When logged into the GUI I can take the folder with the scripts and copy it from CD to my desktop. 

The problem I have is that from the terminal I cannot access the VM home folder to get to the folder with the scripts. This happens with both the VM account and using the sudo -i command for the root account. 

The error I get is:

**FROM VM ACCOUNT**

vm@ubuntu:~$ dir
Desktop    Downloads	     Music     Public	  Videos
Documents  examples.desktop  Pictures  Templates
vm@ubuntu:~$ 
vm@ubuntu:~$ 
vm@ubuntu:~$ cd /desktop/scripts
bash: cd: /desktop/scripts: No such file or directory
vm@ubuntu:~$ cd /desktop
bash: cd: /desktop: No such file or directory
vm@ubuntu:~$ 

**FROM ROOT ACCOUNT VIA SUDO -I**

vm@ubuntu:~$ sudo -i
[sudo] password for vm: 
root@ubuntu:~# 
root@ubuntu:~# 
root@ubuntu:~# cd /
root@ubuntu:/# dir
bin    dev   initrd.img  media	proc  sbin     sys  var
boot   etc   lib	 mnt	root  selinux  tmp  vmlinuz
cdrom  home  lost+found  opt	run   srv      usr
root@ubuntu:/# cd /home
root@ubuntu:/home# dir
vm
root@ubuntu:/home# cd /vm
-bash: cd: /vm: No such file or directory
root@ubuntu:/home# 

Please let me know what I'm doing wrong. Thank you ;-)

---

### Post by RiHL on 2011-11-13
Two things :) :
1) / is the root folder, it is like C:\ in windows
/home is C:\Users
but there isnt any /vm. This is like you want to go into C:\VM
Instead of "cd /vm" (or "cd /desktop/scripts") type "cd vm" (or "cd desktop/scripts")

2)Files and folders are case-sensitive:
desktop is another folder than DESKTOP and another than DeSkToP.
So, your commands should look like:
```

vm@ubuntu:~$ dir
Desktop    Downloads         Music     Public      Videos
Documents  examples.desktop  Pictures  Templates
vm@ubuntu:~$ cd Desktop/Scripts
vm@ubuntu:Scripts$

```or:
```

vm@ubuntu:~$ sudo -i
[sudo] password for vm: 
root@ubuntu:~# cd /home/vm/Desktop/Scripts
root@ubuntu:Scripts$

```

---

### Post by eddo2k on 2011-11-13
RiHL,
 
You are spot on so thank you. One question:
 
How come in the first example you did not have to use the / but in the second example you did? Is it because it was the next folder the current directory?
 
ex.
 
cd Desktop/scripts 
 
vs. 
 
cd **/**home/vm/Desktop/scripts 
 
Either way it worked and you saved me some headaches ;-) Thank you!

---

### Post by RiHL on 2011-11-13
This is because of *current working directory* - when you open terminal, your current working directory (cwd) is /home/vm. So, you can only type "cd Desktop" and your cwd will be /home/vm/Desktop. In the second example, your cwd was "/root" (the roots home), so you had to type the whole path.

---

### Post by eddo2k on 2011-11-13
Excellent, thank you :D

---

