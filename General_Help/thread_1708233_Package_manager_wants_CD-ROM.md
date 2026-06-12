---
title: "Package manager wants CD-ROM?"
date: 2011-03-16
forum: General Help
---

### Post by 5149.5 on 2011-03-16
My package manager now wants access to a CD when I run apt-get update and I don't even have a drive. It looks like this was caused by installing dropbox? Here is the output from apt-get update:

Ign cdrom://Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick Release.gpg
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                                                                    
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en                                                    
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_US                                                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                                                        
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                                  
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]           
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Media change: please insert the disc labeled                         
 'Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

How should I proceed? Is it safe to just remove that line from sources.list?

---

### Post by 5149.5 on 2011-03-16
I went ahead , backed up my sources file, commented out the line in the original, and ran update. Everything seems fine so far.

---

