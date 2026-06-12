---
title: "Can't access Ubuntu repositories et al after changing countriew"
date: 2010-07-25
forum: General Help
---

### Post by dewgong on 2010-07-25
Hi, so here's my story...i downloaded Ubuntu last year and was mightily impressed. I'm not really a techy kinda person, but ubuntu was pretty straightforward to install and set up the packages and stuff like soulseek. however since then i moved to thailand and now I live in Myanmar and Thailand...my problem is that although the internet still works, everything else like updates, Synaptic, IRC, Soulseek don't work anymore...i've lived with it for 6 months, but now it's becoming a problem because i would like to download some more software...

is there a simple solution to this or does ubuntu simply not cover these areas?

---

### Post by drs305 on 2010-07-25
Welcome to the Ubuntu forums.

Run this command from a terminal and provide us with the error messages it produces, if any:
```
sudo apt-get update
```
It should tell us if it can't find the repositories or give us a clue as to what other problems APT (the package manager) is having.

---

### Post by dewgong on 2010-07-25
it just says connecting at 0%  with the i.p address next to it...and then after failed to connect.

---

### Post by drs305 on 2010-07-25
My guess is you have a proxy problem. I know that files such as /etc/resolv.conf and /etc/apt/apt.conf or the files in /etc/apt/apt.confd sometimes need changing but unfortunately that is not my area of expertise.

It would probably help if you posted the *exact* error message (cut/paste) or searched using the exact error message. 

Another way to search would include the words "apt-get" and proxy, with something like "unable to connect". There is an address in one of your files that either must be added or removed - hopefully someone here can tell you which one or you can discover it via Google.

---

### Post by dewgong on 2010-07-26
ok thanks.. i will try that

---

### Post by dewgong on 2010-07-31
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_GB                
  Unable to connect to 10.1.0.254 8008:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_GB            
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                               
  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_GB                    
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_GB              
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_GB                
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_GB              
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg                       
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_GB            
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB      
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_GB        
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB      
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg                      
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_GB           
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_GB     
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_GB       
  Unable to connect to 10.1.0.254 8008:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_GB     
  Unable to connect to 10.1.0.254 8008:
Err [http://www.thanlwinsoft.org](http://www.thanlwinsoft.org) gutsy Release.gpg                              
  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out
Err [http://www.thanlwinsoft.org](http://www.thanlwinsoft.org) gutsy/main Translation-en_GB                   
  Unable to connect to 10.1.0.254 8008:
Err [http://ppa.lauchpad.net](http://ppa.lauchpad.net) jaunty Release.gpg                                 
  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out
Err [http://ppa.lauchpad.net](http://ppa.lauchpad.net) jaunty/main Translation-en_GB                      
  Unable to connect to 10.1.0.254 8008:
Err [http://packages.sil.org](http://packages.sil.org) gutsy Release.gpg                                  
  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out
Err [http://packages.sil.org](http://packages.sil.org) gutsy/main Translation-en_GB
  Unable to connect to 10.1.0.254 8008:
Reading package lists... Done             
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://ppa.lauchpad.net/sunab/ppa/ubuntu/dists/jaunty/Release.gpg](http://ppa.lauchpad.net/sunab/ppa/ubuntu/dists/jaunty/Release.gpg)  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out

W: Failed to fetch [http://ppa.lauchpad.net/sunab/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2](http://ppa.lauchpad.net/sunab/ppa/ubuntu/dists/jaunty/main/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://packages.sil.org/ubuntu/dists/gutsy/Release.gpg](http://packages.sil.org/ubuntu/dists/gutsy/Release.gpg)  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out

W: Failed to fetch [http://packages.sil.org/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://packages.sil.org/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://www.thanlwinsoft.org/ThanLwinSoft/Downloads/ubuntu/dists/gutsy/Release.gpg](http://www.thanlwinsoft.org/ThanLwinSoft/Downloads/ubuntu/dists/gutsy/Release.gpg)  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out

W: Failed to fetch [http://www.thanlwinsoft.org/ThanLwinSoft/Downloads/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://www.thanlwinsoft.org/ThanLwinSoft/Downloads/ubuntu/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/Release.gpg](http://packages.medibuntu.org/dists/jaunty/Release.gpg)  Could not connect to 10.1.0.254:8008 (10.1.0.254), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/jaunty/free/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-en_GB.bz2](http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to 10.1.0.254 8008:

W: Some index files failed to download, they have been ignored, or old ones used instead.



>>>here is the error message i get....
W: You may want to run apt-get update to correct these problems

---

### Post by dewgong on 2010-08-01
I also tried to locate a new server in the software sources, but the search says no suitable server was found...am i looking in the right area to fix my problem?

---

### Post by dewgong on 2010-08-01
ok, so i tried the server wizard a few more times and it seems to work (with random serves from all over the world!)

---

