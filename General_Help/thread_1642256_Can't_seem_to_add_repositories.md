---
title: "Can't seem to add repositories"
date: 2010-12-10
forum: General Help
---

### Post by Belgatom on 2010-12-10
Whenever I want to install something that's not in synaptic and I try to add repositories via commandline, it fails. Does this work through a certain port? I am currently working at work and behind proxy and firewall of the server. I may not have access to certain ports. 

Example: Trying to add this repository
```
sudo add-apt-repository ppa:synapse-core/ppa
```

Gets me the following:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 3DD99294193A09EF9270EEAFE4010F076C2225A4
gpg: requesting key 6C2225A4 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

---

### Post by sikander3786 on 2010-12-10
Are you able to update successfully?

```
sudo apt-get update
```

---

### Post by karthick87 on 2010-12-10
What version of ubuntu you are using?

---

### Post by Belgatom on 2010-12-10
Sorry, using 10.10

And yes, I can update although there are some problems here and there, not so sure, I'm no power user yet. 

```
Hit http://extras.ubuntu.com maverick Release.gpg
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://archive.ubuntu.com maverick Release.gpg                             
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Get:3 http://ppa.launchpad.net maverick Release [9,750B]                       
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Get:4 http://ppa.launchpad.net maverick/main Sources [1,164B]                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Get:5 http://ppa.launchpad.net maverick/main i386 Packages [1,779B]            
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US  
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://linux.dropbox.com maverick Release.gpg                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg          
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release 
Hit http://archive.ubuntu.com maverick-updates Release                         
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://archive.ubuntu.com maverick-security Release              
Hit http://archive.ubuntu.com maverick/main Sources                            
Hit http://archive.ubuntu.com maverick/restricted Sources            
Hit http://archive.ubuntu.com maverick/universe Sources              
Hit http://archive.ubuntu.com maverick/multiverse Sources            
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://linux.dropbox.com maverick Release  
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages      
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources    
Hit http://archive.ubuntu.com maverick-updates/universe Sources      
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources    
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages    
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://linux.dropbox.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Get:6 http://dl.google.com stable Release [1,347B]
Get:7 http://dl.google.com stable/main i386 Packages [1,066B]                  
Fetched 15.6kB in 10s (1,530B/s)                                               
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E4010F076C2225A4

```

---

### Post by sikander3786 on 2010-12-10
A GPG key error.

First try this and paste the output,

```
 sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4010F076C2225A4
```

---

### Post by Belgatom on 2010-12-10
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys E4010F076C2225A4
gpg: requesting key 6C2225A4 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Connection timed out
gpgkeys: HTTP fetch error 7: couldn't connect: Connection timed out
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

---

### Post by sikander3786 on 2010-12-10
Were you previously able to connect to Ubuntu keyserver?

Some ISPs tend to block connections to Ubuntu keyserver. Why? I don't know.

See a bug here.

[https://bugs.launchpad.net/ubuntu-website/+bug/435193](https://bugs.launchpad.net/ubuntu-website/+bug/435193)

Or this thread.

[http://ubuntuforums.org/showthread.php?t=1154111](http://ubuntuforums.org/showthread.php?t=1154111)

---

### Post by Belgatom on 2010-12-10
Just took the pc home with me. I tried at work (behind firewall and proxy) to access [http://keyserver.ubuntu.com:11371/](http://keyserver.ubuntu.com:11371/) with no succes. 

Just installed at home and tried it again, with succes. Clearly port 11371 needs to be forwarded. 

(So how do I set this to Solved)

---

### Post by sikander3786 on 2010-12-11
Yes that seems to be a firewall/proxy issue ;-)

Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

