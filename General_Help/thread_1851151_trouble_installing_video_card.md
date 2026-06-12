---
title: "trouble installing video card"
date: 2011-09-27
forum: General Help
---

### Post by cavyracer1 on 2011-09-27
i have a emachine t3638 and i cant seem to get the video card to install her is what my system has 

lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:02.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 
if u can help me figure out how to insall my video card that would be great THANKS

---

### Post by cavyracer1 on 2011-09-27
my games dont seem to want to start and the ones tat do have sound but a black screen can someone pls help me

---

### Post by papibe on 2011-09-27
From what I see, your computer hasn't recognized your card, and still using the integrated graphics.

My computer has an option on the BIOS, so I can explicitly switch between integrated graphics and a PCI cards. Try checking yours to see if it needs that setting.

Hope it helps,
Regards.

---

### Post by cavyracer1 on 2011-09-27
im using the integrated card thats the one i want to use but none of my 3d games or boxee is not working if tried a lot of things to get it working but it still wont work most of the games and boxee wont even start up and the ones that do have sound with a black screen

---

### Post by papibe on 2011-09-27
I see.

You may want to try what is suggested on this [thread]("http://ubuntuforums.org/showthread.php?t=1087742"), but my guess is that package is already installed.

As far as I know, intel integrated graphics of that generation won't give you much performance on games or 3D effects.

Nevertheless, you may going into the BIOS and try increasing the RAM dedicated to the graphics. 

Regards.

---

### Post by cavyracer1 on 2011-09-27
the thread did not work can u post it again thanks

---

### Post by papibe on 2011-09-27
:sad: Sorry about that.

It is fixed on original post.

---

### Post by cavyracer1 on 2011-09-27
this is what i get when i put in that command 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://apt.boxee.tv](http://apt.boxee.tv) lucid Release.gpg                                      
Ign [http://apt.boxee.tv/](http://apt.boxee.tv/) lucid/main Translation-en_US                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/glasen/intel-drive/ubuntu/](http://ppa.launchpad.net/glasen/intel-drive/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://apt.boxee.tv](http://apt.boxee.tv) lucid Release                                          
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,190B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://apt.boxee.tv](http://apt.boxee.tv) lucid/main Packages                                    
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) natty-getdeb Release.gpg                         
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) natty-getdeb/games Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.getdeb.net](http://archive.getdeb.net) natty-getdeb Release
Hit [http://archive.getdeb.net](http://archive.getdeb.net) natty-getdeb/games Packages
Fetched 2,735B in 1s (1,736B/s)
W: Failed to fetch [http://ppa.launchpad.net/glasen/intel-drive/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/glasen/intel-drive/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.



what should i do now

---

### Post by wildmanne39 on 2011-09-27
Never mind I do not think the fix was for that card but another intel.

---

### Post by cavyracer1 on 2011-09-28
what should i do now is there a way to put the settings back the way they were before i started  trying to get it to work because my boxee was working and now it wont

---

### Post by oldos2er on 2011-09-28
Are you running Natty or Lucid? You've got repositories for both distros in your sources.list, which is going to cause problems.

---

### Post by cavyracer1 on 2011-09-28
lucid

---

### Post by oldos2er on 2011-09-28
Then edit your sources.list and remove the Natty repositories, if you haven't already done so.

---

### Post by cavyracer1 on 2011-09-28
how do i do that

---

### Post by cavyracer1 on 2011-09-28
if i upgrade to 10.10 do u think that might fix my problems

---

### Post by oldos2er on 2011-09-29
```
gksu gedit /etc/apt/sources.list
``` Either delete or comment out (add a # at the start of the line) the Natty lines. When you're done, close the editor and run ```
sudo apt-get update
```

---

### Post by cavyracer1 on 2011-09-29
i did that and im still having issues

---

