---
title: "Help! Firestarter Will Not Install"
date: 2010-05-24
forum: General Help
---

### Post by torresmagnifico on 2010-05-24
After installing Ubuntu 10 and getting my wireless Internet connection  up and running I thought I would install a firewall.

Firestarter is already listed under the *get software* in the *software  centre*.

However, when I attempt to install I get a dialogue box that states:

*Previous Installation has not Been Completed*; it then goes on to  say '...*you have to repair this before you can install or remove any  further software*.'

When I attempt to run the Synaptic Package Manager, I get the following  message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure  -a' to correct the problem. 

E: _cache->open() failed, please report.

This is what I got from the Terminal:

torres@ubuntu:~$ sudo dpkg -configure -a

[sudo] password for torres: 

dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages
[*];

Use `dselect' or `aptitude' for user-friendly package management;

Type dpkg -Dhelp for a list of dpkg debug flag values;

Type dpkg --force-help for a list of forcing options;

Type dpkg-deb --help for help about manipulating *.deb files;

Type dpkg --license|--licence for copyright licence and lack of warranty  (GNU GPL)
[*].

Options marked
[*] produce a lot of output - pipe it through `less' or  `more' !

torres@ubuntu:~$ ^C


My question is simply, how do I repair this problem and get Firestarter installed?

---

### Post by -humanaut- on 2010-05-24
Firestarter is defunct now I believe I'd recommend using UFW you can turn it on with sudo ufw enable

you can download a GUI front-end if you want.

---

### Post by oldos2er on 2010-05-24
What a difference one little "-" makes. Copy and paste ```
sudo dpkg --configure -a
``` into a terminal.

You might want to look into gufw instead of Firestarter.

---

### Post by torresmagnifico on 2010-05-25
Thanks for all your input! 

                                 Terminal:
 

 torres@ubuntu:~$ sudo dpkg --configure -a 
 [sudo] password for torres:  
 dpkg: status database area is locked by another process 
 torres@ubuntu:~$  
 

 Synaptic...
 

 Unable to get exclusive lock 
  
 This usually means that another package management application (like apt-get or aptitude) is already running.  Please close that application first.


Any help would be greatly appreciated otherwise my time with Ubuntu is going to have to be terminated.

---

### Post by torresmagnifico on 2010-05-25
Case has now been solved, so many thanks for your help! :)

---

### Post by -humanaut- on 2010-05-25
Please mark as thread as "SOLVED" thanks.

---

