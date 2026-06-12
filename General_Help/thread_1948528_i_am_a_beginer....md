---
title: "i am a beginer..."
date: 2012-03-28
forum: General Help
---

### Post by ramanathan on 2012-03-28
root@rajesh-HP-G62-Notebook-PC:/home/rajesh# apt-get install;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@rajesh-HP-G62-Notebook-PC:/home/rajesh# 






i last update more than 281 days.now i can't update my os.........

---

### Post by whatthefunk on 2012-03-28
> **ramanathan said:**
> root@rajesh-HP-G62-Notebook-PC:/home/rajesh# apt-get install;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@rajesh-HP-G62-Notebook-PC:/home/rajesh# 






i last update more than 281 days.now i can't update my os.........

Try this:

```
sudo apt-get update
```

Then...

```
sudo apt-get upgrade
```

You were using "apt-get install" which is for installing, not updating.

---

### Post by WasMeHere on 2012-03-28
Hi ramanathan,

Try the following commands
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
and check the output to the terminal screen.

Good luck :-)
Olle

---

### Post by ramanathan on 2012-03-28
> **Olle Wiklund said:**
> Hi ramanathan,

Try the following commands
```
sudo apt-get update
``````
sudo apt-get upgrade
```and check the output to the terminal screen.

Good luck :-)
Olle

```
root@rajesh-HP-G62-Notebook-PC:/home/rajesh# sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty InRelease                             
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                             
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                 
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release.gpg                           
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources/DiffIndex         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources/DiffIndex                  
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release.gpg                   
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources/DiffIndex   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages/DiffIndex                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources/DiffIndex       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty Release                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources/DiffIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates Release                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages/DiffIndex     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Sources/DiffIndex              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Sources/DiffIndex            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Sources/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Sources/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main i386 Packages/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted i386 Packages/DiffIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse i386 Packages/DiffIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted TranslationIndex       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe TranslationIndex               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Sources/DiffIndex          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Sources/DiffIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Sources/DiffIndex    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                          
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main i386 Packages/DiffIndex    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted i386 Packages/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_IN                      
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe i386 Packages/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main TranslationIndex         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse TranslationIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted TranslationIndex   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe TranslationIndex     
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources               
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages             
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages         
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages       
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_IN         
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en            
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_IN   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_IN   
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_IN     
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en        
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Sources                          
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/main Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/multiverse Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/restricted Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty/universe Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Sources
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse i386 Packages
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/main Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/multiverse Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/restricted Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en_IN
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) natty-updates/universe Translation-en
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/main/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/source/Sources)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/multiverse/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_IN](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/natty-security/universe/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/source/Sources)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/binary-i386/Packages)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/main/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/multiverse/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en_IN)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en](http://in.archive.ubuntu.com/ubuntu/dists/natty-updates/universe/i18n/Translation-en)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
root@rajesh-HP-G62-Notebook-PC:/home/rajesh#
```

---

### Post by whatthefunk on 2012-03-28
Next, you need to run the "sudo apt-get upgrade" command.

---

### Post by ramanathan on 2012-03-28
> **whatthefunk said:**
> Next, you need to run the "sudo apt-get upgrade" command.

root@rajesh-HP-G62-Notebook-PC:/home/rajesh# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@rajesh-HP-G62-Notebook-PC:/home/rajesh#

---

### Post by WasMeHere on 2012-03-28
First try to repeat those two command lines in cycles, the result may improve, stepwise. If not you need some stonger remedy. Maybe you can use the GUI ***Synaptic*** and try to add some more program sources, and then try again with update and upgrade. Maybe you can also try
```
sudo apt-get check
```
```
sudo apt-get autoclean
```
```
sudo apt-get autoremove
```
Read ```
man apt-get
``` to learn more about these commands

---

### Post by ramanathan on 2012-03-28
> **Olle Wiklund said:**
> First try to repeat those two command lines in cycles, the result may improve, stepwise. If not you need some stonger remedy. Maybe you can use the GUI ***Synaptic*** and try to add some more program sources, and then try again with update and upgrade. Maybe you can also try
```
sudo apt-get check
``````
sudo apt-get autoclean
``````
sudo apt-get autoremove
```Read ```
man apt-get
``` to learn more about these commands


rajesh@rajesh-HP-G62-Notebook-PC:~$ sudo apt-get check
[sudo] password for rajesh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rajesh@rajesh-HP-G62-Notebook-PC:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rajesh@rajesh-HP-G62-Notebook-PC:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rajesh@rajesh-HP-G62-Notebook-PC:~$

---

### Post by WasMeHere on 2012-03-28
I seems a bit difficult...

Did you use the GUI Synaptic and try to add some more program sources? Or do the updating and upgrading that way to see if you get some more information?

---

### Post by WasMeHere on 2012-03-28
Another tip: Maybe you can try to fetch your updates from another server. In Synaptic: 'Fetch from'

---

### Post by mal1958 on 2012-03-28
It might also help us to know what your system has (chipset, memory, cards, and the like) what flavor of Ubuntu you are using (Ubuntu, lubuntu, kubuntu, xubuntu, mint, etc)  and it's version (10.04, 10.10, 11.04, 11.10)  This may help us find what repository may help you..  I agree though that Synaptic may help but at the same time if you go to Update manager, that may help too.

NOTE: If you are using the gnome interface you will find both Synaptic and Update manager in the System/Admin section.  Try both.  That is the beauty of this system.  More powerful then windoze but can be just as simple too.

---

