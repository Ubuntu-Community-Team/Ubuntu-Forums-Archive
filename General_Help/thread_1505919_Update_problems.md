---
title: "Update problems"
date: 2010-06-09
forum: General Help
---

### Post by ennoil on 2010-06-09
For the last week or so I have not been able to get updates. It dies with the following:

```
$ sudo apt-get update
[sudo] password for jkennedy: 
Get:1 http://archive.canonical.com lucid Release.gpg [189B]
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                            
Get:2 http://security.ubuntu.com lucid-security Release.gpg [189B]                                                         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                                        
Get:3 http://us.archive.ubuntu.com lucid Release.gpg [189B]                                          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                
Hit http://archive.canonical.com lucid Release                                                                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                         
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:4 http://security.ubuntu.com lucid-security Release [38.5kB]     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                         
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:6 http://packages.medibuntu.org lucid Release.gpg [197B]
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US               
Hit http://us.archive.ubuntu.com lucid Release 
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US  
Hit http://packages.medibuntu.org lucid Release                      
Get:7 http://us.archive.ubuntu.com lucid-updates Release [38.5kB]    
E: Method gpgv has died unexpectedly!                                                                                                                                           
E: Sub-process gpgv received signal 7.
```My sources.lst looks like:

```
$ more /etc/apt/sources.list | grep -v ^#
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```How can I fix this? I have not updated in a while.
Thanks,
John

---

### Post by dcstar on 2010-06-10
> **ennoil said:**
> For the last week or so I have not been able to get updates. It dies with the following:
........
How can I fix this? I have not updated in a while.
Thanks,
John

Never update from the default repositories, select a different software source close to you and try again.

---

### Post by ennoil on 2010-06-10
I chose the best location from Software Sources:
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid main restricted
And still get the same result

```
$ sudo apt-get update
Get:1 http://mirrors.ccs.neu.edu lucid Release.gpg [189B]
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid/main Translation-en_US                                                                     
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid/restricted Translation-en_US                                     
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid/universe Translation-en_US                                       
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid/multiverse Translation-en_US                                     
Get:2 http://mirrors.ccs.neu.edu lucid-updates Release.gpg [189B]                                             
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-updates/main Translation-en_US                                                              
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-updates/restricted Translation-en_US                             
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-updates/universe Translation-en_US                               
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-updates/multiverse Translation-en_US                             
Get:3 http://mirrors.ccs.neu.edu lucid-security Release.gpg [189B]                                                                  
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-security/main Translation-en_US                                                             
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-security/restricted Translation-en_US                                                       
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-security/universe Translation-en_US                                                         
Ign http://mirrors.ccs.neu.edu/ubuntu/ lucid-security/multiverse Translation-en_US                                                       
Get:4 http://mirrors.ccs.neu.edu lucid Release [57.2kB]                                                                                  
Get:5 http://mirrors.ccs.neu.edu lucid-updates Release [38.5kB]                                                                          
Get:6 http://mirrors.ccs.neu.edu lucid-security Release [38.5kB]                                                                                            
Get:7 http://archive.canonical.com lucid Release.gpg [189B]                                                                                                          
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                              
Get:8 http://packages.medibuntu.org lucid Release.gpg [197B]           
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US        
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US    
Hit http://archive.canonical.com lucid Release                         
Hit http://packages.medibuntu.org lucid Release                        
E: Method gpgv has died unexpectedly!                                                                                                                                           
E: Sub-process gpgv received signal 7.
```

Should I download the latest gpgv and install by hand?
John

---

### Post by fragos on 2010-06-10
I always use the Gnome Update Manager and Software Sources. Software Sources allows you to select the server and if you drop down the list you'll see an option for Other..., select it and then the Select Best Server Button.

---

