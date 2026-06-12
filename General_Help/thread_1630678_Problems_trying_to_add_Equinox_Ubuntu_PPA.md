---
title: "Problems trying to add Equinox Ubuntu PPA"
date: 2010-11-25
forum: General Help
---

### Post by bluelamp999 on 2010-11-25
Hello friends,

I'm trying to add the Equinox Ubuntu PPA with...

```
sudo add-apt-repository ppa:tiheum/equinox && sudo apt-get update
```

However all is not going well, here's the output...

```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv BC9EE88A229B9C049A06D1FB464AD83D4631BBEA
gpg: requesting key 4631BBEA from hkp server keyserver.ubuntu.com
gpg: key 4631BBEA: public key "Launchpad equinoxart" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_IE
Get:1 http://extras.ubuntu.com maverick Release.gpg [316B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en             
Hit http://archive.ubuntu.com maverick Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://ppa.launchpad.net maverick Release.gpg
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_IE
Hit http://ppa.launchpad.net maverick Release                        
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IE 
Get:2 http://extras.ubuntu.com maverick Release [57.3kB]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_IE  
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_IE
Get:3 http://archive.ubuntu.com maverick-updates Release.gpg [198B]
Hit http://ppa.launchpad.net maverick Release           
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_IE
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_IE
Get:4 http://archive.ubuntu.com maverick-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_IE
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_IE
Hit http://archive.ubuntu.com maverick Release
Get:5 http://archive.ubuntu.com maverick-updates Release [31.4kB]
Get:6 http://archive.ubuntu.com maverick-security Release [27.2kB]
Hit http://archive.ubuntu.com maverick/main Sources   
Hit http://archive.ubuntu.com maverick/restricted Sources
Hit http://archive.ubuntu.com maverick/universe Sources
Hit http://archive.ubuntu.com maverick/multiverse Sources
Hit http://archive.ubuntu.com maverick/main amd64 Packages
Hit http://archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://archive.ubuntu.com maverick/universe amd64 Packages
Hit http://archive.ubuntu.com maverick/multiverse amd64 Packages
Get:7 http://archive.ubuntu.com maverick-updates/main Sources [41.4kB]
Get:8 http://archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:9 http://archive.ubuntu.com maverick-updates/universe Sources [13.5kB]
Get:10 http://archive.ubuntu.com maverick-updates/multiverse Sources [649B]
Get:11 http://archive.ubuntu.com maverick-updates/main amd64 Packages [110kB]
Get:12 http://archive.ubuntu.com maverick-updates/restricted amd64 Packages [14B]
Get:13 http://archive.ubuntu.com maverick-updates/universe amd64 Packages [44.6kB]
Get:14 http://archive.ubuntu.com maverick-updates/multiverse amd64 Packages [1,826B]
Get:15 http://archive.ubuntu.com maverick-security/main Sources [13.8kB]
Get:16 http://archive.ubuntu.com maverick-security/restricted Sources [14B]
Get:17 http://archive.ubuntu.com maverick-security/universe Sources [4,365B]
Get:18 http://archive.ubuntu.com maverick-security/multiverse Sources [649B]
Get:19 http://archive.ubuntu.com maverick-security/main amd64 Packages [39.5kB]
Get:20 http://archive.ubuntu.com maverick-security/restricted amd64 Packages [14B]
Get:21 http://archive.ubuntu.com maverick-security/universe amd64 Packages [18.4kB]
Get:22 http://archive.ubuntu.com maverick-security/multiverse amd64 Packages [1,531B]
Fetched 349kB in 1s (271kB/s)                           
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Can anyone please tell me what's going on here? Or another way to install the Equinox theme?

I installed it without problems on the same machine about 10 days ago...

I'm running 10.10 64 bit.

Many thanks

---

### Post by plucky on 2010-11-25
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Open a terminal and copy and paste each command ```
gpg --keyserver keyserver.ubuntu.com --recv 02FDF932
gpg --export --armor 02FDF932 | sudo apt-key add -
sudo apt-get update
```

Good Luck

---

### Post by bluelamp999 on 2010-11-25
> **plucky said:**
> Open a terminal and copy and paste each command ```
gpg --keyserver keyserver.ubuntu.com --recv 02FDF932
gpg --export --armor 02FDF932 | sudo apt-key add -
sudo apt-get update
```

Good Luck

Thank you, thank you, thank you!

Worked perfectly...

I've been using Ubuntu for ~3 years now and the above is some pretty arcane looking stuff but it sorted the issue...

Thanks again, Plucky.

---

### Post by Nordoelum on 2010-11-28
Thank you, plucky ;) It solved my problem.

---

