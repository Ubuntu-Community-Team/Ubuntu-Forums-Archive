---
title: "Error performing update"
date: 2011-11-17
forum: General Help
---

### Post by ewaynec on 2011-11-17
I have Ubuntu 10.04 and every time I do an update, (the last three) I get this error.
  (The screen shots are sent as an attachment)
I have checked the repositories and everything seems to be OK. The information in the error box is of no use because I do not understand what it is telling me. If you know please help me.

---

### Post by BillyBoa on 2011-11-17
I can't see very well the names of the repositories but you have a conflict.

You have to uncheck the problematic repo.

Open the Update Manager and down to the left it's the button Settings.

From there go to the tab Other Software and uncheck the PPA with the problem. 

Then close and update.

---

### Post by BillyBoa on 2011-11-17
Ok I download the photo and read the lines.

You have duplicate PPAs.

Follow my instructions above, find which repositories are duplicate and uncheck them.

---

### Post by ewaynec on 2011-11-17
Thank you Billy Boa for the quick reply. When I read it I thought "of course, thats it" but I tried as you said, and found 2 duplicates. I unchecked them and ran the update again, and got the same errors again.[ATTACH]207425[/ATTACH]

[ATTACH]207426[/ATTACH]

[ATTACH]207427[/ATTACH]
  It gave me the option to partially upgrade, I did that and got the last error.

---

### Post by hydrox24 on 2011-11-17
Hi ewaynec,
I hope that you don't have too much of an issue with the command line, because after unchecking those repositories and closing the update manager you need to run the command ```
sudo apt-get update
``` In the terminal (Applications>Accessories>terminal) and lots of lines should scroll past quickly. when that command is done, simply close the terminal window and start-up the update manager again, after doing this the problem should be fixed.

---

### Post by ewaynec on 2011-11-18
I did what you said from the terminal, then ran the update manager, and got the same error. (The last screen shot about the partial upgrade) I ran the partial upgrade, and got the error "uncalculable"...
  I have not seen a problem this is creating, but there is a lot going on that I don't see. I want to get it fixed mainly because I do not know what it is. I hate to say this but I am completely lost on this one.

---

### Post by raja.genupula on 2011-11-18
Man no you shouldn't go for partial upgrades , they will move your system to unstable state . 

one small suggestion if you dont mind , we can make a quicker look at text than images , so better to paste the output , dont attach images here .


so please provide us ```
sudo apt-get update
``` 
from the terminal and post the output here with # tags on starting and ending of output. 

Thank you

---

### Post by ewaynec on 2011-11-18
When using the package manager, the output IS an image.
here is the output for sudo apt-get update

wayne@wayne-desktop:~$ sudo apt-get update
[sudo] password for wayne: 
Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Release Candidate i386 (20100419.1)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 _Lucid Lynx_ - Release Candidate i386 (20100419.1)/ lucid/restricted Translation-en_US
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_US              
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Sources                                
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Sources                                
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,220B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Sources                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:6 [http://dl.google.com](http://dl.google.com) stable/main Packages [777B]                         
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_US              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Ign [http://ppa.launchpad.net/qwibber-daily/ppa/ubuntu/](http://ppa.launchpad.net/qwibber-daily/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://ppa.launchpad.net/ssakar/ppa/ubuntu/](http://ppa.launchpad.net/ssakar/ppa/ubuntu/) lucid/main Translation-en_US   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty Release.gpg                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) jaunty/main Translation-en_US         
Ign [http://cz.archive.ubuntu.com/ubuntu/](http://cz.archive.ubuntu.com/ubuntu/) jaunty/universe Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                             
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages                
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages                  
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages                
Ign [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources                       
Err [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty/main Packages                          
  404  Not Found [IP: 91.189.92.180 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources                 
Err [http://cz.archive.ubuntu.com](http://cz.archive.ubuntu.com) jaunty/universe Packages                      
  404  Not Found [IP: 91.189.92.180 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Sources                        
Fetched 5,087B in 8s (597B/s)                                                  
W: Failed to fetch [http://ppa.launchpad.net/qwibber-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/qwibber-daily/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://cz.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.gz](http://cz.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

W: Failed to fetch [http://cz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.gz](http://cz.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.180 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
wayne@wayne-desktop:~$

---

### Post by ewaynec on 2011-11-18
I was reading on this forum, trying to find a similar problem with a solution, and I found this. It may not be a solution to my problem (the problem is slightly different and another version OS) but it may provide a hint. The solution begins at message 44.

[http://ubuntuforums.org/showthread.php?t=1791867&highlight=run+monitors+splitter+cable&page=3](http://ubuntuforums.org/showthread.php?t=1791867&highlight=run+monitors+splitter+cable&page=3)

---

### Post by raja.genupula on 2011-11-18
Hi man actually the problem is temporary server downs , do this then it will be fine .

goto update manager -> settings -> 1st tab at download from change your server to main server or best server for your location and then try again.

---

### Post by ewaynec on 2011-11-19
It was set to "custom server", I changed it to "Main server" with no difference. It still gives me the option to do a partial upgrade. (I closed it) I downloaded the updates from terminal and tried again, same error.

---

### Post by ewaynec on 2011-11-24
It's OK I don't have any idea either.

---

### Post by raja.genupula on 2011-11-24
hi man , hope you're doing good.

[http://ubuntuforums.org/showthread.php?t=1876836&page=3](http://ubuntuforums.org/showthread.php?t=1876836&page=3)

this helped me.

Hope it will be fine for you.

---

### Post by ewaynec on 2011-11-24
If I understand what I read in the thread you suggested, I would screw up my system if I followed the instructions given. I am using 10.04.

  I know what is happening, the update is looking for files in repositories that I don't have listed as software sources. It tells me the sources I need, but if I try to install the sources as it list them I get an error (404), if I try to go to the web page it list, I get the 404 error.
  I did not change anything to cause this. Everything was running so well I was afraid to change anything then about a month ago I did an update and got the errors listed above.

---

### Post by raja.genupula on 2011-11-24
My OS is  12.04 , i mean that thread.

---

### Post by ewaynec on 2011-12-11
Well OK, I guess this will go into the "unsolvable" section.

---

### Post by matt_symes on 2011-12-11
Hi

Unsolveable ? No. You using Jaunty repositories for some of your PPA's. Remove them.

> Err [http://cz.archive.ubuntu.com]("http://cz.archive.ubuntu.com/") **jaunty**/main Packages                          
  404  Not Found [IP: 91.189.92.180 80]

Kind regards

---

