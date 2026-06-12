---
title: "Trying to install Tor through Terminal"
date: 2010-11-17
forum: General Help
---

### Post by Tyler89 on 2010-11-17
Hello,

To begin, I've always been a Microsoft *****, in that my main operating system has always been Windows. I have decided that it is time to learn Linux, as I am in college working to become a network administrator, and realize that Red Hat and Ubuntu servers will probably be something I work with in the future. At any pace, being a beginner has its draw backs, namely that small mistakes are preventing me from doing things. Today, I need help finding out why I cannot install a program named Tor through Terminal. I get error messages back from Terminal saying it failed, used older files, or a mixture of both when imputing some of these commands.

I would like to state that the reason I have come to you guys first, instead of going to Tor, is that I believe this is an input problem on my part when trying to setup Tor. 


Link to site: [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) (Tried to follow instructions of option two)

Thank you for your time, as I know you're going to have to spend a minute reading the source code.

Tyler

source code:
[PHP]
jedi@Ubuntu01:~$ sudo ap-get tor-geoipdb
[sudo] password for jedi: 
sudo: ap-get: command not found
jedi@Ubuntu01:~$ sudo apt-get tor-geoipdb
E: Invalid operation tor-geoipdb
jedi@Ubuntu01:~$ sudo tor-geoipdb
sudo: tor-geoipdb: command not found
jedi@Ubuntu01:~$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: directory `/home/jedi/.gnupg' created
gpg: new configuration file `/home/jedi/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/jedi/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/jedi/.gnupg/secring.gpg' created
gpg: keyring `/home/jedi/.gnupg/pubring.gpg' created
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: /home/jedi/.gnupg/trustdb.gpg: trustdb created
gpg: key 886DDD89: public key "deb.torproject.org archive signing key" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
jedi@Ubuntu01:~$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
OK
jedi@Ubuntu01:~$ apg-get update
No command 'apg-get' found, did you mean:
 Command 'apt-get' from package 'apt' (main)
apg-get: command not found
jedi@Ubuntu01:~$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jedi@Ubuntu01:~$ gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
gpg: failed to create temporary file `/home/jedi/.gnupg/.#lk0x8c938d0.Ubuntu01.1817': Permission denied
gpg: keyblock resource `/home/jedi/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/jedi/.gnupg/.#lk0x8c95118.Ubuntu01.1817': Permission denied
gpg: keyblock resource `/home/jedi/.gnupg/pubring.gpg': general error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
jedi@Ubuntu01:~$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add-
Usage: apt-key [--keyring file] [command] [arguments]

Manage apt's list of trusted keys

  apt-key add <file>          - add the key contained in <file> ('-' for stdin)
  apt-key del <keyid>         - remove the key <keyid>
  apt-key export <keyid>      - output the key <keyid>
  apt-key exportall           - output all trusted keys
  apt-key update              - update keys using the keyring package
  apt-key net-update          - update keys using the network
  apt-key list                - list keys
  apt-key finger              - list fingerprints
  apt-key adv                 - pass advanced options to gpg (download key)

If no specific keyring file is given the command applies to all keyring files.
jedi@Ubuntu01:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Get:2 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en           
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://deb.torproject.org <lucid> Release.gpg
Ign http://deb.torproject.org/torproject.org/ <lucid>/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:3 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://deb.torproject.org/torproject.org/ <lucid>/main Translation-en_US
Ign http://deb.torproject.org <lucid> Release                        
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://deb.torproject.org <lucid>/main Sources
Hit http://extras.ubuntu.com maverick/main Sources
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:4 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://deb.torproject.org <lucid>/main i386 Packages             
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:5 http://archive.ubuntu.com maverick Release [39.8kB]
Ign http://deb.torproject.org <lucid>/main Sources   
Ign http://deb.torproject.org <lucid>/main i386 Packages
Err http://deb.torproject.org <lucid>/main Sources                     
  404  Not Found [IP: 86.59.30.36 80]
Get:6 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://deb.torproject.org <lucid>/main i386 Packages
  404  Not Found [IP: 86.59.30.36 80]
