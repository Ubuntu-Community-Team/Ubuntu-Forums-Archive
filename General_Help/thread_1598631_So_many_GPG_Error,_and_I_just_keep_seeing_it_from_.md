---
title: "So many GPG Error, and I just keep seeing it from the first"
date: 2010-10-16
forum: General Help
---

### Post by maizuddin35 on 2010-10-16
Hello guys.

From the start ive been using ubuntu .and now im using lucid 10.04, what I see when I turn on update the multiverse and universe and the others, what I found is, Error.

Here are the error from my terminal . It just annoys me, for now, I don't have any problem with any of it yet, and I don't want to have one. Is there anyone, thanks in advanced.

ha, here the output :
```
adib@adib-desktop:~$ sudo apt-get update
[sudo] password for adib: 
Hit http://ubuntu.bytecraft.com.my lucid Release.gpg                                                                     
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid/main Translation-en_US                                                  
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid/restricted Translation-en_US                                            
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid/universe Translation-en_US                                              
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid/multiverse Translation-en_US                                            
Hit http://ubuntu.bytecraft.com.my lucid-updates Release.gpg                                                             
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-updates/main Translation-en_US                                          
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-updates/restricted Translation-en_US                                    
Get:1 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                  
Ign http://ppa.launchpad.net/and471/kazam-daily-stable/ubuntu/ lucid/main Translation-en_US                              
Get:2 http://ppa.launchpad.net lucid Release.gpg [316B]                                                            
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-updates/universe Translation-en_US                                
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-updates/multiverse Translation-en_US                              
Hit http://ubuntu.bytecraft.com.my lucid-security Release.gpg                                                      
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-security/main Translation-en_US                                   
Hit http://archive.canonical.com lucid Release.gpg                                                                 
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                           
Ign http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu/ lucid/main Translation-en_US                 
Get:3 http://ppa.launchpad.net lucid Release.gpg [307B]                                      
Ign http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu/ lucid/main Translation-en_US                              
Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]                                                            
Ign http://ppa.launchpad.net/mixxxdevelopers/ppa/ubuntu/ lucid/main Translation-en_US                              
Get:5 http://ppa.launchpad.net lucid Release.gpg [316B]                                                            
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-security/restricted Translation-en_US                             
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-security/universe Translation-en_US                               
Ign http://ubuntu.bytecraft.com.my/ubuntu/ lucid-security/multiverse Translation-en_US                             
Hit http://ubuntu.bytecraft.com.my lucid Release                                                                   
Hit http://ubuntu.bytecraft.com.my lucid-updates Release                                                           
Ign http://ppa.launchpad.net/murrine-daily/ppa/ubuntu/ lucid/main Translation-en_US                                      
Get:6 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                  
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ lucid/main Translation-en_US                                   
Hit http://archive.canonical.com lucid Release                                                                     
Hit http://ubuntu.bytecraft.com.my lucid-security Release                                                          
Get:7 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                  
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US                                    
Get:8 http://ppa.launchpad.net lucid Release.gpg [316B]                                                            
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US                                  
Get:9 http://ppa.launchpad.net lucid Release.gpg [307B]                                                            
Ign http://ppa.launchpad.net/wfg/0ad/ubuntu/ lucid/main Translation-en_US                                          
Get:10 http://ppa.launchpad.net lucid Release [57.3kB]                                                             
Ign http://ppa.launchpad.net lucid Release                                                                               
Hit http://ubuntu.bytecraft.com.my lucid/main Sources                                                                    
Hit http://ubuntu.bytecraft.com.my lucid/restricted Sources                                                        
Hit http://ubuntu.bytecraft.com.my lucid/universe Sources                                                          
Hit http://ubuntu.bytecraft.com.my lucid/multiverse Sources                                                        
Hit http://ubuntu.bytecraft.com.my lucid/main Packages                                                             
Hit http://archive.canonical.com lucid/partner Packages                                                            
Hit http://ubuntu.bytecraft.com.my lucid/restricted Packages                                                       
Hit http://ubuntu.bytecraft.com.my lucid/universe Packages                                   
Hit http://ubuntu.bytecraft.com.my lucid/multiverse Packages                                 
Hit http://ubuntu.bytecraft.com.my lucid-updates/main Packages                               
Hit http://ubuntu.bytecraft.com.my lucid-updates/restricted Packages                         
Hit http://ubuntu.bytecraft.com.my lucid-updates/universe Packages                                                 
Hit http://ubuntu.bytecraft.com.my lucid-updates/multiverse Packages                                               
Hit http://ubuntu.bytecraft.com.my lucid-updates/main Sources                                                      
Get:11 http://ppa.launchpad.net lucid Release [57.3kB]                                       
Get:12 http://ppa.launchpad.net lucid Release [57.3kB]                                                                   
Ign http://ppa.launchpad.net lucid Release                                                                               
Ign http://ppa.launchpad.net lucid Release                                                                               
Get:13 http://ppa.launchpad.net lucid Release [57.3kB]                                                                   
Get:14 http://ppa.launchpad.net lucid Release [57.3kB]                                                             
Ign http://ppa.launchpad.net lucid Release                                                                               
Ign http://ppa.launchpad.net lucid Release                                                                               
Get:15 http://ppa.launchpad.net lucid Release [57.3kB]                                                                   
Ign http://ppa.launchpad.net lucid Release                                                                               
Hit http://ubuntu.bytecraft.com.my lucid-updates/restricted Sources                                                      
Hit http://ubuntu.bytecraft.com.my lucid-updates/universe Sources                                                  
Get:16 http://ppa.launchpad.net lucid Release [57.3kB]                                                             
Get:17 http://ppa.launchpad.net lucid Release [57.3kB]                                                                   
Ign http://ppa.launchpad.net lucid Release                                                                               
Ign http://ppa.launchpad.net lucid Release                                                                               
Hit http://ubuntu.bytecraft.com.my lucid-updates/multiverse Sources                                                      
Hit http://ubuntu.bytecraft.com.my lucid-security/main Packages                                                    
Hit http://ubuntu.bytecraft.com.my lucid-security/restricted Packages                                              
Hit http://ubuntu.bytecraft.com.my lucid-security/universe Packages                                                
Hit http://ubuntu.bytecraft.com.my lucid-security/multiverse Packages                        
Hit http://archive.canonical.com lucid/partner Sources                                                             
Hit http://ubuntu.bytecraft.com.my lucid-security/main Sources                                                           
Hit http://ubuntu.bytecraft.com.my lucid-security/restricted Sources                                                     
Hit http://ubuntu.bytecraft.com.my lucid-security/universe Sources                                                       
Hit http://ubuntu.bytecraft.com.my lucid-security/multiverse Sources                                                     
Get:18 http://ppa.launchpad.net lucid Release [57.2kB]                                                                   
Ign http://ppa.launchpad.net lucid Release                                                                               
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Hit http://ppa.launchpad.net lucid/main Packages                                                                         
Err http://dl.google.com stable Release.gpg                                                                              
  Could not connect to dl.google.com:80 (64.233.181.190). - connect (110: Connection timed out) [IP: 64.233.181.190 80]
Err http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US
  Unable to connect to dl.google.com:http: [IP: 64.233.181.190 80]
Ign http://dl.google.com stable Release           
Ign http://dl.google.com stable/main Packages
Ign http://dl.google.com stable/main Packages
Err http://dl.google.com stable/main Packages
  Unable to connect to dl.google.com:http: [IP: 64.233.181.190 80]
Fetched 2,835B in 1min 24s (34B/s)
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DEF31B9A9E345C0
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F678A01569113AE
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FD58F8C9E8EF47D2
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AF5ED91C56978EF9
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8CA7A6E8E4FA953A
W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg  Could not connect to dl.google.com:80 (64.233.181.190). - connect (110: Connection timed out) [IP: 64.233.181.190 80]

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en_US.bz2  Unable to connect to dl.google.com:http: [IP: 64.233.181.190 80]

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages.gz  Unable to connect to dl.google.com:http: [IP: 64.233.181.190 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
adib@adib-desktop:~$ 

```

