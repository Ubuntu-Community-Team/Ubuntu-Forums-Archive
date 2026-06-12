---
title: "Update Issue - Firefox problem"
date: 2011-09-10
forum: General Help
---

### Post by SecretEaDad on 2011-09-10
Hi I am stuck in a loop..
Trying to update software I get
Items cannot be installed or removed until the package catalogue is repaired. Do you want to repair it now?
So I click repair
An unhandled error occured

Details:
last line is KeyError: 'at-spi2-bore'

If i I use sudo commands in terminal it appears to be a firefox issue, I have tried sudo update, sudo clean etc. cannot uninstal firefox and can't update it.

Also chromium now won't launch and firefox crashes all the time.

Help please

---

### Post by TeoBigusGeekus on 2011-09-10
Try this
```
sudo dpkg-reconfigure firefox
```

---

### Post by SecretEaDad on 2011-09-10
hi tried that 
dpkg-query: error: parsing file '/var/lib/dpkg/status' near line 27833 package 'gnome-system-tools':
'Depends' field, refernece to 'libfontconfig1': invalid archetecture name 'i386': a value different from 'any' is currently not allowed
/usr/sbin/dpkg-reconfigure firefox is not installed.

which it is, hardwork typing out longhand

---

### Post by SecretEaDad on 2011-09-10
the other error I get is
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies.
firefox-globalmenu : Depends: firefox (=6.0.2+build2+nobinonly-0ubuntu0.11.04.1) but 6.0.1+build1+nobinonly-0ubuntu0.11.04.1 is installed
E: Unmet dependencies. Try using -f.

so try apt-get -f instal
E: Invalid operation instal

head ache
 thanks

---

### Post by TeoBigusGeekus on 2011-09-10
You've misspelled install.
Try again with
```
sudo apt-get -f install
```

---

### Post by Pariah819 on 2011-09-10
Here is a thread that solved a broken package catalog, perhaps it will help...

The last code section is what would apply to you.

[http://ubuntuforums.org/showpost.php?p=10546597&postcount=2](http://ubuntuforums.org/showpost.php?p=10546597&postcount=2)

---

### Post by SecretEaDad on 2011-09-11
I am such a klutz, well spotted and thank you, however, still get 

'Depends' field, refernece to 'libfontconfig1': invalid archetecture name 'i386': a value different from 'any' is currently not allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)

Still no further forward