Get:7 http://archive.ubuntu.com maverick-security Release [27.2kB]
Get:8 http://archive.ubuntu.com maverick/main Sources [829kB]
Get:9 http://archive.ubuntu.com maverick/restricted Sources [4,370B]
Get:10 http://archive.ubuntu.com maverick/universe Sources [4,179kB]
Get:11 http://archive.ubuntu.com maverick/multiverse Sources [151kB]           
Get:12 http://archive.ubuntu.com maverick/main i386 Packages [1,492kB]         
Get:13 http://archive.ubuntu.com maverick/restricted i386 Packages [5,992B]    
Get:14 http://archive.ubuntu.com maverick/universe i386 Packages [5,791kB]     
Get:15 http://archive.ubuntu.com maverick/multiverse i386 Packages [183kB]     
Get:16 http://archive.ubuntu.com maverick-updates/main Sources [39.1kB]        
Get:17 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]     
Get:18 http://archive.ubuntu.com maverick-updates/universe Sources [11.8kB]    
Get:19 http://archive.ubuntu.com maverick-updates/multiverse Sources [651B]    
Get:20 http://archive.ubuntu.com maverick-updates/main i386 Packages [100kB]   
Get:21 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:22 http://archive.ubuntu.com maverick-updates/universe i386 Packages [38.0kB]
Get:23 http://archive.ubuntu.com maverick-updates/multiverse i386 Packages [1,963B]
Get:24 http://archive.ubuntu.com maverick-security/main Sources [12.7kB]       
Get:25 http://archive.ubuntu.com maverick-security/restricted Sources [14B]    
Get:26 http://archive.ubuntu.com maverick-security/universe Sources [3,279B]   
Get:27 http://archive.ubuntu.com maverick-security/multiverse Sources [651B]   
Get:28 http://archive.ubuntu.com maverick-security/main i386 Packages [36.3kB] 
Get:29 http://archive.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:30 http://archive.ubuntu.com maverick-security/universe i386 Packages [13.1kB]
Get:31 http://archive.ubuntu.com maverick-security/multiverse i386 Packages [1,660B]
Fetched 13.0MB in 19s (659kB/s)                                                
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/source/Sources.gz  404  Not Found [IP: 86.59.30.36 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.30.36 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
jedi@Ubuntu01:~$ sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'tor' has no installation candidate
E: Unable to locate package tor-geoipdb
jedi@Ubuntu01:~$ [/PHP]

---

### Post by Swagman on 2010-11-17
```
sudo apt-get install tor
```

No gap in apt-get.. install is the do command

---

### Post by alphaamanitin on 2010-11-17
> **Tyler89 said:**
> Ign [http://deb.torproject.org](http://deb.torproject.org) <lucid>/main Sources


Not sure how you input it but you should add this to your /etc/apt/sources.list

```
deb     http://deb.torproject.org/torproject.org lucid main

```

It doesn't look like that is what has been used from your quoted output of apt-get update

AlphaA

---

### Post by Swagman on 2010-11-17
He could either use terminal and nano /etc/apt/sources.list or use update manager/settings add (other software)

---

### Post by Tyler89 on 2010-11-17
Okay, I have once more entered in the commands as shown on Tor, and tried to be sure that I entered them correctly, as I know they are case-sensitive. I keep getting a 404 not found when downloading a few files, which you will find near the bottom of this source code. I'm guessing this is the probably cause of it not correctly installing? (Source code at the bottom of this post)

@ Swagman 

I am not too sure if I have added it correctly, as this is my first time around the block. Here is a picture of how I executed that portion of the task.

[IMG]http://img600.imageshack.us/img600/2936/screenshotf.png[/IMG]


[PHP]
jedi@Ubuntu01:~$ sudo ap-get tor-geoipdb
[sudo] password for jedi: 
sudo: ap-get: command not found
jedi@Ubuntu01:~$ sudo apt-get tor-geoipdb
E: Invalid operation tor-geoipdb
jedi@Ubuntu01:~$ sudo tor-geoipdb
sudo: tor-geoipdb: command not found
jedi@Ubuntu01:~$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: directory `/home/jedi/.gnupg' created
gpg: new configuration file `/home/jedi/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/jedi/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/jedi/.gnupg/secring.gpg' created
gpg: keyring `/home/jedi/.gnupg/pubring.gpg' created
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: /home/jedi/.gnupg/trustdb.gpg: trustdb created
gpg: key 886DDD89: public key "deb.torproject.org archive signing key" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
jedi@Ubuntu01:~$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
OK
jedi@Ubuntu01:~$ apg-get update
No command 'apg-get' found, did you mean:
 Command 'apt-get' from package 'apt' (main)
apg-get: command not found
jedi@Ubuntu01:~$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jedi@Ubuntu01:~$ gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
gpg: failed to create temporary file `/home/jedi/.gnupg/.#lk0x8c938d0.Ubuntu01.1817': Permission denied
gpg: keyblock resource `/home/jedi/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/jedi/.gnupg/.#lk0x8c95118.Ubuntu01.1817': Permission denied
gpg: keyblock resource `/home/jedi/.gnupg/pubring.gpg': general error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
jedi@Ubuntu01:~$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add-
Usage: apt-key [--keyring file] [command] [arguments]

Manage apt's list of trusted keys

  apt-key add <file>          - add the key contained in <file> ('-' for stdin)
  apt-key del <keyid>         - remove the key <keyid>
  apt-key export <keyid>      - output the key <keyid>
  apt-key exportall           - output all trusted keys
  apt-key update              - update keys using the keyring package
  apt-key net-update          - update keys using the network
  apt-key list                - list keys
  apt-key finger              - list fingerprints
  apt-key adv                 - pass advanced options to gpg (download key)

If no specific keyring file is given the command applies to all keyring files.
jedi@Ubuntu01:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com maverick Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Get:2 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en           
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://deb.torproject.org <lucid> Release.gpg
Ign http://deb.torproject.org/torproject.org/ <lucid>/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:3 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://deb.torproject.org/torproject.org/ <lucid>/main Translation-en_US
Ign http://deb.torproject.org <lucid> Release                        
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://deb.torproject.org <lucid>/main Sources
Hit http://extras.ubuntu.com maverick/main Sources
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:4 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://deb.torproject.org <lucid>/main i386 Packages             
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Get:5 http://archive.ubuntu.com maverick Release [39.8kB]
Ign http://deb.torproject.org <lucid>/main Sources   
Ign http://deb.torproject.org <lucid>/main i386 Packages
Err http://deb.torproject.org <lucid>/main Sources                     
  404  Not Found [IP: 86.59.30.36 80]
Get:6 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Err http://deb.torproject.org <lucid>/main i386 Packages
  404  Not Found [IP: 86.59.30.36 80]
Get:7 http://archive.ubuntu.com maverick-security Release [27.2kB]
Get:8 http://archive.ubuntu.com maverick/main Sources [829kB]
Get:9 http://archive.ubuntu.com maverick/restricted Sources [4,370B]
Get:10 http://archive.ubuntu.com maverick/universe Sources [4,179kB]
Get:11 http://archive.ubuntu.com maverick/multiverse Sources [151kB]           
Get:12 http://archive.ubuntu.com maverick/main i386 Packages [1,492kB]         
Get:13 http://archive.ubuntu.com maverick/restricted i386 Packages [5,992B]    
Get:14 http://archive.ubuntu.com maverick/universe i386 Packages [5,791kB]     
Get:15 http://archive.ubuntu.com maverick/multiverse i386 Packages [183kB]     
Get:16 http://archive.ubuntu.com maverick-updates/main Sources [39.1kB]        
Get:17 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]     
Get:18 http://archive.ubuntu.com maverick-updates/universe Sources [11.8kB]    
Get:19 http://archive.ubuntu.com maverick-updates/multiverse Sources [651B]    
Get:20 http://archive.ubuntu.com maverick-updates/main i386 Packages [100kB]   
Get:21 http://archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:22 http://archive.ubuntu.com maverick-updates/universe i386 Packages [38.0kB]
Get:23 http://archive.ubuntu.com maverick-updates/multiverse i386 Packages [1,963B]
Get:24 http://archive.ubuntu.com maverick-security/main Sources [12.7kB]       
Get:25 http://archive.ubuntu.com maverick-security/restricted Sources [14B]    
Get:26 http://archive.ubuntu.com maverick-security/universe Sources [3,279B]   
Get:27 http://archive.ubuntu.com maverick-security/multiverse Sources [651B]   
Get:28 http://archive.ubuntu.com maverick-security/main i386 Packages [36.3kB] 
Get:29 http://archive.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:30 http://archive.ubuntu.com maverick-security/universe i386 Packages [13.1kB]
Get:31 http://archive.ubuntu.com maverick-security/multiverse i386 Packages [1,660B]
Fetched 13.0MB in 19s (659kB/s)                                                
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/source/Sources.gz  404  Not Found [IP: 86.59.30.36 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.30.36 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
jedi@Ubuntu01:~$ sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'tor' has no installation candidate
E: Unable to locate package tor-geoipdb
jedi@Ubuntu01:~$ clear

jedi@Ubuntu01:~$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
[sudo] password for jedi: 
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jedi@Ubuntu01:~$ gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
gpg: failed to create temporary file `/home/jedi/.gnupg/.#lk0x952d8d0.Ubuntu01.2150': Permission denied
gpg: keyblock resource `/home/jedi/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/jedi/.gnupg/.#lk0x952f118.Ubuntu01.2150': Permission denied
gpg: keyblock resource `/home/jedi/.gnupg/pubring.gpg': general error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
jedi@Ubuntu01:~$ gpg -export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89
gpg: Invalid option "-export"
jedi@Ubuntu01:~$ sudo gpg --export A3C40F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key - 
gpg: WARNING: nothing exported
Usage: apt-key [--keyring file] [command] [arguments]

Manage apt's list of trusted keys

  apt-key add <file>          - add the key contained in <file> ('-' for stdin)
  apt-key del <keyid>         - remove the key <keyid>
  apt-key export <keyid>      - output the key <keyid>
  apt-key exportall           - output all trusted keys
  apt-key update              - update keys using the keyring package
  apt-key net-update          - update keys using the network
  apt-key list                - list keys
  apt-key finger              - list fingerprints
  apt-key adv                 - pass advanced options to gpg (download key)

If no specific keyring file is given the command applies to all keyring files.
jedi@Ubuntu01:~$ sudo gpg -export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DD89 | sudo apt-key add - tor
gpg: Invalid option "-export"
gpg: no valid OpenPGP data found.
jedi@Ubuntu01:~$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - tor
OK
jedi@Ubuntu01:~$ sudo apt-get update
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en           
Hit http://archive.ubuntu.com maverick Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release                        
Ign http://deb.torproject.org <lucid> Release.gpg                    
Ign http://deb.torproject.org/torproject.org/ <lucid>/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://deb.torproject.org/torproject.org/ <lucid>/main Translation-en_US
Get:2 http://deb.torproject.org lucid Release.gpg [489B]
Ign http://deb.torproject.org/torproject.org/ lucid/main Translation-en       
Ign http://deb.torproject.org/torproject.org/ lucid/main Translation-en_US
Ign http://deb.torproject.org <lucid> Release                        
Hit http://archive.ubuntu.com maverick-updates Release.gpg           
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                   
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Get:3 http://deb.torproject.org lucid Release [2,224B]               
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://deb.torproject.org <lucid>/main Sources
Ign http://deb.torproject.org <lucid>/main i386 Packages
Hit http://archive.ubuntu.com maverick Release 
Hit http://archive.ubuntu.com maverick-updates Release
Hit http://archive.ubuntu.com maverick-security Release              
Ign http://deb.torproject.org lucid/main Sources                     
Ign http://deb.torproject.org lucid/main i386 Packages               
Ign http://deb.torproject.org <lucid>/main Sources                   
Hit http://archive.ubuntu.com maverick/main Sources                  
Ign http://deb.torproject.org <lucid>/main i386 Packages
Ign http://deb.torproject.org lucid/main Sources
Ign http://deb.torproject.org lucid/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Err http://deb.torproject.org <lucid>/main Sources
  404  Not Found [IP: 86.59.30.36 80]
Err http://deb.torproject.org <lucid>/main i386 Packages
  404  Not Found [IP: 86.59.30.36 80]
Get:4 http://deb.torproject.org lucid/main Sources [1,961B]
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources  
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Get:5 http://deb.torproject.org lucid/main i386 Packages [3,899B]
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Fetched 8,638B in 1s (4,943B/s)
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/source/Sources.gz  404  Not Found [IP: 86.59.30.36 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.30.36 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
jedi@Ubuntu01:~$ sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  polipo socat tsocks
Suggested packages:
  mixmaster mixminion anon-proxy
The following NEW packages will be installed:
  polipo socat tor tor-geoipdb tsocks
0 upgraded, 5 newly installed, 0 to remove and 27 not upgraded.
Need to get 3,081kB of archives.
After this operation, 7,864kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ maverick/universe polipo i386 1.0.4.1-1.1 [185kB]
Get:2 http://deb.torproject.org/torproject.org/ lucid/main tor i386 0.2.1.26-1~lucid+1 [1,469kB]
Get:3 http://archive.ubuntu.com/ubuntu/ maverick/universe tsocks i386 1.8beta5-9.1 [276kB]
Get:4 http://archive.ubuntu.com/ubuntu/ maverick/universe socat i386 1.7.1.3-1 [346kB]
Get:5 http://deb.torproject.org/torproject.org/ lucid/main tor-geoipdb all 0.2.1.26-1~lucid+1 [804kB]
Fetched 3,081kB in 5s (598kB/s)                      
Selecting previously deselected package polipo.
(Reading database ... 137707 files and directories currently installed.)
Unpacking polipo (from .../polipo_1.0.4.1-1.1_i386.deb) ...
Selecting previously deselected package tsocks.
Unpacking tsocks (from .../tsocks_1.8beta5-9.1_i386.deb) ...
Selecting previously deselected package tor.
Unpacking tor (from .../tor_0.2.1.26-1~lucid+1_i386.deb) ...
Selecting previously deselected package socat.
Unpacking socat (from .../socat_1.7.1.3-1_i386.deb) ...
Selecting previously deselected package tor-geoipdb.
Unpacking tor-geoipdb (from .../tor-geoipdb_0.2.1.26-1~lucid+1_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up polipo (1.0.4.1-1.1) ...
Starting polipo: polipo.
Setting up tsocks (1.8beta5-9.1) ...
Setting up tor (0.2.1.26-1~lucid+1) ...
Something or somebody made /var/run/tor disappear.
Creating one for you again.
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Nov 17 11:13:00.566 [notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Nov 17 11:13:00.585 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Nov 17 11:13:00.587 [notice] Opening Socks listener on 127.0.0.1:9050
done.
Setting up socat (1.7.1.3-1) ...
Setting up tor-geoipdb (0.2.1.26-1~lucid+1) ...
jedi@Ubuntu01:~$ 
[/PHP]

---

### Post by Swagman on 2010-11-17
Wow.. BIG pic

Yup.. That looks right !!

I take it you are still not having any joy though ?

In a terminal enter sudo nano /etc/apt/sources.list

and check what your entry verses previous entries look like

---

### Post by Tyler89 on 2010-11-17
@ Swagman

I have done what you have asked me to do, but I am not too sure how to read it, so I'm going to just paste the output I got from Terminal. 

Again, thank you and everyone else so far for helping me out. Since you said what I entered is all correct in Terminal and update manager, Swagman, I'm now working to get Polipo to work. I knew Linux was going to be tough to get things running, but this makes me want to run for the hills. Ha. Ha. 

Thanks again,

[PHP]  GNU nano 2.2.4         File: /etc/apt/sources.list                         

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ mav$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe

^G Get Help ^O WriteOut ^R Read File^Y Prev Page^K Cut Text ^C Cur Pos
^X Exit     ^J Justify  ^W Where Is ^V Next Page^U UnCut Tex^T To Spell[/PHP]

---

### Post by Tlingit on 2010-11-17
> **Tyler89 said:**
> @ Swagman

I have done what you have asked me to do, but I am not too sure how to read it, so I'm going to just paste the output I got from Terminal. 

Again, thank you and everyone else so far for helping me out. Since you said what I entered is all correct in Terminal and update manager, Swagman, I'm now working to get Polipo to work. I knew Linux was going to be tough to get things running, but this makes me want to run for the hills. Ha. Ha. 

Thanks again,

[PHP]  GNU nano 2.2.4         File: /etc/apt/sources.list                         

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ mav$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe

^G Get Help ^O WriteOut ^R Read File^Y Prev Page^K Cut Text ^C Cur Pos
^X Exit     ^J Justify  ^W Where Is ^V Next Page^U UnCut Tex^T To Spell[/PHP]

put this
```
deb     http://deb.torproject.org/torproject.org lucid main
```

right under the similar line starting with "deb"

---

### Post by endotherm on 2010-11-17
yeah, the problem with apt-get update appears to be the deb line. from your output:
```

[COLOR=#000000][COLOR=#0000BB]W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/source/Sources.gz  404  Not Found [IP: 86.59.30.36 80]

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/<lucid>/main/binary-i386/Packages.gz  404  Not Found [IP: 86.59.30.36 80][/COLOR][/COLOR]

```

the angle braces ( .../<Lucid>/...)  should not be there. the URL does not exist, but if you remove them, then it comes up fine. 
if you fix your sources list, the rest should attend to itself.

---

### Post by Tyler89 on 2010-11-17
Hey, thanks for going back in and finding that <lucid> error I made in Update Manager. Anyways, I have fixed the problem now, and I would like you guys to review the output to make sure it all looks good. Finally, I got something done after a few hours. >.< Ha. Ha. 

[PHP]
jedi@Ubuntu01:~$ sudo gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg: requesting key 886DDD89 from hkp server keys.gnupg.net
gpg: key 886DDD89: "deb.torproject.org archive signing key" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jedi@Ubuntu01:~$ sudo gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add - tor
OK
jedi@Ubuntu01:~$ sudo apt-get update
Hit http://extras.ubuntu.com maverick Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en   
Hit http://archive.ubuntu.com maverick Release.gpg                  
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://deb.torproject.org lucid Release.gpg
Ign http://deb.torproject.org/torproject.org/ lucid/main Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release  
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://deb.torproject.org/torproject.org/ lucid/main Translation-en_US
Hit http://deb.torproject.org lucid Release                          
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-updates Release.gpg           
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://extras.ubuntu.com maverick/main Sources                   
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://deb.torproject.org lucid/main Sources
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://archive.ubuntu.com maverick-security Release.gpg          
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://deb.torproject.org lucid/main i386 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.ubuntu.com maverick Release 
Hit http://archive.ubuntu.com maverick-updates Release
Ign http://deb.torproject.org lucid/main Sources                     
Hit http://archive.ubuntu.com maverick-security Release
Hit http://archive.ubuntu.com maverick/main Sources                  
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Ign http://deb.torproject.org lucid/main i386 Packages
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-updates/main Sources
Hit http://archive.ubuntu.com maverick-updates/restricted Sources
Hit http://archive.ubuntu.com maverick-updates/universe Sources
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://deb.torproject.org lucid/main Sources
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/main Sources
Hit http://archive.ubuntu.com maverick-security/restricted Sources
Hit http://archive.ubuntu.com maverick-security/universe Sources
Hit http://archive.ubuntu.com maverick-security/multiverse Sources
Hit http://deb.torproject.org lucid/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Reading package lists... Done
jedi@Ubuntu01:~$ sudo apt-get install tor tor-geoipdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tor is already the newest version.
tor-geoipdb is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
jedi@Ubuntu01:~$ ^C
jedi@Ubuntu01:~$ [/PHP]

---

### Post by endotherm on 2010-11-17
looks good to me. 
gl and hf!

---