---

### Post by maizuddin35 on 2010-10-16
bump

---

### Post by maizuddin35 on 2010-10-20
is there someone know about how to fix this?

---

### Post by plucky on 2010-10-21
> **maizuddin35 said:**
> is there someone know about how to fix this?

Have you even tried a search on the forum for "GPG error".

This [might help](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)

Good Luck

---

### Post by oldos2er on 2010-10-21
Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

where KEYID is number shown in error msg

---

### Post by sikander3786 on 2010-10-21
You can also import all the keys automatically. Tutorial here.

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

### Post by maizuddin35 on 2010-10-21
thanks for the reply, I have google, and search here. but most of the findings just temporary, I don't know why, and some , not work at all. What I see since jaunty, this gpg error just don't stop doesn't? when I tick the universe and multiverse, the gpg error will appear, and sometimes, it just turn out to be this way all of suddent. A wierd thing to me. What does make this gpg error ? 
Thanks by the way for all your reply. I will try the link.

---

### Post by plucky on 2010-10-21
> when I tick the universe and multiverse, the gpg error will appear, and sometimes, it just turn out to be this way all of suddent


Change your download server!!

Open **System > Administration > Software Sources** and in the "Download From" box select another server and try again.Also try disabling all the non-canonical sources such as google and the PPAs and see if you get the same problems.

Good Luck

---

### Post by maizuddin35 on 2010-10-22
that might fix this. I will change my settings after this, I hope it goes well.

---

### Post by maizuddin35 on 2010-10-25
there is nothing much happen when I change the server to the main one. It just the same.

---

