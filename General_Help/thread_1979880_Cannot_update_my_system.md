---
title: "Cannot update my system"
date: 2012-05-14
forum: General Help
---

### Post by serhancan on 2012-05-14
Hello,

It has been three days that I started using an Unix based OS. Therefore I am not able to solve my problems on my own. However even though I have searched a lot, I could not solve my update problem. I am using Ubuntu 11.10 and tried updating directly with: sudo apt-get update and via update manager. When I try update manager I get the error: "check your internet connection" and  when I use "sudo apt-get update" I get the errors occuring due to the signature verification. I know that there are lots topics about my signature verification problem however none of them solved my problem or maybe I am missing something. Could you please help me?

Thanks,
Serhan

---

### Post by zvacet on 2012-05-14
Maybe changing server will help,so under synaptic>repositories> change to main or to faster (closer I don´t remember but you will see option).Reload and then also in synaptic press refresh ( that will do update) and after that mark all updates ( that will update your system).Of course you can do same thing from terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Zvlwab on 2012-05-14
try this:
```
sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG 16126D3A3ESC1192
```

and do the same for the other number mentioned.

For future posts: It would be handier if you copy the terminal output to your post instead of posting a picture.

---

### Post by serhancan on 2012-05-14
> **Zvlwab said:**
> try this:
```
sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG 16126D3A3ESC1192
```and do the same for the other number mentioned.

For future posts: It would be handier if you copy the terminal output to your post instead of posting a picture.

I tried that before too however it did not solve my problem: ```
 
serhan@serhan-Lenovo-B560:~$ sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG 40976EAF437D05B5
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
serhan@serhan-Lenovo-B560:~$ sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG 16126D3A3E5C1192
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
serhan@serhan-Lenovo-B560:~$ sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG B725097B3ACC3965
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

   
```

Still getting:

```
serhan@serhan-Lenovo-B560:~$ sudo apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                            
Ign http://cy.archive.ubuntu.com oneiric InRelease                                        
Ign http://cy.archive.ubuntu.com oneiric-updates InRelease                                 
Ign http://cy.archive.ubuntu.com oneiric-backports InRelease                               
Ign http://archive.canonical.com oneiric InRelease                                         
Ign http://ppa.launchpad.net oneiric InRelease                                             
Ign http://ppa.launchpad.net oneiric InRelease                                             
Ign http://ppa.launchpad.net oneiric InRelease                                             
Hit http://security.ubuntu.com oneiric-security Release.gpg                                
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                  
Hit http://cy.archive.ubuntu.com oneiric Release.gpg                                       
Hit http://cy.archive.ubuntu.com oneiric-updates Release.gpg         
Get:2 http://archive.canonical.com oneiric Release.gpg [198 B]                             
Get:3 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                            
Hit http://security.ubuntu.com oneiric-security Release                                                                     
Hit http://cy.archive.ubuntu.com oneiric-backports Release.gpg                             
Hit http://cy.archive.ubuntu.com oneiric Release                                           
Hit http://extras.ubuntu.com oneiric Release                                               
Hit http://archive.canonical.com oneiric Release                                           
Hit http://ppa.launchpad.net oneiric Release.gpg                                           
Hit http://ppa.launchpad.net oneiric Release                          
Err http://extras.ubuntu.com oneiric Release                                                
  
Err http://archive.canonical.com oneiric Release                                            
  
Ign http://ppa.launchpad.net oneiric Release                                                
Hit http://cy.archive.ubuntu.com oneiric-updates Release                                    
Hit http://cy.archive.ubuntu.com oneiric-backports Release           
Hit http://ppa.launchpad.net oneiric Release                                                
Hit http://ppa.launchpad.net oneiric Release                                                
Hit http://security.ubuntu.com oneiric-security/main Sources                                
Hit http://cy.archive.ubuntu.com oneiric/main Sources                                       
Hit http://cy.archive.ubuntu.com oneiric/restricted Sources          
Hit http://cy.archive.ubuntu.com oneiric/universe Sources
Hit http://cy.archive.ubuntu.com oneiric/multiverse Sources          
Hit http://cy.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://cy.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://cy.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://cy.archive.ubuntu.com oneiric/multiverse i386 Packages    
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex          
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/restricted Sources   
Hit http://security.ubuntu.com oneiric-security/universe Sources     
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://cy.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://cy.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://cy.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://cy.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://cy.archive.ubuntu.com oneiric-updates/main Sources
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://cy.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://cy.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Hit http://security.ubuntu.com oneiric-security/main Translation-en  
Hit http://cy.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/main Sources
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://cy.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://cy.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric/main Translation-en
Hit http://cy.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://cy.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric/universe Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Fetched 586 B in 1s (448 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by arpanaut on 2012-05-14
leave the "BADSIG" part out just enter the the actual key

---

### Post by serhancan on 2012-05-14
> **zvacet said:**
> Maybe changing server will help,so under synaptic>repositories> change to main or to faster (closer I don´t remember but you will see option).Reload and then also in synaptic press refresh ( that will do update) and after that mark all updates ( that will update your system).Of course you can do same thing from terminal

```
sudo apt-get update && sudo apt-get upgrade
```


It did not solve my problem also. Still getting the error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release](http://archive.canonical.com/ubuntu/dists/oneiric/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by serhancan on 2012-05-14
> **arpanaut said:**
> leave the "BADSIG" part out just enter the the actual key

Nothing's changed. :/

---

### Post by Zvlwab on 2012-05-15
> **serhancan said:**
> I tried that before too however it did not solve my problem: ```
 
