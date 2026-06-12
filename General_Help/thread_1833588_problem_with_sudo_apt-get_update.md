---
title: "problem with sudo apt-get update"
date: 2011-08-26
forum: General Help
---

### Post by kaidnz on 2011-08-26
Hello

I'm new to Linux and I just installed ubuntu 11.04. I'm having  problem with "sudo apt-get update", this is the output:

[PHP] 
Ign http://archive.canonical.com natty InRelease                               
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://packages.medibuntu.org natty InRelease                              
Ign http://archive.ubuntu.com natty InRelease                        
Ign http://archive.ubuntu.com natty-updates InRelease                
Ign http://extras.ubuntu.com natty InRelease                         
Ign http://archive.ubuntu.com natty-security InRelease                  
Ign http://archive.ubuntu.com natty-proposed InRelease                  
Hit http://archive.canonical.com natty Release                                 
Ign http://archive.ubuntu.com natty-backports InRelease                        
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://archive.ubuntu.com natty Release.gpg                       
Hit http://packages.medibuntu.org natty/free amd64 Packages           
Hit http://archive.ubuntu.com natty-updates Release.gpg               
Hit http://archive.ubuntu.com natty-security Release.gpg             
Hit http://archive.ubuntu.com natty-proposed Release.gpg                       
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com natty/partner Sources               
Hit http://packages.medibuntu.org natty/non-free amd64 Packages       
Hit http://archive.ubuntu.com natty-backports Release.gpg             
Hit http://archive.ubuntu.com natty Release                                    
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Hit http://archive.ubuntu.com natty-updates Release                            
Hit http://archive.ubuntu.com natty-security Release                           
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Hit http://extras.ubuntu.com natty/main Sources                                
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Hit http://archive.ubuntu.com natty-proposed Release                           
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://archive.ubuntu.com natty-backports Release                          
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Hit http://archive.ubuntu.com natty/main Sources                               
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://archive.ubuntu.com natty/multiverse Sources                         
Hit http://archive.ubuntu.com natty/universe Sources                           
Hit http://archive.ubuntu.com natty/main amd64 Packages                        
Hit http://archive.ubuntu.com natty/restricted amd64 Packages                  
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages                  
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://archive.ubuntu.com natty-updates/restricted Sources       
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                 
Hit http://archive.ubuntu.com natty-updates/universe Sources                   
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages                
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages          
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages            
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages          
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty-security/restricted Sources      
Hit http://archive.ubuntu.com natty-security/main Sources                      
Hit http://archive.ubuntu.com natty-security/multiverse Sources                
Hit http://archive.ubuntu.com natty-security/universe Sources                  
Hit http://archive.ubuntu.com natty-security/main amd64 Packages               
Hit http://archive.ubuntu.com natty-security/restricted amd64 Packages         
Hit http://archive.ubuntu.com natty-security/universe amd64 Packages           
Hit http://archive.ubuntu.com natty-security/multiverse amd64 Packages         
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.ubuntu.com natty-security/main TranslationIndex   
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Ign http://extras.ubuntu.com natty/main Translation-en                         
Hit http://archive.ubuntu.com natty-proposed/restricted Sources      
Hit http://archive.ubuntu.com natty-proposed/main Sources
Hit http://archive.ubuntu.com natty-proposed/multiverse Sources
Hit http://archive.ubuntu.com natty-proposed/universe Sources                  
Hit http://archive.ubuntu.com natty-proposed/restricted amd64 Packages         
Hit http://archive.ubuntu.com natty-proposed/main amd64 Packages               
Hit http://archive.ubuntu.com natty-proposed/multiverse amd64 Packages         
Hit http://archive.ubuntu.com natty-proposed/universe amd64 Packages
Ign http://archive.ubuntu.com natty-proposed/main TranslationIndex
Ign http://archive.ubuntu.com natty-proposed/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-proposed/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-proposed/universe TranslationIndex
Hit http://archive.ubuntu.com natty-backports/restricted Sources               
Hit http://archive.ubuntu.com natty-backports/main Sources                     
Hit http://archive.ubuntu.com natty-backports/multiverse Sources               
Hit http://archive.ubuntu.com natty-backports/universe Sources                 
Hit http://archive.ubuntu.com natty-backports/restricted amd64 Packages        
Hit http://archive.ubuntu.com natty-backports/main amd64 Packages
Hit http://archive.ubuntu.com natty-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com natty-backports/universe amd64 Packages
Ign http://archive.ubuntu.com natty-backports/main TranslationIndex            
Ign http://archive.ubuntu.com natty-backports/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty-backports/universe TranslationIndex        
Get:1 http://archive.ubuntu.com natty/universe amd64 Packages [7,733 kB]       
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/main Translation-en
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en
Ign http://archive.ubuntu.com natty-backports/main Translation-en_US
Ign http://archive.ubuntu.com natty-backports/main Translation-en
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-backports/multiverse Translation-en
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-backports/restricted Translation-en
Ign http://archive.ubuntu.com natty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com natty-backports/universe Translation-en
Fetched 1 B in 59s (0 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

[/PHP]
why I'm getting this:

[PHP]
W: Failed to fetch  gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages   Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/PHP]how can i solve it?

Thank you

---

### Post by Beacon11 on 2011-08-26
Try changing your mirror. To change that, open up Synaptic Package Manager, hit Settings > Repositories. In the Ubuntu Software tab, change the Download From drop-down to Other, which will cause another window to pop up. In the new window, hit Select Best Server. This will select the one to which you have the fastest connection, and it hopefully won't have that issue.

---

### Post by kaidnz on 2011-08-27
thanks for your replies.

I did what Beacon11 said and after i reload i got this message

[IMG]http://i53.tinypic.com/2lw198n.png[/IMG]

what should i do?

---

### Post by raja.genupula on 2011-08-27
open update manager --> settings and then other software uncheck error link in the list and try again .

---

