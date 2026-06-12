---
title: "Trying to install qBitTorrent in 8.04... help?"
date: 2009-07-18
forum: General Help
---

### Post by TheSmokingGNU on 2009-07-18
just having a hard time understanding the line starting with gpg, the one after Packages are signed...

[http://www.ubuntugeek.com/howto-install-qbittorrent-in-ubuntu-gutsy.html](http://www.ubuntugeek.com/howto-install-qbittorrent-in-ubuntu-gutsy.html)

just trying to understand what I actually type, sorry, linux noob. thanks in advance! you guys are great!

---

### Post by TheSmokingGNU on 2009-07-18
hate to cheaply bump my thread, but... seriously, anyone?

---

### Post by TheSmokingGNU on 2009-07-18
okay, so my problem is kinda in the same thread as this, but this was locked:

[http://ubuntuforums.org/showthread.php?t=424079](http://ubuntuforums.org/showthread.php?t=424079)

so here is what I get when I try to:

sudo apt-get update && sudo apt-get install qbittorrent

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


any ideas? I just need to make a torrent file... didn't think it'd be this difficult. :)

---

### Post by michael37 on 2009-12-20
just for the record, the correct apt line is

deb [http://hydr0g3n.free.fr/ubuntu/](http://hydr0g3n.free.fr/ubuntu/) hardy main
deb-src [http://hydr0g3n.free.fr/ubuntu/](http://hydr0g3n.free.fr/ubuntu/) hardy main

for 8.04.

Use [qbittorrent ppa]("https://launchpad.net/~hydr0g3n/+archive/ppa") for Jaunty and Karmic.

---