serhan@serhan-Lenovo-B560:~$ sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG 40976EAF437D05B5
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
serhan@serhan-Lenovo-B560:~$ sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG 16126D3A3E5C1192
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
serhan@serhan-Lenovo-B560:~$ sudo apt-key --key-server keyserver.ubuntu.com --recv-keys BADSIG B725097B3ACC3965
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

   
```

Still getting:

```
serhan@serhan-Lenovo-B560:~$ sudo apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                            
Ign http://cy.archive.ubuntu.com oneiric InRelease                                        
Ign http://cy.archive.ubuntu.com oneiric-updates InRelease                                 
Ign http://cy.archive.ubuntu.com oneiric-backports InRelease                               
Ign http://archive.canonical.com oneiric InRelease                                         
Ign http://ppa.launchpad.net oneiric InRelease                                             
Ign http://ppa.launchpad.net oneiric InRelease                                             
Ign http://ppa.launchpad.net oneiric InRelease                                             
Hit http://security.ubuntu.com oneiric-security Release.gpg                                
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                  
Hit http://cy.archive.ubuntu.com oneiric Release.gpg                                       
Hit http://cy.archive.ubuntu.com oneiric-updates Release.gpg         
Get:2 http://archive.canonical.com oneiric Release.gpg [198 B]                             
Get:3 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                                                                            
Hit http://security.ubuntu.com oneiric-security Release                                                                     
Hit http://cy.archive.ubuntu.com oneiric-backports Release.gpg                             
Hit http://cy.archive.ubuntu.com oneiric Release                                           
Hit http://extras.ubuntu.com oneiric Release                                               
Hit http://archive.canonical.com oneiric Release                                           
Hit http://ppa.launchpad.net oneiric Release.gpg                                           
Hit http://ppa.launchpad.net oneiric Release                          
Err http://extras.ubuntu.com oneiric Release                                                
  
Err http://archive.canonical.com oneiric Release                                            
  
Ign http://ppa.launchpad.net oneiric Release                                                
Hit http://cy.archive.ubuntu.com oneiric-updates Release                                    
Hit http://cy.archive.ubuntu.com oneiric-backports Release           
Hit http://ppa.launchpad.net oneiric Release                                                
Hit http://ppa.launchpad.net oneiric Release                                                
Hit http://security.ubuntu.com oneiric-security/main Sources                                
Hit http://cy.archive.ubuntu.com oneiric/main Sources                                       
Hit http://cy.archive.ubuntu.com oneiric/restricted Sources          
Hit http://cy.archive.ubuntu.com oneiric/universe Sources
Hit http://cy.archive.ubuntu.com oneiric/multiverse Sources          
Hit http://cy.archive.ubuntu.com oneiric/main i386 Packages          
Hit http://cy.archive.ubuntu.com oneiric/restricted i386 Packages    
Hit http://cy.archive.ubuntu.com oneiric/universe i386 Packages      
Hit http://cy.archive.ubuntu.com oneiric/multiverse i386 Packages    
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex          
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/restricted Sources   
Hit http://security.ubuntu.com oneiric-security/universe Sources     
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://cy.archive.ubuntu.com oneiric/main TranslationIndex       
Hit http://cy.archive.ubuntu.com oneiric/multiverse TranslationIndex 
Hit http://cy.archive.ubuntu.com oneiric/restricted TranslationIndex 
Hit http://cy.archive.ubuntu.com oneiric/universe TranslationIndex   
Hit http://cy.archive.ubuntu.com oneiric-updates/main Sources
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://cy.archive.ubuntu.com oneiric-updates/universe Sources    
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://cy.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Hit http://security.ubuntu.com oneiric-security/main Translation-en  
Hit http://cy.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/main Sources
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://cy.archive.ubuntu.com oneiric-backports/universe Sources  
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://cy.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://cy.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://cy.archive.ubuntu.com oneiric/main Translation-en
Hit http://cy.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://cy.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric/universe Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://cy.archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Fetched 586 B in 1s (448 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Oh sorry I forgot one argument, try:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo apt-get update
```

---

### Post by matt_symes on 2012-05-15
Hi

My post here may be redundant if the above steps work. 

However, if they do not work then try a new server.

Software center->edit->software sources->download from:

Pick a different server.

Sometimes the problem is with the repository server. In most cases it's local though.

Also you could clean out all the caches to remove the gpg files manually.

This is an old post but the principle is the same.

[http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/](http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/)

Also, are you behind a proxy ? If so, is this giving you a cached and out of date release.gpg file ?

Have you cleaned the proxy cache or have you considered using wget to get the release.gpg files directly and copying it manually ?

Like i said though, this post will be redundant if the above steps work :)

Kind regards

---

### Post by serhancan on 2012-05-15
> **Zvlwab said:**
> Oh sorry I forgot one argument, try:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo apt-get update
```

> **matt_symes said:**
> Hi

My post here may be redundant if the above steps work. 

However, if they do not work then try a new server.

Software center->edit->software sources->download from:

Pick a different server.

Sometimes the problem is with the repository server. In most cases it's local though.

Also you could clean out all the caches to remove the gpg files manually.

This is an old post but the principle is the same.

[http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/](http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/)

Also, are you behind a proxy ? If so, is this giving you a cached and out of date release.gpg file ?

Have you cleaned the proxy cache or have you considered using wget to get the release.gpg files directly and copying it manually ?

Like i said though, this post will be redundant if the above steps work :)

Kind regards

Thank you for your help. First I used ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo apt-get update
``` and then chose a different server, now I am able to update my system.

Best regards

---

