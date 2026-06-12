---
title: "Update Manger Failed to Download repository information"
date: 2012-01-11
forum: General Help
---

### Post by latinlightning on 2012-01-11
Hello,

I noticed that my desktop computer had not been asking me to install any updates as of late on my Ubuntu 11.04. So I manually went to the Update Manager and clicked the check button but I get "Failed to Download repository information Check your Internet Connection" and under details it has the following:

W:Failed to fetch [http://ppa.launchpad.net/user/java/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/user/java/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/user/java/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/user/java/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I'm assuming something related to java?When I try apt-get update I get the following:

[PHP]Ign http://ppa.launchpad.net natty InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://security.ubuntu.com natty-security InRelease              
Ign http://extras.ubuntu.com natty InRelease                         
Ign http://us.archive.ubuntu.com natty InRelease                     
Ign http://us.archive.ubuntu.com natty-updates InRelease             
Hit http://ppa.launchpad.net natty Release.gpg                       
Hit http://security.ubuntu.com natty-security Release.gpg            
Hit http://extras.ubuntu.com natty Release.gpg                       
Hit http://us.archive.ubuntu.com natty Release.gpg                   
Ign http://ppa.launchpad.net natty Release.gpg                       
Hit http://security.ubuntu.com natty-security Release                
Hit http://extras.ubuntu.com natty Release                           
Hit http://us.archive.ubuntu.com natty-updates Release.gpg            
Hit http://ppa.launchpad.net natty Release                                     
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://extras.ubuntu.com natty/main Sources                                
Ign http://ppa.launchpad.net natty Release                           
Hit http://us.archive.ubuntu.com natty-updates Release               
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main i386 Packages               
Hit http://security.ubuntu.com natty-security/restricted i386 Packages         
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Hit http://us.archive.ubuntu.com natty/main Sources                  
Hit http://us.archive.ubuntu.com natty/restricted Sources            
Hit http://us.archive.ubuntu.com natty/universe Sources              
Hit http://us.archive.ubuntu.com natty/multiverse Sources            
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://security.ubuntu.com natty-security/universe i386 Packages           
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages         
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages        
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com natty/main TranslationIndex         
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Ign http://extras.ubuntu.com natty/main Translation-en                         
Err http://ppa.launchpad.net natty/main i386 Packages                          
  404  Not Found
Ign http://security.ubuntu.com natty-security/main Translation-en_US 
Ign http://security.ubuntu.com natty-security/main Translation-en    
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en               
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
W: Failed to fetch http://ppa.launchpad.net/user/java/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/user/java/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/PHP] My Internet connection works fine so I know that shouldn't be a problem. Any help is appreciated!

---

### Post by latinlightning on 2012-01-12
Any suggestions? Because of this I haven't been able to update my system for 41 days :(

---

### Post by westie457 on 2012-01-12
Hi, welcome to the Forum.

In 'Update Manager' go to Settings and in the 'Other Software' tab uncheck the two ppa's. Close the window and wait for update manager to reload the sources file, then try updating.

Hope this helps

---

### Post by latinlightning on 2012-01-12
It worked! Thank you so much!!

Any way to fix the Java though? :D

---

### Post by raja.genupula on 2012-01-12
Actually those things are occur if those things  re not available but some times with update server issues also.

+1 to the answer , but before try that change your server from update manager settings and then try again.
If problem still exists then do as he said .

---

### Post by grahammechanical on 2012-01-12
You might want to read this page:

[https://wiki.ubuntu.com/JavaTeam]("https://wiki.ubuntu.com/JavaTeam")

I read somewhere that because of Oracle's removal of the license agreement, Canonical will use updates to remove Oracle Java from pre-11.10 Ubuntu installs.

And another link

[http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/]("http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/")

I think this explains it all.

Regards

---

