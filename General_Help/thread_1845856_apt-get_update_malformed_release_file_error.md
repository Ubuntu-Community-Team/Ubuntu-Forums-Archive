---
title: "apt-get update malformed release file error"
date: 2011-09-17
forum: General Help
---

### Post by squigish on 2011-09-17
Whenever I run sudo apt-get update on my home computer (ubuntu lucid 10.04 64 bit) I receive the following error:

```

W: Failed to fetch http://ubuntu-mirror/ubuntu/dists/lucid/Release  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

```

(ubuntu-mirror is replaced with the url for a mirror of the official ubuntu package repos run by my university)

I get the same error when refreshing in synaptic.

However, when running sudo aptitude update, I usually get no error at all, but sometimes I get the following output, which I provide in two boxes, first just (what I think are) the relevant parts (two separate errors), and secondly the entire thing:

```

Hit http://ubuntu-mirror lucid Release                         
Err http://ubuntu-mirror lucid Release                         
  
Fetched 10.7kB in 33s (318B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ubuntu-mirror lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```



```

matt@halifax:~$ sudo aptitude update
Get:1 http://private-repo lucid Release.gpg [198B]                      
Get:2 http://ubuntu-mirror lucid Release.gpg [189B]            
Get:3 http://apt.spideroak.com release Release.gpg [189B]                       
Get:4 http://linux.dropbox.com lucid Release.gpg [489B]                         
Get:5 http://www.math.uiuc.edu stable Release.gpg [197B]                        
Get:6 http://dl.google.com stable Release.gpg [198B]                            
Get:7 http://deb.opera.com stable Release.gpg [189B]                            
Get:8 http://ppa.launchpad.net lucid Release.gpg [316B]                         
Get:9 http://archive.canonical.com lucid Release.gpg [198B]                     
Ign http://private-repo/ubuntu/ lucid/myrepo Translation-en_US          
Ign http://ubuntu-mirror/ubuntu/ lucid/main Translation-en_US  
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US               
Ign http://apt.spideroak.com/ubuntu-spideroak-hardy/ release/restricted Translation-en_US
Ign http://www.math.uiuc.edu/Macaulay2/Repositories/Ubuntu/ stable/main Translation-en_US
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US               
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Ign http://archive.canonical.com/ lucid/partner Translation-en_US               
Hit http://private-repo lucid Release                                   
Ign http://ubuntu-mirror/ubuntu/ lucid/restricted Translation-en_US
Hit http://linux.dropbox.com lucid Release                                      
Hit http://deb.opera.com stable Release                                         
Get:10 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Hit http://www.math.uiuc.edu stable Release                                     
Hit http://archive.canonical.com lucid Release                                  
Ign http://ubuntu-mirror/ubuntu/ lucid/universe Translation-en_US
Hit http://linux.dropbox.com lucid/main Packages                                
Ign http://ubuntu-mirror/ubuntu/ lucid/multiverse Translation-en_US
Hit http://www.math.uiuc.edu stable/main Packages                               
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages                         
Ign http://deb.opera.com stable/non-free Packages                               
Hit http://apt.spideroak.com release Release                                    
Get:11 http://ubuntu-mirror lucid-updates Release.gpg [198B]   
Hit http://ppa.launchpad.net lucid Release                                      
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US        
Ign http://ubuntu-mirror/ubuntu/ lucid-updates/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                      
Hit http://private-repo lucid/myrepo Packages                           
Get:12 http://dl.google.com stable Release.gpg [189B]                           
Ign http://apt.spideroak.com release/restricted Packages                        
Ign http://ubuntu-mirror/ubuntu/ lucid-updates/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid/main Packages                                
Ign http://ubuntu-mirror/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_US           
Ign http://apt.spideroak.com release/restricted Packages                        
Hit http://ppa.launchpad.net lucid/main Packages                                
Ign http://ubuntu-mirror/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://apt.spideroak.com release/restricted Packages                        
Ign http://deb.opera.com stable/non-free Packages                               
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US               
Get:13 http://ubuntu-mirror lucid-security Release.gpg [198B]  
Hit http://deb.opera.com stable/non-free Packages                               
Ign http://ubuntu-mirror/ubuntu/ lucid-security/main Translation-en_US
Get:14 http://dl.google.com stable Release [1,347B]                             
Ign http://ubuntu-mirror/ubuntu/ lucid-security/restricted Translation-en_US
Get:15 http://dl.google.com stable Release [2,544B]                             
Ign http://ubuntu-mirror/ubuntu/ lucid-security/universe Translation-en_US
Get:16 http://dl.google.com stable/main Packages [1,180B]                       
Ign http://ubuntu-mirror/ubuntu/ lucid-security/multiverse Translation-en_US
Get:17 http://dl.google.com stable/non-free Packages [1,025B]                   
Get:18 http://ubuntu-mirror lucid-backports Release.gpg [198B] 
Get:19 http://dl.google.com stable/main Packages [1,104B]                       
Ign http://ubuntu-mirror/ubuntu/ lucid-backports/main Translation-en_US
Ign http://ubuntu-mirror/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://ubuntu-mirror/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://ubuntu-mirror/ubuntu/ lucid-backports/multiverse Translation-en_US
Get:20 http://ubuntu-mirror lucid Release.gpg [197B]           
Ign http://ubuntu-mirror/medibuntu/ lucid/free Translation-en_US
Ign http://ubuntu-mirror/medibuntu/ lucid/non-free Translation-en_US
Hit http://ubuntu-mirror lucid Release                         
Err http://ubuntu-mirror lucid Release                         
  
Hit http://ubuntu-mirror lucid-updates Release                 
Hit http://ubuntu-mirror lucid-security Release                
Hit http://ubuntu-mirror lucid-backports Release               
Hit http://ubuntu-mirror lucid Release                         
Hit http://ubuntu-mirror lucid-updates/main Packages           
Hit http://ubuntu-mirror lucid-updates/restricted Packages     
Hit http://ubuntu-mirror lucid-updates/universe Packages       
Hit http://ubuntu-mirror lucid-updates/multiverse Packages     
Hit http://ubuntu-mirror lucid-security/main Packages          
Hit http://ubuntu-mirror lucid-security/restricted Packages
Hit http://ubuntu-mirror lucid-security/universe Packages
Hit http://ubuntu-mirror lucid-security/multiverse Packages
Hit http://ubuntu-mirror lucid-backports/main Packages
Hit http://ubuntu-mirror lucid-backports/restricted Packages
Hit http://ubuntu-mirror lucid-backports/universe Packages
Hit http://ubuntu-mirror lucid-backports/multiverse Packages
Hit http://ubuntu-mirror lucid/free Packages
Hit http://ubuntu-mirror lucid/non-free Packages
Fetched 10.7kB in 33s (318B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ubuntu-mirror lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>



```

What's weird about this is the following:  
[LIST]
[*]apt-get and aptitude are giving seemingly unrelated errors about the same file
[*]aptitude gives inconsistent output (I hate intermittent errors!)
[*]I don't get this error (using apt-get, synaptic, or aptitude), when I update my work computer, which has *the exact same* /etc/apt/sources.list file.
[/LIST]

Both of my computers are running lucid 10.04 with all the latest updates.  The administrator for my university's mirror has said that nobody else has mentioned this problem to him, and confirmed that he gets an error-free output from his home computer (showing that the problem is not that I'm off-campus).

Anybody have any ideas?

---

### Post by squigish on 2011-09-22
bump.

---

### Post by raja.genupula on 2011-09-22
System->update manager->Settings->ubuntu software->at server choose another server and try again .
let me know what you got

---

