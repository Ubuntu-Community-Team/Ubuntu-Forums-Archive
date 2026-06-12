---
title: "Help Help!  I cannot install applications due to corrupt file."
date: 2009-07-28
forum: General Help
---

### Post by bleemme on 2009-07-28
Hey Guys, 

 Nice Forum! Here is the deal. Being a former Windows fan, I'm new to Xubuntu/Linux (Jaunty 9.04) so please bear with me if I don't understand the linux lingo :D. 

I tried installing Open Office and in the process of doing so my computer crashed. After trying to reinstall the same program again using "Add/remove" application, I get the following error:: 

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.So using the "terminal", I ran sudo dpkg --configure -a. I get this: 

> marc@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for marc: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0016' near line 1:
 newline in field name `#padding'
marc@ubuntu:~$ 

What should I do next? I just want to be able to add/remove programs again. Your help is greatly appreciated.

---

### Post by plucky on 2009-07-28
> 
dpkg: parse error, in file `/var/lib/dpkg/updates/0016' near line 1:
newline in field name `#padding'

What should I do next? I just want to be able to add/remove programs again. Your help is greatly appreciated.



Delete the file **0016** as it is corrupt.Open a terminal ```
cd /var/lib/dpkg/updates
ls
sudo rm 0016
sudo apt-get update
```

The ls command is to make sure you are in the correct directory before you use the "sudo rm" command.Just in case you made a typo when changing directory.


Good luck

---

### Post by bleemme on 2009-07-28
thanks, still can't seem to get it to work. Here is what I did. 


> marc@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for marc: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0016' near line 1:
 newline in field name `#padding'
marc@ubuntu:~$ cd /var/lib/dpkg/updates
marc@ubuntu:/var/lib/dpkg/updates$ ls
0000  0003  0006  0009  0012  0015  0018  0021  0024  0027  0030  0033  0036
0001  0004  0007  0010  0013  0016  0019  0022  0025  0028  0031  0034  0037
0002  0005  0008  0011  0014  0017  0020  0023  0026  0029  0032  0035  tmp.i
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0016
marc@ubuntu:/var/lib/dpkg/updates$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [49.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release    
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages [59.3kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [122kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages [2391B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources [17.2kB]         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources [522B]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages [23.1kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources [5238B]     
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2391B] 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [37.4kB]       
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages [14B]    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources [14B]     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [522B]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [41.6kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [11.7kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [3933B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [1349B]
Fetched 429kB in 2s (144kB/s)                         
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
marc@ubuntu:/var/lib/dpkg/updates$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0017' near line 1:
 newline in field name `padding'
marc@ubuntu:/var/lib/dpkg/updates$ ls
0000  0002  0004  0006  0008  0010  0012  0014  0017  0019  0021  0023  0025  0027  0029  0031  0033  0035  0037
0001  0003  0005  0007  0009  0011  0013  0015  0018  0020  0022  0024  0026  0028  0030  0032  0034  0036  tmp.i
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0016
rm: cannot remove `0016': No such file or directory
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0016
rm: cannot remove `0016': No such file or directory
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0016
rm: cannot remove `0016': No such file or directory
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0017
marc@ubuntu:/var/lib/dpkg/updates$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
marc@ubuntu:/var/lib/dpkg/updates$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0018' near line 23 package `python-uno':
 EOF after field name `'
marc@ubuntu:/var/lib/dpkg/updates$ lm
bash: lm: command not found
marc@ubuntu:/var/lib/dpkg/updates$ ls
0000  0002  0004  0006  0008  0010  0012  0014  0018  0020  0022  0024  0026  0028  0030  0032  0034  0036  tmp.i
0001  0003  0005  0007  0009  0011  0013  0015  0019  0021  0023  0025  0027  0029  0031  0033  0035  0037
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0018
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0019
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 20
rm: cannot remove `20': No such file or directory
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0020
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0021
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0022
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0023
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0024
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0025
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0026
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0027
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0028
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0029
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0030
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0031
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0033
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0034
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0032
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0035
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0036
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm 0037
marc@ubuntu:/var/lib/dpkg/updates$ sudo rm tmp.i
marc@ubuntu:/var/lib/dpkg/updates$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
marc@ubuntu:/var/lib/dpkg/updates$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
marc@ubuntu:/var/lib/dpkg/updates$ 


---

### Post by Coder543 on 2009-07-28
wait, jk (about my previous post). You might just want to back up your home folder(s), and reinstall at this point. What did you do to cause this?

---

### Post by bleemme on 2009-07-29
> **Coder543 said:**
> wait, jk (about my previous post). You might just want to back up your home folder(s), and reinstall at this point. What did you do to cause this?


the best solution was to go into windows vista and uninstall xubuntu and reinstall. everything works like a charm now.

---

