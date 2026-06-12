---
title: "Can't fix broken packages"
date: 2011-09-11
forum: General Help
---

### Post by clongstaff on 2011-09-11
I have been trying to fix some broken packages but without success.  I have a warning sign in the top panel and I tried to run Synaptic Package Manager and delete the broken packages.  This failed to fix the problem.  A warning message appeared saying "Not all changes and updates succeeded".  In the details panel it said "dpkg: parse error in file '/var/lib/dpkg/status' near line 14258 invalid package name (must start with alphanumeric)".  Following a bit of reading around I tried sudo apt-get -f install.  This says it will install libgdu0, but then this fails too and the same error appears as above "dpkg parse error.....".  I am very new to all this so sorry if I've missed something vital.

---

### Post by raja.genupula on 2011-09-11
please post exactly what you got from this 

```
sudo apt-get update
```

---

### Post by bodhi.zazen on 2011-09-11
Follow the procedure on this blog, from top to bottom:

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by clongstaff on 2011-09-12
p { margin-bottom: 0.08in; }  I tried the command you suggested and here is the response.  (will try the blog too)



colin@ubuntu:~$ sudo apt-get update 
 [sudo] password for colin:  
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg 
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US 
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                    
 Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                    
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US 
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US 
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources            
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages       
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages               
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources 
 Reading package lists... Done

---

### Post by clongstaff on 2011-09-14
OK I think I see the method in the blog where I should go in and remove the offending package.  I'm a bit nervous in case something dramatic happens so I wanted to check if possible.

When I do sudo apg-get install -f I get the response below.  Should I go to the '/var/lib/dpkg' and remove 'status'.  Is this correct  and would this be OK? And do I then use the reinstreq lines?

Advice gratefully received.


[Output]
colin@ubuntu:~$ sudo apt-get install -f
[sudo] password for colin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgdu0
The following NEW packages will be installed:
  libgdu0
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
5 not fully installed or removed.
Need to get 0B/92.4kB of archives.
After this operation, 299kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 14258:
 invalid package name (must start with an alphanumeric)
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by clongstaff on 2011-09-25
OK, I think I have it sorted now.

I looked in the "status" file at line 14258 and found "Package: "libgdu0 ".
I looked in the file "status-old" and found an equivalent line "Package: libgdu0 "
So it looked like there was a stray " in the "status" file at line 14258.  Cleverly I thought I could just edit it out, but this was pretty disastrous and multiple things went wrong. I was considering a reinstall but what seems to have worked was to rename (using sudo mv) "status" to "status-broke" and "status-old" to "status".  Then I did an update and everything seems OK-for now!

---

