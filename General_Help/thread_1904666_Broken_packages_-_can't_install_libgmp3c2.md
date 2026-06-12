---
title: "Broken packages - can't install libgmp3c2"
date: 2012-01-05
forum: General Help
---

### Post by rikmik on 2012-01-05
For the first time in several years Ubuntu use I have a problem with package system update: "Sub-process /usr/bin/dpkg returned an error code (2)". Won't install libgmp3c2 or fix broken packages. Would appreciate some help. 

See following output from Terminal:


richard@main-pc:~/Desktop$ sudo apt-get update
[sudo] password for richard: 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                               
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                                        
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                      
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB   
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_GB 
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Get: 3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                               
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_GB                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Get: 5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,185B]
Get: 6 [http://dl.google.com](http://dl.google.com) stable/main Packages [765B]
Fetched 5,040B in 2s (2,327B/s)
Reading package lists... Done
richard@main-pc:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  cpp-4.4: Depends: libgmp3c2 but it is not installed
  g++-4.4: Depends: libgmp3c2 but it is not installed
  guile-1.8-libs: Depends: libgmp3c2 but it is not installed
  libmpfr1ldbl: Depends: libgmp3c2 (>= 4.2.dfsg-1) but it is not installed
  librasqal2: Depends: libgmp3c2 but it is not installed
  python-crypto: Depends: libgmp3c2 but it is not installed
E: Unmet dependencies. Try using -f.
richard@main-pc:~/Desktop$ sudo apt-get -f install libgmp3c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libgmp3c2
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/331kB of archives.
After this operation, 709kB of additional disk space will be used.
dpkg: parse error, in file '/var/lib/dpkg/available' near line 1303:
 invalid package name (may not be empty string)
E: Sub-process /usr/bin/dpkg returned an error code (2)
richard@main-pc:~/Desktop$ uname -q
uname: invalid option -- 'q'
Try `uname --help' for more information.
richard@main-pc:~/Desktop$ uname -a
Linux main-pc 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
richard@main-pc:~/Desktop$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB  
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB                   
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB                     
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                       
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_GB    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_GB 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release     
Get: 3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                                         
Get: 5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,185B]            
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Get: 6 [http://dl.google.com](http://dl.google.com) stable/main Packages [765B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Fetched 5,040B in 1s (3,493B/s)
Reading package lists... Done
richard@main-pc:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  cpp-4.4: Depends: libgmp3c2 but it is not installed
  g++-4.4: Depends: libgmp3c2 but it is not installed
  guile-1.8-libs: Depends: libgmp3c2 but it is not installed
  libmpfr1ldbl: Depends: libgmp3c2 (>= 4.2.dfsg-1) but it is not installed
  librasqal2: Depends: libgmp3c2 but it is not installed
  python-crypto: Depends: libgmp3c2 but it is not installed
E: Unmet dependencies. Try using -f.
richard@main-pc:~/Desktop$ sudo apt-get -f install libgmp3c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libgmp3c2
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/331kB of archives.
After this operation, 709kB of additional disk space will be used.
dpkg: parse error, in file '/var/lib/dpkg/available' near line 1303:
 invalid package name (may not be empty string)
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by lechien73 on 2012-01-05
Hi & welcome to the forums,

Could you try running:

```
sudo dpkg --clear-avail
```

and then try the apt-get commands again? As the man page says, this will "Erase the existing information about what packages are available", which seems to be causing the problem.

As a note for the future, if you're posting long output like above, then please could you surround it with CODE tags? You can do this by selecting your text, and then clicking the **#** button on the post toolbar. Thanks.

---

### Post by rikmik on 2012-01-05
Hi Matt, thanks for the quick reply.

I tried your suggestion but still no joy. See code below: 


```
richard@main-pc:~/Desktop$ sudo dpkg --clear-avail
[sudo] password for richard: 
richard@main-pc:~/Desktop$ sudo apt-get update
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                              
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB                           
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_GB 
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB                   
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                                      
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB                       
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                             
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_GB                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_GB
Get: 3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get: 5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,185B]                                    
Get: 6 [http://dl.google.com](http://dl.google.com) stable/main Packages [765B]                                      
Fetched 5,040B in 17s (296B/s)
Reading package lists... Done
richard@main-pc:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ghostscript ghostscript-cups ghostscript-x libgs8
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/3,303kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/status' near line 36174 package 'lidgmp3c2':
 invalid package name (character ` ' not allowed (only letters, digits and characters `-+._'))
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by crazy bird on 2012-01-05
Try this:
[http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/](http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/)
Or this:
[http://georgeblog.nyarangi.com/2010/02/fixing-broken-packages-in-ubuntu.html](http://georgeblog.nyarangi.com/2010/02/fixing-broken-packages-in-ubuntu.html)

---

### Post by rikmik on 2012-01-05
No luck. I have followed all the suggestions in these links and sub links to no avail. I still get the following so I think there is something wrong with libgmp3c2 itself. I notice the program is called li**d**gmp3c2 in the error text.

```
richard@main-pc:~/Desktop$ sudo apt-get install libgmp3c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libgmp3c2
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/331kB of archives.
After this operation, 709kB of additional disk space will be used.
dpkg: parse error, in file '/var/lib/dpkg/status' near line 36152 package 'lidgmp3c2':
 invalid package name (character ` ' not allowed (only letters, digits and characters `-+._'))
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by topsites on 2012-01-05
I just had a similar problem with a different set of packages, attempting to remove the old (corrupt) one went without love, it broke several parts of my OS (such as flash, firefox would only open to half window OR full screen) and after more pain than I could tolerate I re-installed Ubuntu fresh which fixed the problems but I am currently downloading a Debian ISO.

---

### Post by sdowney717 on 2012-01-05
looks like the file '/var/lib/dpkg/status' has an error

Why not rename that file to keep it for backup.
then delete it and try again.

maybe you could just delete that one bad line
And read up on the file and how modifying it might change things, it keeps track of the installed packages.

[http://askubuntu.com/questions/48303/how-can-i-clean-up-var-lib-dpkg-status](http://askubuntu.com/questions/48303/how-can-i-clean-up-var-lib-dpkg-status)

looks like you can purge this particular item
follow the text

> 
Try a "dpkg -P " for the offending package. That will purge it from the local repository, removing all traces. On my system, that was the fix for removed (but not yet purged) packages that produced that error.

---

### Post by rikmik on 2012-01-06
Thank you so much sdowney717 for pointing me to the basics and to following the error text. 

I backed up the status file, removed the offending package section, replaced the file in /var/lib/dpkg, used the dpkg -P option and then apt-get update/upgrade. All is now well :D 

Thanks everyone for all the help.

---

