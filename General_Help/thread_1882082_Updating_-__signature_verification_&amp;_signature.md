---
title: "Updating -  signature verification &amp; signatures invalid errors"
date: 2011-11-16
forum: General Help
---

### Post by DogMatix on 2011-11-16
I have been experiencing some problems during updating. When I run:

```
sudo apt-get update
```

I am returned:

```
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release.gpg                    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                     
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources/DiffIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages/DiffIndex              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                         
Get:3 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189 B]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources                 
Ign [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Sources                   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages/DiffIndex               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Sources   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main i386 Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_GB         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_GB             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_GB   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_GB     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en_GB
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en
Fetched 577 B in 2s (240 B/s)
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures were invalid: BADSIG A2019EA84E7532C8 Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)[/COLOR] 

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

I have tried the following fixes:

```
gpg --keyserver keyserver.ubuntu.com &#8211;recv 16126D3A3E5C1192
```

which returns:

```
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

So I then enter:
```
gpg --export --armor 3E5C1192 | sudo apt-key add -

```

which returns:

```
OK
```
I have tried this for several of the invalid signatures but the problems persist.

I have also tried:

```
sudo apt-get update && sudo apt-get install -f && sudo apt-get upgrade
```

which  returns:

```
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-backports InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Get:1 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.ubuntu.com oneiric-backports Release.gpg                    
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://extras.ubuntu.com oneiric Release                                   
Get:3 http://deb.opera.com stable Release.gpg [189 B]                          
Hit http://archive.ubuntu.com oneiric-backports Release                        
Hit http://archive.ubuntu.com oneiric-security Release                         
Ign http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex                    
Ign http://linux.dropbox.com oneiric InRelease                                 
Hit http://deb.opera.com stable Release                                        
Hit http://archive.ubuntu.com oneiric/main Sources                             
Err http://extras.ubuntu.com oneiric Release                                   
  
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Ign http://deb.opera.com stable Release                                        
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages       
Hit http://archive.ubuntu.com oneiric/universe i386 Packages         
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://linux.dropbox.com oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/main Sources                     
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources               
Hit http://archive.ubuntu.com oneiric-updates/universe Sources                 
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources               
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com oneiric-backports/main Sources                   
Hit http://archive.ubuntu.com oneiric-backports/restricted Sources             
Hit http://archive.ubuntu.com oneiric-backports/universe Sources               
Hit http://archive.ubuntu.com oneiric-backports/multiverse Sources             
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages             
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages         
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-security/main Sources                    
Hit http://archive.ubuntu.com oneiric-security/restricted Sources              
Hit http://archive.ubuntu.com oneiric-security/universe Sources                
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources              
Hit http://linux.dropbox.com oneiric Release                         
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex 
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex       
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB                   
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB             
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB             
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB               
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB          
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en  
Hit http://archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-backports/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en        
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Hit http://linux.dropbox.com oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://linux.dropbox.com oneiric/main TranslationIndex
Hit http://deb.opera.com stable/non-free i386 Packages
Ign http://deb.opera.com stable/non-free Translation-en_GB
Ign http://deb.opera.com stable/non-free Translation-en
Ign http://linux.dropbox.com oneiric/main Translation-en_GB
Ign http://linux.dropbox.com oneiric/main Translation-en
Fetched 577 B in 2s (212 B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://deb.opera.com stable Release: The following signatures were invalid: BADSIG A2019EA84E7532C8 Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Problems persist.

I have also tried changing the software sources download server and reinstalling ubuntu-extras-keyring in Synaptic Package Manager. Also, restoring default keys in the Software Sources 'Authentification' tab.


I have found similar fixes to the above on this forum but none have worked. Any assistance appreciated.

DM

**EDIT: ** Fix in Post #9

---

### Post by eyden on 2011-11-16
You may want to install launchpad-getkeys. I had the same problem minutes ago and it did fix the keys for me

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys
```

then :

```

sudo launchpad-getkeys
```

From : [http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

Eyden

---

### Post by DogMatix on 2011-11-17
Thanks Eyden. I have already tried that fix. It appears to work & claims all missing keys have been replaced. But upon running update. I get the same errors.

---

### Post by raja.genupula on 2011-11-17
hi do this 
```
sudo apt-get autoclean
```

```
sudo apt-get update
```

---

### Post by DogMatix on 2011-11-17
raja.genupula: Thanks. Good call but still didn't work.

Still getting:

```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: GPG error: http://deb.opera.com stable Release: The following signatures were invalid: BADSIG A2019EA84E7532C8 Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by raja.genupula on 2011-11-17
> **DogMatix said:**
> raja.genupula: Thanks. Good call but still didn't work.

Still getting:

```
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG B725097B3ACC3965 Launchpad lffl
W: GPG error: http://deb.opera.com stable Release: The following signatures were invalid: BADSIG A2019EA84E7532C8 Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

Hi man i am sure these two things gonna help you . 
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)

---

### Post by DogMatix on 2011-11-17
raja.genupula: First Link Method 1:

```
cd /var/lib/apt
```

returned no such directory.

First Link Method 2:

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

returned

sudo: aptitude: command not found

Link 2 is a fix I have already tried and it did not work.

Thanks for trying though.

---

### Post by raja.genupula on 2011-11-17
aptitude was not installed in your system.

```
sudo apt-get install aptitude
```

and try again.

& i feel surprise about the output of 
cd /var/lib/apt

if not use mkdir to create that and try again.

---

### Post by DogMatix on 2011-11-17
raja.genupula: Thank you. It is now fixed. I installed apptitude but that fix still had no effect. However when I came to mkdir /var/lib/apt it was already there. I guess I must have mistyped that line in the fix. Anyway, I completed the fix below and it seems to have worked I get no errors after sudo apt-get-update and update manager is showing system up to date.

```
$ sudo -i

# apt-get clean

# cd /var/lib/apt

# mv lists lists.old

# mkdir -p lists/partial

# apt-get clean

# apt-get update

```

ref: [link]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")

---

### Post by DarkBattM14 on 2012-08-24
> **eyden said:**
> You may want to install launchpad-getkeys. I had the same problem minutes ago and it did fix the keys for me

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys
```

then :

```

sudo launchpad-getkeys
```

From : [http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

Eyden


Thanks!!!! this was the only solution that help me to solve this issue...
;);););)

---

