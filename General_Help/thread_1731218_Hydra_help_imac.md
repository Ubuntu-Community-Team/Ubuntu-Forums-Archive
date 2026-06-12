---
title: "Hydra help imac"
date: 2011-04-16
forum: General Help
---

### Post by enzodad on 2011-04-16
Hey all , well i am new to linux, i do not know how to compile things....anyway i cant get Hydra-GTK to compile/install no matter what directions i follow----can someone assist me please-----a simple guide maybe---- ubuntu 10.10

---

### Post by spikoley on 2011-04-18
I found this [guide]("http://www.bec0de.com/linux.php?page=installing-hydra-and-hydragtk-from-backtrack4-packages-on-ubuntu").

---

### Post by enzodad on 2011-04-19
Does not work

---

### Post by bodhi.zazen on 2011-04-19
> **enzodad said:**
> Does not work

What have you tried and what error messages are you getting ?

---

### Post by enzodad on 2011-04-21
christopher@christopher:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,077B]                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://repo.offensive-security.com](http://repo.offensive-security.com) binary/ Release.gpg                     
  Could not connect to repo.offensive-security.com:80 (208.68.239.28), connection timed out
Err [http://repo.offensive-security.com/dist/bt4/](http://repo.offensive-security.com/dist/bt4/) binary/ Translation-en
  Unable to connect to repo.offensive-security.com:http:
Err [http://repo.offensive-security.com/dist/bt4/](http://repo.offensive-security.com/dist/bt4/) binary/ Translation-en_US
  Unable to connect to repo.offensive-security.com:http:
Fetched 2,621B in 2min 0s (22B/s)
Reading package lists... Done
W: Failed to fetch [http://repo.offensive-security.com/dist/bt4/binary/Release.gpg](http://repo.offensive-security.com/dist/bt4/binary/Release.gpg)  Could not connect to repo.offensive-security.com:80 (208.68.239.28), connection timed out

W: Failed to fetch [http://repo.offensive-security.com/dist/bt4/binary/en.bz2](http://repo.offensive-security.com/dist/bt4/binary/en.bz2)  Unable to connect to repo.offensive-security.com:http:

W: Failed to fetch [http://repo.offensive-security.com/dist/bt4/binary/en_US.bz2](http://repo.offensive-security.com/dist/bt4/binary/en_US.bz2)  Unable to connect to repo.offensive-security.com:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
christopher@christopher:~$

---

### Post by enzodad on 2011-04-21
christopher@christopher:~$ sudo apt-get install hydra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hydra
christopher@christopher:~$

---

### Post by bodhi.zazen on 2011-04-21
Looks like the offensive security repo is off line.

You will need to either compile it yourself, download a deb, or contact offensive security . com

---

### Post by enzodad on 2011-04-21
Ok i dont know how to complie or anything lol newbie here-----

---

### Post by enzodad on 2011-04-21
Download a deb? and i do not know how to compile  ---

---

### Post by bodhi.zazen on 2011-04-21
Ok =)

Using this blog as a guide:

[http://edwincastillo.com/archives/242](http://edwincastillo.com/archives/242)

Use this code:

```
sudo apt-get update

sudo apt-get install build-essential linux-headers-$(uname -r) libgtk2.0-dev libssl-dev cmake

# Download and install Hydra
cd ~/Downloads
wget http://freeworld.thc.org/releases/hydra-5.9.1-src.tar.gz
tar -xvzf hydra-5.9-src.tar.gz
cd hydra-5.9-src

./configure
make
sudo make install
```

Post any error messages you may get.

One last piece of advice, with penetration testing you are going to need to learn to do some reading ;)

---

### Post by enzodad on 2011-04-26
Okay ill give it a try--ill post results

---

### Post by enzodad on 2011-04-26
do i copy and paste entire code or each line by its self

---

### Post by bodhi.zazen on 2011-04-26
> **enzodad said:**
> do i copy and paste entire code or each line by its self

Just the error message, if any, which is at the very end. Perhaps one or two lines above so we can see what it was doing at the time it failed.

---

