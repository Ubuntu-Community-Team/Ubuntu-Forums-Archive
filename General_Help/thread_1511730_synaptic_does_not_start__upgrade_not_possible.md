---
title: "synaptic does not start / upgrade not possible"
date: 2010-06-17
forum: General Help
---

### Post by nkbatsi on 2010-06-17
my synaptic will not start. I get this  message when i start synaptic and then synaptic shuts down: 

[B]The package libi2c-dev is not ok and I don't know how to fix it!

[/B]So i try from the terminal:
 ```

$ **sudo apt-get clean**
$ **sudo apt-get update**
Ign file: apt-build Release.gpg
Ign file: apt-build/main Translation-en_US                                     
Get:1 file: apt-build Release [89B]                                            
Ign file: apt-build/main Packages                                              
Ign file: apt-build/main Packages                                              
Hit http://ftp.ntua.gr karmic-updates Release.gpg                              
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net karmic/main Translation-en_US                     
Hit http://archive.ubuntu.com karmic Release.gpg                               
Ign http://archive.ubuntu.com karmic/main Translation-en_US                    
Hit http://archive.canonical.com karmic Release.gpg                            
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://ftp.ntua.gr karmic-updates/main Translation-en_US                   
Get:2 http://packages.medibuntu.org karmic Release.gpg [197B]                  
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://archive.canonical.com karmic Release                                
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://ftp.ntua.gr karmic-updates/multiverse Translation-en_US             
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US              
Ign http://archive.ubuntu.com karmic/universe Translation-en_US                
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US              
Hit http://archive.ubuntu.com karmic Release                                   
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Get:3 http://packages.medibuntu.org karmic Release [9,237B]                    
Ign http://ftp.ntua.gr karmic-updates/restricted Translation-en_US             
Hit http://deb.opera.com stable Release                                        
Ign http://ftp.ntua.gr karmic-updates/universe Translation-en_US               
Hit http://ftp.ntua.gr karmic-updates Release                                  
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://apt.wicd.net jaunty Release.gpg                          
Ign http://apt.wicd.net jaunty/extras Translation-en_US             
Hit http://archive.canonical.com karmic/partner Sources             
Hit http://security.ubuntu.com karmic-security/main Packages        
Hit http://archive.ubuntu.com karmic/main Packages                             
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://apt.wicd.net jaunty Release                                         
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://archive.ubuntu.com karmic/restricted Packages                       
Hit http://archive.ubuntu.com karmic/universe Packages              
Hit http://archive.ubuntu.com karmic/multiverse Packages            
Hit http://packages.medibuntu.org karmic/free Packages              
Hit http://ftp.ntua.gr karmic-updates/main Packages                            
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://ftp.ntua.gr karmic-updates/multiverse Packages                      
Hit http://packages.medibuntu.org karmic/non-free Packages                     
Hit http://deb.opera.com stable/non-free Packages                              
Hit http://ftp.ntua.gr karmic-updates/restricted Packages                      
Hit http://ftp.ntua.gr karmic-updates/universe Packages                
Ign http://apt.wicd.net jaunty/extras Packages                         
Ign http://apt.wicd.net jaunty/extras Packages
Hit http://apt.wicd.net jaunty/extras Packages
Fetched 9,434B in 1s (6,075B/s)
Reading package lists... Done

$** sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: [B]The package libi2c-dev is not ok and I don't know how to fix it!
[/B]$

```

I am quite new in ubuntu so i cannot sort out mistakes. I guess I might have some double inputs in my repositories still i don't really know how i 've done this and how to clean them up!
Can anybody please help?

---

### Post by Chesamo on 2010-06-17
Try ```
sudo dpkg-configure -a
```

---

### Post by nkbatsi on 2010-06-17
I did and this is what came out:

```
$ sudo dpkg-configure -a
sudo: dpkg-configure: command not found
$ 

```

---

### Post by philinux on 2010-06-17
> **Chesamo said:**
> Try ```
sudo dpkg-configure -a
```

That should be

```
sudo dpkg --configure -a
```

---

### Post by Chesamo on 2010-06-17
> **philinux said:**
> That should be

```
sudo dpkg --configure -a
```
That's the one! Sorry, just woke up and haven't eaten breakfast yet ^.^;

---

### Post by nkbatsi on 2010-06-17
Ok, thanks to both of you.

now that's the output :
```
$ sudo dpkg --configure -a
Setting up xulrunner-1.9.1 (1.9.1.11~hg20100616r26954+nobinonly-0ubuntu1~umd1~karmic) ...
/var/lib/dpkg/info/xulrunner-1.9.1.postinst: 5: /usr/bin/xulrunner-1.9.1: not found
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up xulrunner-1.9.3 (1.9.3~a6~hg20100617r43709+nobinonly-0ubuntu1~umd1~karmic) ...
/var/lib/dpkg/info/xulrunner-1.9.3.postinst: 5: /usr/bin/xulrunner-1.9.3: not found
dpkg: error processing xulrunner-1.9.3 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.7:
 firefox-3.7 depends on xulrunner-1.9.3; however:
  Package xulrunner-1.9.3 is not configured yet.
dpkg: error processing firefox-3.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9.1-gnome-support:
 xulrunner-1.9.1-gnome-support depends on xulrunner-1.9.1 (= 1.9.1.11~hg20100616r26954+nobinonly-0ubuntu1~umd1~karmic); however:
  Package xulrunner-1.9.1 is not configured yet.
dpkg: error processing xulrunner-1.9.1-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.7-branding:
 firefox-3.7-branding depends on firefox-3.7 (= 3.7~a6~hg20100615r43622+nobinonly-0ubuntu1~umd1~karmic); however:
  Package firefox-3.7 is not configured yet.
dpkg: error processing firefox-3.7-branding (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9.1
 xulrunner-1.9.3
 firefox-3.7
 xulrunner-1.9.1-gnome-support
 firefox-3.7-branding
$ 

```

any suggestion?

---

### Post by philinux on 2010-06-17
Err. 

Firefox 3.7, you must have a ppa or other active.

---

### Post by nkbatsi on 2010-06-17
that's true: i 've uploaded a screenshot of my repositories, I've just unclicked the ppa.

What now?

---

### Post by nkbatsi on 2010-06-17
I've tried to update and my computer stalled so i had to press the reset button. this is what i get now: 
```
$ sudo apt-get upgrade
Reading package lists... Done
Segmentation faulty tree... 0%
$

```

Does anyone have any ideas, please...

---

### Post by philinux on 2010-06-17
I would untick the non standard ones, one by one and see which if any is the cause.

---

### Post by nkbatsi on 2010-06-17
thanks for that, i 'll try it and get back.

---

### Post by joko_e42 on 2011-02-16
Hello, :), good evening,
  thanks Everybody, especially for philinux. I had same issue with my Ubuntu 10.10. This problem raised after I reboot my Ubuntu whereas the Update Manager program was still running. After that restart, I installed several packages, than the message raised :
   "Reading package lists... Done
   Segmentation faulty tree... 0%"
after the message shown, I could not install any packages, than I searched in google, ..finally I found this topic, so I used some solution described above. I used :
  sudo dpkg --configure -a than
  sudo apt-get update
the two commands above fixed the problem. :)

---

