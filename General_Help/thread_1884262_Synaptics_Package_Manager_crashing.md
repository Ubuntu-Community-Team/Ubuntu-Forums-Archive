---
title: "Synaptics Package Manager crashing"
date: 2011-11-20
forum: General Help
---

### Post by honeybadger20 on 2011-11-20
I was forced to reformat my hard-drive after a most unfortunate incident with my copy of Windows XP dying, forcing me to install Ubuntu. I had a copy of 10.10, so I installed that and upgraded to 11.04. While it was updating, it was giving me numerous errors while installing packages. When I rebooted, I found that I had to repair the packages. I tried through both Ubuntu Software Centre, and Synaptics Package Manager, both to no avail.
I tried once more with Synaptics, but this time it stopped responding, and crashed. Now when I try to launch it, it asks for my password, loads, but stays at an unresponsive, greyed-out window. I tried launching it with gksudo -d, and that lead to this:
```

buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
buffer: --
brute force GNOME_SUDO_PASS ended...
No password prompt found; we'll assume we don't need a password.
xauth: /tmp/libgksu-EvKhk2/.Xauthority
xauth_env: /var/run/gdm/auth-for-zain-m2DTM1/database
dir: /tmp/libgksu-EvKhk2

```

The buffer: -- took up more lines than sudo could recall, so lines were omitted to save space.

---

### Post by raja.genupula on 2011-11-21
```
sudo apt-get update
``` 
give me output of that command . 
and do this also 
```
 
sudo apt-get install --reinstall synaptic

```
 
let me know what you got.

---

### Post by honeybadger20 on 2011-11-21
```
zain@zain-1545:~$ sudo apt-get update
Ign http://security.ubuntu.com natty-security InRelease
Ign http://extras.ubuntu.com natty InRelease   
Ign http://ca.archive.ubuntu.com natty InRelease
Ign http://ca.archive.ubuntu.com natty-updates InRelease
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://extras.ubuntu.com natty Release.gpg 
Hit http://ca.archive.ubuntu.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release
Hit http://extras.ubuntu.com natty Release                            
Hit http://ca.archive.ubuntu.com natty-updates Release.gpg            
Hit http://security.ubuntu.com natty-security/main Sources
Hit http://extras.ubuntu.com natty/main Sources
Hit http://ca.archive.ubuntu.com natty Release 
Hit http://security.ubuntu.com natty-security/restricted Sources                            
Hit http://security.ubuntu.com natty-security/universe Sources       
Hit http://security.ubuntu.com natty-security/multiverse Sources     
Hit http://security.ubuntu.com natty-security/main amd64 Packages    
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages
Hit http://extras.ubuntu.com natty/main amd64 Packages               
Ign http://extras.ubuntu.com natty/main TranslationIndex             
Hit http://ca.archive.ubuntu.com natty-updates Release               
Hit http://security.ubuntu.com natty-security/universe amd64 Packages 
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com natty/main Sources                  
Hit http://ca.archive.ubuntu.com natty/restricted Sources            
Hit http://ca.archive.ubuntu.com natty/universe Sources              
Hit http://ca.archive.ubuntu.com natty/multiverse Sources            
Hit http://ca.archive.ubuntu.com natty/main amd64 Packages           
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://ca.archive.ubuntu.com natty/restricted amd64 Packages     
Hit http://ca.archive.ubuntu.com natty/universe amd64 Packages       
Hit http://ca.archive.ubuntu.com natty/multiverse amd64 Packages
Ign http://ca.archive.ubuntu.com natty/main TranslationIndex         
Ign http://ca.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://ca.archive.ubuntu.com natty/restricted TranslationIndex   
Ign http://ca.archive.ubuntu.com natty/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com natty-updates/main Sources          
Hit http://ca.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://ca.archive.ubuntu.com natty-updates/universe Sources      
Hit http://ca.archive.ubuntu.com natty-updates/multiverse Sources    
Hit http://ca.archive.ubuntu.com natty-updates/main amd64 Packages   
Hit http://ca.archive.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com natty-updates/universe amd64 Packages
Hit http://ca.archive.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://ca.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://ca.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://ca.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://ca.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://ca.archive.ubuntu.com natty/main Translation-en_CA
Hit http://ca.archive.ubuntu.com natty/restricted Translation-en_CA  
Ign http://extras.ubuntu.com natty/main Translation-en_CA            
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://security.ubuntu.com natty-security/main Translation-en_CA
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_CA
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://ca.archive.ubuntu.com natty/main Translation-en
Ign http://ca.archive.ubuntu.com natty/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/multiverse Translation-en
Ign http://ca.archive.ubuntu.com natty/restricted Translation-en
Ign http://ca.archive.ubuntu.com natty/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/universe Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/main Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en
Reading package lists... Done

```

For the second, it does something really strange.

```
zain@zain-1545:~$ sudo apt-get install --reinstall synaptic
Reading package lists... Done
Building dependency tree... 0%

```
^That appears for maybe 4-5 seconds, then this appears:
```

zain@zain-1545:~$ sudo apt-get install --reinstall synaptic
Reading package lists... Done
zain@zain-1545:~$ y tree... 0%

```

---

### Post by raja.genupula on 2011-11-21
try this man
```
 
gksu synaptic

```
 
if its not done 
 
then 
```
sudo apt-get remove --purge synaptic
```
 
& ```
sudo apt-get install synaptic
```
 
I am sure they gonna help you.

---

