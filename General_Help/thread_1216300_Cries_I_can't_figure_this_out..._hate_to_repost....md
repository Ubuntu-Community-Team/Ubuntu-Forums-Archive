---
title: "*Cries* I can't figure this out... hate to repost... but no one replies!"
date: 2009-07-18
forum: General Help
---

### Post by TheSmokingGNU on 2009-07-18
k, so here's the deal: I want to install qbittorrent on my 8.04 distro. I am having some difficulties... and they make no sense to me. this is what I get when I do a sudo apt-get update && sudo apt-get install qbittorrent, which by all accounts I've read should do it:

darren@darren-desktop:~$ sudo apt-get update && sudo apt-get install qbittorrent
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release.gpg                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages   
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Translation-en_US
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release              
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages             
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Sources              
Err [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages             
  404 Not Found
Err [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Sources              
  404 Not Found
W: Failed to fetch [http://hydr0g3n.free.fr/qbittorrent/hardy/./Packages.gz](http://hydr0g3n.free.fr/qbittorrent/hardy/./Packages.gz)  404 Not Found

W: Failed to fetch [http://hydr0g3n.free.fr/qbittorrent/hardy/./Sources.gz](http://hydr0g3n.free.fr/qbittorrent/hardy/./Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


any help at all?

---

### Post by kerry_s on 2009-07-18
like it says "404 Not Found".
on the site it says "qBittorrent is now available in official Ubuntu repositories since v9.04 "Jaunty""
( [http://qbittorrent.sourceforge.net/download.php](http://qbittorrent.sourceforge.net/download.php) )

and your using "8.04 hardy" , so either update or you can try & grab the debs from jaunty & hope it don't break you current install.

---

