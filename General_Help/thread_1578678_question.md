---
title: "question"
date: 2010-09-20
forum: General Help
---

### Post by xdweaver on 2010-09-20
I did a sudo apt-get update and got this:

wendy@ubuntu:~$  sudo add-apt-repository ppa:racb/extra 
[sudo] password for wendy: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 51872791937F07146F995B72A038EB51A7F7F9D4
gpg: requesting key A7F7F9D4 from hkp server keyserver.ubuntu.com
gpg: key A7F7F9D4: "Launchpad PPA for Robie Basak" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
wendy@ubuntu:~$ sudo apt-get update 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/main Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/deb-src Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/jaunty Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/racb/extra/ubuntu/](http://ppa.launchpad.net/racb/extra/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [77.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [299kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [38.0kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,998B]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,252B] 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [118kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [3,771B]
Fetched 625kB in 3s (202kB/s)                        
W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
wendy@ubuntu:~$ sudo apt-get install pianobooster 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pianobooster is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
W: Duplicate sources.list entry [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_gwibber-daily_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
wendy@ubuntu:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                      
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/main Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/deb-src Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu Translation-en_US
Ign [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/) jaunty/jaunty Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://ppa.launchpad.net/racb/extra/ubuntu/](http://ppa.launchpad.net/racb/extra/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/jaunty/Release](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
wendy@ubuntu:~$

---

### Post by Bachstelze on 2010-09-20
You have a bad line in your sources.list. You should be able to spot it easily, it will be significantly longer than all the others. Comment it ot or delete it, it's for Jaunty so useless for you.

---

