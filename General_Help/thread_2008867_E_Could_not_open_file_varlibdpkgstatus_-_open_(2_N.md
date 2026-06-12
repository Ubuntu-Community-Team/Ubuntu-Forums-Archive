---
title: "E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)"
date: 2012-06-23
forum: General Help
---

### Post by destinmartin on 2012-06-23
[B][I]root@bt:~# sudo apt-get install dolphin-emu
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.

[/I][/B]
How do I fix this?

---

### Post by mörgæs on 2012-06-23
Hi, welcome to the fora.

Changed the thread title to a more informative one.

Does this help?
[http://ubuntuforums.org/showthread.php?t=1863160](http://ubuntuforums.org/showthread.php?t=1863160)

---

### Post by destinmartin on 2012-06-23
> **mörgæs said:**
> Hi, welcome to the fora.

Changed the thread title to a more informative one.

Does this help?
[http://ubuntuforums.org/showthread.php?t=1863160](http://ubuntuforums.org/showthread.php?t=1863160)


No, I get
[B][I]E: Lists directory /var/lib/apt/lists/partial is missing.
[/I][/B]

---

### Post by destinmartin on 2012-06-23
I fixed it with:
***sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status***
For future reference. 
I can Install now, but when I go to run
***sudo apt-get update***
I get:
***E: Lists directory /var/lib/apt/lists/partial is missing.***
Help?!?!

---

### Post by destinmartin on 2012-06-23
Also, 
***sudo dpkg --configure -a***
outputs:
[B][I]dpkg: parse error, in file '/var/lib/dpkg/available' near line 18743 package 'libkio5':
 EOF during value of field `Depends' (missing final newline)
[/I][/B]
fixed by making folder.
sudo mkdir /var/lib/apt/lists/partial

---

### Post by destinmartin on 2012-06-23
I cant figure this one out now 
[B][I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-source-3.2.6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsfml-network1.6 libsoil1 nvidia-cg-toolkit
The following NEW packages will be installed:
  dolphin-emu libsfml-network1.6 libsoil1 nvidia-cg-toolkit
0 upgraded, 4 newly installed, 0 to remove and 120 not upgraded.
Need to get 0B/20.8MB of archives.
After this operation, 53.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/available' near line 18743 package 'libkio5':
 EOF during value of field `Depends' (missing final newline)
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/I][/B]


](*,)

---

### Post by destinmartin on 2012-06-23
It works. For now.
sudo dpkg --clear-avail
Is all that i needed xP

---

### Post by mörgæs on 2012-06-24
Good, then please mark the thread 'solved' using 'thread tools'.

---