Full terminal
```

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease             
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty
Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main
Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386
Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main
TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main
Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main
TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted
Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386
Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386
Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main
TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse
TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted
TranslationIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386
Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386
Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse
TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted
TranslationIndex     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe
TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse
Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted
Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse
Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted
Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe
Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 72 B in 1s (41 B/s)
Reading package lists... Done
mark@mark-NoteBook:~$ sudo apt-get install aptitude
--no-install-recommends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 aptitude : Depends: libboost-iostreams1.42.0 (>= 1.42.0-1) but it is
not going to be installed
            Depends: libcwidget3 but it is not going to be installed
 firefox-globalmenu : Depends: firefox (= 6.0.2+build2
+nobinonly-0ubuntu0.11.04.1) but 6.0.1+build1+nobinonly-0ubuntu0.11.04.1
is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or
specify a solution).
mark@mark-NoteBook:~$ sudo aptitude install -f
sudo: aptitude: command not found
mark@mark-NoteBook:~$ sudo aptitude full-upgrade
sudo: aptitude: command not found
mark@mark-NoteBook:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer
required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox firefox-globalmenu
Suggested packages:
  latex-xft-fonts
The following packages will be upgraded:
  firefox firefox-globalmenu
2 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 15.8 MB of archives.
After this operation, 69.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/)
natty/main firefox-globalmenu i386 7.0~b5+build1
+nobinonly-0ubuntu0.11.04.1~mfn1 [41.1 kB]
Get:2 [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/)
natty/main firefox i386 7.0~b5+build1+nobinonly-0ubuntu0.11.04.1~mfn1
[15.7 MB]
Fetched 15.8 MB in 1min 8s (231
kB/s)                                          
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27833 package
'gnome-system-tools':
 'Depends' field, reference to 'libfontconfig1': invalid architecture
name 'i386': a value different from 'any' is currently not allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by SecretEaDad on 2011-09-13
I have an issue with what appears to be a firefox update and a discrepancy between i386 and any? please see below...any help greatly received!

```

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty
Release.gpg 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main
Sources 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386
Packages 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main
TranslationIndex 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main
Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main
TranslationIndex 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted
Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386
Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386
Packages 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main
TranslationIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse
TranslationIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted
TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386
Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386
Packages 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse
TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted
TranslationIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe
TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse
Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted
Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse
Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted
Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe
Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 72 B in 1s (41 B/s)
Reading package lists... Done
mark@mark-NoteBook:~$ sudo apt-get install aptitude
--no-install-recommends
Reading package lists... Done
Building dependency tree 
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
aptitude : Depends: libboost-iostreams1.42.0 (>= 1.42.0-1) but it is
not going to be installed
Depends: libcwidget3 but it is not going to be installed
firefox-globalmenu : Depends: firefox (= 6.0.2+build2
+nobinonly-0ubuntu0.11.04.1) but 6.0.1+build1+nobinonly-0ubuntu0.11.04.1
is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or
specify a solution).
mark@mark-NoteBook:~$ sudo aptitude install -f
sudo: aptitude: command not found
mark@mark-NoteBook:~$ sudo aptitude full-upgrade
sudo: aptitude: command not found
mark@mark-NoteBook:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer
required:
linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
firefox firefox-globalmenu
Suggested packages:
latex-xft-fonts
The following packages will be upgraded:
firefox firefox-globalmenu
2 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 15.8 MB of archives.
After this operation, 69.6 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/mozillateam...x-next/ubuntu/](http://ppa.launchpad.net/mozillateam...x-next/ubuntu/)
natty/main firefox-globalmenu i386 7.0~b5+build1
+nobinonly-0ubuntu0.11.04.1~mfn1 [41.1 kB]
Get:2 [http://ppa.launchpad.net/mozillateam...x-next/ubuntu/](http://ppa.launchpad.net/mozillateam...x-next/ubuntu/)
natty/main firefox i386 7.0~b5+build1+nobinonly-0ubuntu0.11.04.1~mfn1
[15.7 MB]
Fetched 15.8 MB in 1min 8s (231
kB/s) 
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27833 package
'gnome-system-tools':
'Depends' field, reference to 'libfontconfig1': invalid architecture
name 'i386': a value different from 'any' is currently not allowed
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

What am I doing wrong?

---

### Post by coffeecat on 2011-09-13
@SecretEaDad, I've moved your latest post into your original thread because the output appears to be identical with what you posted two days ago.

Please do not create multiple threads on the same issue. It is quite OK to bump a thread after 24 hours if you receive no further replies.

---

### Post by SecretEaDad on 2011-09-13
> **coffeecat said:**
> @SecretEaDad, I've moved your latest post into your original thread because the output appears to be identical with what you posted two days ago.

Please do not create multiple threads on the same issue. It is quite OK to bump a thread after 24 hours if you receive no further replies.

ok, thanks....what is bump? As this error has affected me for several days I was starting to get desperate, to the point of checking out how much win7 will cost me to buy, just to have a safe working operating system.

---

### Post by coffeecat on 2011-09-13
No problem. Sorry I didn't explain.

If you want to bring your thread up to the top again so that it gets noticed, simply post with the word "bump". It's an acronym for "bring up my post". General rule of thumb: don't bump more often than 24 hours. Anything less is frowned on.

But good luck! :)

---

### Post by TeoBigusGeekus on 2011-09-13
Try this:
```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_old
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by SecretEaDad on 2011-09-14
Thanks apparently there is no such directory....

mark@mark-NoteBook:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_old
[sudo] password for mark: 
mark@mark-NoteBook:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease             
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]  
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release                                 
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [67.5 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex     
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources [105 kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [10.6 kB]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [650 B]    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [179 kB]   
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources [25.2 kB]   
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources [1,890 B] 
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages [318 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [37.5 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,071 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages [92.2 kB]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,258 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 907 kB in 5s (175 kB/s)
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
mark@mark-NoteBook:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
mark@mark-NoteBook:~$

---

### Post by SecretEaDad on 2011-09-15
still stuck...nothing has worked so far, please help

---

### Post by SecretEaDad on 2011-09-18
anyone - ??

---

### Post by Krytarik on 2011-09-18
First, undo the previously done renaming of the "status" file:
```
sudo mv /var/lib/dpkg/status_old /var/lib/dpkg/status
```Then try following the steps in this guide (currently unavailable):

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

Btw., please try using code boxes for terminal outputs and commands. Therefore, just highlight the concerned text, then click on the #-button in the editor.

---

### Post by SecretEaDad on 2011-09-27
Thank you, I have tried and done that, looks like it may have worked

---

### Post by SecretEaDad on 2011-10-03
firefox problem is back again - driving me nuts

---

