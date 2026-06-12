---
title: "Various newbie questions about Ubuntu"
date: 2012-05-13
forum: General Help
---

### Post by Serthing on 2012-05-13
Hello. I've been using Ubuntu 10.04 LTS for a couple of years and I have some questions about Ubuntu.    

1) For probably the past 6 months, there have been software in the Update Manager that says "You are about to install software that can't be authenticated!" and lists a bunch of software like: ifupdown, taskel, pciutils, libpci3, app-install-data, initramfs-tools, libnet-dbus-perl, libuuid-perl, libxml-parser-perl I have no clue what those are so I've just stopped updating Update Manager (besides the Important updates, which apparently is authenticated). So what are these and how do I get rid of it?    

2) My CD burner programs (Brasero, K3b) cannot recognize when I insert a blank CD. (Although I can insert used CDs and view its contents just fine) I Googled it and it says: [http://askubuntu.com/questions/1273/does-anyone-have-a-solution-to-10-04-lts-not-recognizing-blank-cd-dvds](http://askubuntu.com/questions/1273/does-anyone-have-a-solution-to-10-04-lts-not-recognizing-blank-cd-dvds) something about installing "linux" from the Synaptic. So I did it and nothing happened. They also said to install other things like linux-headers or something but I couldn't find it in the Synaptic.  Does anyone know how to fix this problem?  

3) Wine worked perfectly fine for me before. But just today I found out that it didn't work. When I right click a file and run it with Wine it just opens and then immediately closes. And when I run a program installed in Wine, it gives me an error: "There is no Windows program configured to open this type of file." The same exact programs worked fine before. I don't know what or when it happened. Does anyone know what happened or what I should do? 

4) Are all the programs in Synaptic or Ubuntu Software Center safe? I sometimes just randomly install things to try to fix problems. 

5) What are the updates in Update Manager?  

Thanks.

---

### Post by Vaphell on 2012-05-13
programs in official repositories are safe in a sense that they are not malicious but not always installing bunch of packages is beneficial - you can create additional conflicts that way if let's say few programs are meant to manage some resource exclusively and you install all of them. Such situations are rare but the fact of life is that tidy systems are easier to manage and bugs happen.
You can add other repositories provided by 3rd parties to the list. 3rd party repos rock (they allow you to be more current and/or install software not present in official repos) but it's a good idea to be cautious. Synaptic/software center don't discriminate against the repositories so once you allowed them to make changes to your system, they will make changes to your system.

If the packages exist in more than one repo, newest one (version string) will be used in case of installation/update. There is risk of instability if you add a repository that provides let's say some bleeding edge versions of core system parts and you update few of them, while the rest of system stays at the official version number.

Update manager shows you packages that you have installed already but according to package database there is a newer version in repositories than currently installed.

---

### Post by Serthing on 2012-05-22
Well, I just updated stuff and it seems Update manager stopped bother me. The WINE problem is still there, I tried uninstalling and reinstalling both 1.2 and 1.3 and it didn't work.  I read somewhere that changing the kernel will cause WINE to not work. (I installed "linux" from Synaptic which I think is a kernel) Meaning, I think by me installing "linux" from Synaptic caused my WINE to not work anymore. I uninstalled "linux" but WINE still didn't work. How do I go back to what I had before?

---

### Post by oldos2er on 2012-05-22
> **Serthing said:**
> 1) For probably the past 6 months, there have been software in the Update Manager that says "You are about to install software that can't be authenticated!" and lists a bunch of software like: ifupdown, taskel, pciutils, libpci3, app-install-data, initramfs-tools, libnet-dbus-perl, libuuid-perl, libxml-parser-perl I have no clue what those are so I've just stopped updating Update Manager (besides the Important updates, which apparently is authenticated). So what are these and how do I get rid of it?    


You may be missing a gpg key for one or more repositories. Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post the output here?

---

### Post by Serthing on 2012-05-22
> 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_US     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                       
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release.gpg                                 
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en_US              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                         
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                      
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [412kB]          
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
  404  Not Found
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [659kB]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages                      
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]             
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,855B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,259B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [122kB]          
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,775B]             
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,323B]   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [40.5kB]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [130kB]     
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,368B]  
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:26 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                            
Get:27 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,250B]                      
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]          
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]          
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [613kB]        
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,617B] 
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]  
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [221kB]         
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,537B]  
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [99.6kB]    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [269kB]    
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.3kB] 
Get:38 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,250B]                      
Get:39 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,250B]
Get:40 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,250B]
Fetched 13.8MB in 7min 39s (30.0kB/s)
W: Failed to fetch [http://ftp.de.debian.org/debian/dists/lenny/main/binary-i386/Packages.gz](http://ftp.de.debian.org/debian/dists/lenny/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
> 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                         
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/games Translation-en_US     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                      
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny/main Translation-en_US              
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release                                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [412kB]          
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
Ign [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Err [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny/main Packages                               
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [659kB]                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                             
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB]             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/games Packages                      
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,855B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,259B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [122kB]          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,323B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [40.5kB]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [130kB]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,368B]  
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,775B]             
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]          
Get:27 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                          
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]          
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [613kB]        
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,617B] 
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]  
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [221kB]         
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,537B]  
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [99.6kB]    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [269kB]    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.3kB] 
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:37 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get:38 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,250B]                      
Fetched 13.8MB in 5min 1s (45.8kB/s)                                           
W: Failed to fetch [http://ftp.de.debian.org/debian/dists/lenny/main/binary-i386/Packages.gz](http://ftp.de.debian.org/debian/dists/lenny/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
Also ran it a second time.
As for the WINE problem I'm having, I uninstalled and deleted the .wine from the home folder and then reinstalled. It still has the same error. Does anyone know what the default kernel is that I can install in Synaptic? Actually, I do faintly remember that when I marked "linux" for installation that there were a few more other things that got marked. Maybe those are what's causing WINE not to work? I don't remember what those other things are though. Is there a way I could check?

---

### Post by oldos2er on 2012-05-22
> W: Failed to fetch [http://ftp.de.debian.org/debian/dist...86/Packages.gz](http://ftp.de.debian.org/debian/dist...86/Packages.gz) 404 Not Found

You need to remove the above repository from your sources.list. Run ```
gksu software-properties-gtk
``` in a terminal. It's really a bad idea to mix repositories from different distros.

---

### Post by Baldrick_NZ on 2012-05-22
Also, with regard to wine, there latest version is 1.5, which I'm running here with no probs. 

[http://ubuntublog.org/install-latest-wine-release-1-5-2.htm](http://ubuntublog.org/install-latest-wine-release-1-5-2.htm), for more info.

This might help resolve your issues too. Note, after installing 1.5, you may also need to do a clean install of your windows app as well.

---

### Post by Serthing on 2012-05-23
Thanks. It worked I think. I removed the something called "Debian 5.0 'Lenny'  Officially supported" from the repository list. Then I looked at Update Manager and the things that caused problems are gone. I wonder how that got there? 

As for Wine, I went to:
> 
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)
and clicked on both 1.4 and 1.5 under "Installing Wine" but neither worked. 
1.4 said: "Package 'wine1.4' is virtual."
1.5 said: "Could not find package 'wine1.5'."

> 
@-desktop:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine1.5
@-desktop:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine1.4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine1.4 has no installation candidate




I have Wine in the repository list. I was just wondering but since 1.4 and 1.5 is out and I have Wine listed in the repository list, how come 1.4 and 1.5 aren't listed in the list of programs/packages in Synaptic? (I have refreshed the list) I'm really confused with that.
Anyways, what do you mean by "windows app"? How do I do a clean installation of it?

---

