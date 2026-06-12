---
title: "How to install 'Remastersys'"
date: 2009-12-09
forum: General Help
---

### Post by emigrant on 2009-12-09
hi all,
how to install 'remastersys'?
i added 
```
# Remastersys
deb http://www.remastersys.klikit-linux.com/repository remastersys/
```
in source list to do

```
sudo apt-get update
```
and
```
sudo apt-get install remastersys
```

but i get the following error:

```
$ sudo apt-get update 
Hit http://deb.torproject.org jaunty Release.gpg                               
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Hit http://lk.archive.ubuntu.com jaunty Release.gpg                            
Ign http://deb.torproject.org jaunty/main Translation-en_US                    
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US    
Ign http://lk.archive.ubuntu.com jaunty/main Translation-en_US                 
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US      
Ign http://lk.archive.ubuntu.com jaunty/restricted Translation-en_US           
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US    
Hit http://deb.torproject.org jaunty Release                                   
Ign http://lk.archive.ubuntu.com jaunty/universe Translation-en_US             
Hit http://security.ubuntu.com jaunty-security Release                         
Ign http://lk.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Hit http://lk.archive.ubuntu.com jaunty-updates Release.gpg                    
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Ign http://deb.torproject.org jaunty/main Packages                             
Ign http://lk.archive.ubuntu.com jaunty-updates/main Translation-en_US         
Ign http://lk.archive.ubuntu.com jaunty-updates/restricted Translation-en_US   
Ign http://lk.archive.ubuntu.com jaunty-updates/universe Translation-en_US     
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Ign http://lk.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US   
Hit http://deb.torproject.org jaunty/main Packages                             
Hit http://lk.archive.ubuntu.com jaunty Release                                
Hit http://security.ubuntu.com jaunty-security/main Sources                    
Hit http://lk.archive.ubuntu.com jaunty-updates Release                        
Hit http://security.ubuntu.com jaunty-security/restricted Sources              
Ign http://www.remastersys.klikit-linux.com remastersys/ Release.gpg           
Hit http://lk.archive.ubuntu.com jaunty/main Packages                          
Ign http://www.remastersys.klikit-linux.com remastersys/ Translation-en_US     
Hit http://security.ubuntu.com jaunty-security/universe Packages               
Hit http://lk.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://security.ubuntu.com jaunty-security/universe Sources                
Ign http://www.remastersys.klikit-linux.com remastersys/ Release               
Hit http://lk.archive.ubuntu.com jaunty/main Sources                           
Hit http://security.ubuntu.com jaunty-security/multiverse Packages             
Ign http://www.remastersys.klikit-linux.com remastersys/ Packages              
Hit http://lk.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://security.ubuntu.com jaunty-security/multiverse Sources              
Ign http://www.remastersys.klikit-linux.com remastersys/ Packages              
Hit http://lk.archive.ubuntu.com jaunty/universe Packages
[COLOR=Red]Err http://www.remastersys.klikit-linux.com remastersys/ Packages             
  404 Not Found[/COLOR]
Hit http://lk.archive.ubuntu.com jaunty/universe Sources
Hit http://lk.archive.ubuntu.com jaunty/multiverse Packages
Hit http://lk.archive.ubuntu.com jaunty/multiverse Sources
Hit http://lk.archive.ubuntu.com jaunty-updates/main Packages
Hit http://lk.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://lk.archive.ubuntu.com jaunty-updates/main Sources
Hit http://lk.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://lk.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://lk.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://lk.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://lk.archive.ubuntu.com jaunty-updates/multiverse Sources
[COLOR=Red]W: Failed to fetch http://www.remastersys.klikit-linux.com/repository/remastersys/Packages  404 Not Found[/COLOR]

```

---

### Post by earthpigg on 2009-12-09
hi,

i think you are reading some obsolete directions :D

here are up to date ones:

[http://geekconnection.org/remastersys/ubuntu.html](http://geekconnection.org/remastersys/ubuntu.html)

> Where can I get remastersys?

The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:

For Gutsy and Earlier - up to version 2.0.11-1
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) remastersys/


For Hardy and Newer with original grub - version 2.0.12-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) ubuntu/

For Karmic and Newer with grub2 - version 2.0.13-1 and up
# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/


Then simply either reload in Synaptic or you can "sudo apt-get update" and install remastersys.


---

### Post by emigrant on 2009-12-09
thanks earthpiggg it worked :)

---

### Post by emigrant on 2009-12-09
hi all,
i get the following files:
which one to be written on dvd? only the .iso is enough?
```

/home/remastersys/remastersys$ ls
cleantmpusers   customdist.iso.md5  ISOTMP           tmpusers   tmpusers2
customdist.iso  dummysys            remastersys.log  tmpusers1  tmpusers3
```

---

### Post by earthpigg on 2009-12-09
correct, the .iso.

---

### Post by emigrant on 2009-12-09
thanks man :)

---

