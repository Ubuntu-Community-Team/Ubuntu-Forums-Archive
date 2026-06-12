---
title: "Error Message: Software Index is Broken"
date: 2010-09-02
forum: General Help
---

### Post by techiewannabe on 2010-09-02
I get the following message when I try to add or remove programs. This includes when I try to use the Update Manager:


[INDENT]Software index is broken. It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/INDENT] 

 When I follow this advice, I get the following message:
 

 [INDENT]tom@Compaq:~$ sudo apt-get install -f 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 



[/INDENT]If anyone can offer suggestions about this problem, I would appreciate it. Although I've been using Ubuntu for a while, I'm not very confident with the command line (unless I am copy and pasting commands!)


Thanks.

---

### Post by Soul-Sing on 2010-09-02
you should kill/close all -apt/dpkg/software managers

try again: ```
sudo apt-get update
```

no good? Try:

```
sudo rm /var/lib/dpkg/lock 
```

```
sudo apt-get update
```

---

### Post by Soul-Sing on 2010-09-02
you should kill/close all -apt/dpkg/software managers

try again: ```
sudo apt-get update
```

no good? Try:

```
sudo rm /var/lib/dpkg/lock 
```

```
sudo apt-get update
```

no good?

```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

---

### Post by techiewannabe on 2010-09-02
Thanks to each of you for your suggestions. I followed each step you offered. Unfortunately, the problem continues. When I try to use the Update Manager, I get a series of messages. You can see them below:

Other ideas?

Thanks in advance.

[ATTACH]168277[/ATTACH]

[ATTACH]168278[/ATTACH]

[ATTACH]168279[/ATTACH]

[ATTACH]168280[/ATTACH]

[ATTACH]168281[/ATTACH]

---

### Post by Soul-Sing on 2010-09-02
thx for the additional info

could you please copy the errors after:

```
sudo apt-get update
```
```
sudo apt-get safe-upgrade
```

with error codes and the package errors.

---

### Post by techiewannabe on 2010-09-02
Leoquant:

Thanks for your willingness to help with this. 

Here is the text following the first command:

[INDENT]tom@Compaq:~$ sudo apt-get update
[sudo] password for tom: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,076B]                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty/partner Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Fetched 3,809B in 6s (603B/s)                                                  
Reading package lists... Done
tom@Compaq:~$ 
[/INDENT]
The second command yielded this:

[INDENT]tom@Compaq:~$ sudo apt-get safe-upgrade
E: Invalid operation safe-upgrade
tom@Compaq:~$ 

[/INDENT]Thanks.

---

### Post by Soul-Sing on 2010-09-03
So there are two  "broken" packages

```
gksudo nautilus
```

navigate to

 /var/lib/dpkg/info

remove the two "broken" files with the exact name in the errormessages.. There is a search option rightabove your screen...
close nautilus! Then:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by techiewannabe on 2010-09-03
Leoquant:
 
Thanks for your help with this problem. The problem is resolved but not for the reasons mentioned in this thread. I had been experiencing other problems with Lucid, not mentioned in this thread, and decided to do a clean install. Since the install, I have been able to update my software as expected. 
 
I feel a bit guilty that I didn't have a chance to try your solution before the clean install. I hate to see you go to the trouble of exploring the problem and then finding that I didn't take your advice. (By the time I received your posting, I had already done the clean install.)
 
I appreciate your time and thoughts about my Ubuntu hassles.
 
Thanks.

---

### Post by Soul-Sing on 2010-09-03
techiewannabe no problem, and have fun with linux! :KS

---

### Post by techiewannabe on 2010-09-03
Thanks.

---

### Post by Ykcir on 2010-09-04
I am having similar problems also. Can't get any updates or packages installed. I get the following message when I try to use the package manager or update manager:
E:Malformed line 54 in source list/etc/apt/sources.list (URI parse)
E:The list of sources could not be read.
Go to the repository dialog to correct the problem
E:_cache->open() failed, please report.
I am new to Ubuntu 10.04 and have already installed and uninstalled it four times because of various problems and I hope I will not have to do it again because of this. Any solutions? And does anyone else think that Ubuntu is kinda complicated?

---

### Post by techiewannabe on 2010-09-04
Thanks to everyone for your help. I decided to reinstall Jaunty which I had been using for quite a while without problems.

---

### Post by Soul-Sing on 2010-09-17
> **techiewannabe said:**
> Thanks to everyone for your help. I decided to reinstall Jaunty which I had been using for quite a while without problems.

Its a 1 week old post, but jaunty reaches EOL very soon...

---

### Post by techiewannabe on 2010-09-18
Thanks, leoquant.
I haven't given up on 10.4 I'll go back to it at some time.

---

