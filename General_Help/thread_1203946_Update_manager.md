---
title: "Update manager"
date: 2009-07-04
forum: General Help
---

### Post by DeMus on 2009-07-04
Hi,
Just now the update manager was started to inform me about some updates. Three of those updates are for the "new" kernel 2.6.28.13. Since I have installed 2.6.28.11 and 2.6.28.12 but also 2.6.30. I don't need and don't want to update to the 28.13 version. This is a step backwards.

How can I get rid of those updates being mentioned every time the update manager starts? Now I have to unclick them to not install them. This should be done easier, right? But how?

---

### Post by tommcd on 2009-07-04
How did you install 2.6.30? This is not currently in the Jaunty repos. Did you compile it yourself?

---

### Post by DeMus on 2009-07-04
> **tommcd said:**
> How did you install 2.6.30? This is not currently in the Jaunty repos. Did you compile it yourself?

I found it here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

It works great.

---

### Post by tommcd on 2009-07-04
See this tutorial from Ubuntu Geek for how to hold packages:
[http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html](http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html)
Just out of curiosity, why did you install the 2.6.30 kernel? Was it just because you wanted to use the latest (and hopefully greatest) kernel? Or did you need the newer kernel for some specific reason?

---

### Post by DeMus on 2009-07-04
> **tommcd said:**
> See this tutorial from Ubuntu Geek for how to hold packages:
[http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html](http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html)
Just out of curiosity, why did you install the 2.6.30 kernel? Was it just because you wanted to use the latest (and hopefully greatest) kernel? Or did you need the newer kernel for some specific reason?

With all three 2.6.28 versions (11 , 12 and 13) I had problems with one program. So I tried the 2.6.30 version and the problem is gone.
The program I use is Boinc, a program initiated by the Berkeley university in California. One project in this program is called Seti@home (Search for Extra Terrestrial Intelligence @ home).
An application is running on your home computer and receives packages of data from the main server. These packages have to be "crunched" (investigated) and the results are send back.
Now that I use 2.6.30 on Jaunty I no longer get the computation errors which I did get with 2.6.28.x

---

### Post by DeMus on 2009-07-04
> **tommcd said:**
> See this tutorial from Ubuntu Geek for how to hold packages:
[http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html](http://www.ubuntugeek.com/how-to-prevent-a-package-from-being-updated-in-ubuntu.html)
Just out of curiosity, why did you install the 2.6.30 kernel? Was it just because you wanted to use the latest (and hopefully greatest) kernel? Or did you need the newer kernel for some specific reason?

I tried your link, but this does not work for me. I must have typed something wrong. Any idea what is the correct syntax I have to us to stop the 3 kernel updates as mentioned in the picture?
I used:
sudo aptitude hold linux-headers-2.6.28-13 linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic

Thanks for your help.

---

### Post by tommcd on 2009-07-04
> **DeMus said:**
> I tried your link, but this does not work for me. I must have typed something wrong. Any idea what is the correct syntax I have to us to stop the 3 kernel updates as mentioned in the picture?
I used:
sudo aptitude hold linux-headers-2.6.28-13 linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic

Can you post the errors you get when you run that command?

Try running:
```
aptitude search linux-image
```
and:
```
aptitude search linux-headers
```
This will list all of the linux-image and linux-headers packages in the repos. Use the output of those commands to get the exact names of the 2.6.28 image and headers packages that you want to hold. Then run (as an example):
```
sudo aptitude hold linux-image-2.6.28-13-generic
```
to hold the linux-image-2.6.28-13-generic package.
Then don't forget to run:
```
sudo apt-get update
```
after you hold all the packages you don't want.

---

### Post by DeMus on 2009-07-04
Well, I did exactly as you wrote down, but the 3 items keep appearing in the update manager when I start it after having done all the steps.
Any idea what I am doing wrong here?

---

### Post by tommcd on 2009-07-04
It seems this problem with holding packages with aptitude has been reported before, going back to Ubuntu Feisty:
[http://ubuntuforums.org/showthread.php?t=539305](http://ubuntuforums.org/showthread.php?t=539305)
As long as you are running the commands correctly, then you are probably not doing anything wrong. I can't tell unless you post the commands you ran, along with the terminal output from those commands.

Try using the **dpkg --set-selections** method as in the first part of the Ubuntu Geek tutorial I linked to earlier. That was reported as working in the thread I linked to above in this post.

---

### Post by DeMus on 2009-07-04
> **tommcd said:**
> It seems this problem with holding packages with aptitude has been reported before, going back to Ubuntu Feisty:
[http://ubuntuforums.org/showthread.php?t=539305](http://ubuntuforums.org/showthread.php?t=539305)
As long as you are running the commands correctly, then you are probably not doing anything wrong. I can't tell unless you post the commands you ran, along with the terminal output from those commands.

Try using the **dpkg --set-selections** method as in the first part of the Ubuntu Geek tutorial I linked to earlier. That was reported as working in the thread I linked to above in this post.

Okay, here goes:

jan@2-Quad:~$ aptitude search linux-imagep   linux-image                       - Generic Linux kernel image.                
v   linux-image-2.6                   -                                            
i   linux-image-2.6.28-11-generic     - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-11-server      - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-11-virtual     - Linux kernel image for version 2.6.28 on x8
i   linux-image-2.6.28-12-generic     - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-12-server      - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-12-virtual     - Linux kernel image for version 2.6.28 on x8
ih  linux-image-2.6.28-13-generic     - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-13-server      - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-13-virtual     - Linux kernel image for version 2.6.28 on x8
p   linux-image-2.6.28-3-rt           - Linux kernel image for version 2.6.28 on In
i   linux-image-2.6.30-020630-generic - Linux kernel image for version 2.6.30 on x8
i   linux-image-generic               - Generic Linux kernel image                 
p   linux-image-rt                    - Rt Linux kernel image                      
p   linux-image-server                - Linux kernel image on Server Equipment.    
p   linux-image-virtual               - Linux kernel image for virtual machines 
   
jan@2-Quad:~$ sudo aptitude hold linux-image-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jan@2-Quad:~$ sudo aptitude hold linux-image-2.6.28-13-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

jan@2-Quad:~$ sudo aptitude hold linux-image-2.6.28-13-virtual
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jan@2-Quad:~$ aptitude search linux-headers
v   linux-headers                     -                                            
v   linux-headers-2.6                 -                                            
i A linux-headers-2.6.28-11           - Header files related to Linux kernel versio
i A linux-headers-2.6.28-11-generic   - Linux kernel headers for version 2.6.28 on 
p   linux-headers-2.6.28-11-server    - Linux kernel headers for version 2.6.28 on 
i A linux-headers-2.6.28-12           - Header files related to Linux kernel versio
i A linux-headers-2.6.28-12-generic   - Linux kernel headers for version 2.6.28 on 
p   linux-headers-2.6.28-12-server    - Linux kernel headers for version 2.6.28 on 
ih  linux-headers-2.6.28-13           - Header files related to Linux kernel versio
ih  linux-headers-2.6.28-13-generic   - Linux kernel headers for version 2.6.28 on 
p   linux-headers-2.6.28-13-server    - Linux kernel headers for version 2.6.28 on 
p   linux-headers-2.6.28-3-rt         - Linux kernel headers for version 2.6.28 on 
i   linux-headers-2.6.30-020630       - Header files related to Linux kernel versio
i   linux-headers-2.6.30-020630-gener - Linux kernel headers for version 2.6.30 on 
i   linux-headers-generic             - Generic Linux kernel headers               
v   linux-headers-lbm                 -                                            
v   linux-headers-lbm-2.6             -                                            
p   linux-headers-lbm-2.6.28-11-gener - Header files related to linux-backports-mod
p   linux-headers-lbm-2.6.28-11-serve - Header files related to linux-backports-mod
p   linux-headers-lbm-2.6.28-12-gener - Header files related to linux-backports-mod
p   linux-headers-lbm-2.6.28-12-serve - Header files related to linux-backports-mod
p   linux-headers-lbm-2.6.28-13-gener - Header files related to linux-backports-mod
p   linux-headers-lbm-2.6.28-13-serve - Header files related to linux-backports-mod
p   linux-headers-rt                  - Rt Linux kernel headers                    
p   linux-headers-server              - Linux kernel headers on Server Equipment.  
p   linux-headers-virtual             - Linux kernel headers for virtual machines  
jan@2-Quad:~$ sudo aptitude hold linux-headers-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jan@2-Quad:~$ sudo aptitude hold linux-headers-2.6.28-13-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jan@2-Quad:~$ sudo aptitude hold linux-headers-lbm-2.6.28-13-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

jan@2-Quad:~$ sudo aptitude hold linux-headers-lbm-2.6.28-13-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

jan@2-Quad:~$ sudo apt-get update
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release.gpg
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Translation-en_US                    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Translation-en_US              
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Translation-en_US                
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Translation-en_US              
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates Release.gpg                       
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Translation-en_US            
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US      
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release.gpg                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_US                 
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Translation-en_US        
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US      
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed Release.gpg                      
Hit [http://www.ftd4linux.nl](http://www.ftd4linux.nl) jaunty Release.gpg                                    
Ign [http://www.ftd4linux.nl](http://www.ftd4linux.nl) jaunty/main Translation-en_US                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                               
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US       
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US     
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/main Translation-en_US           
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                   
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US     
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/universe Translation-en_US       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US       
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/main Translation-en_US          
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US    
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/universe Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US               
Hit [http://www.ftd4linux.nl](http://www.ftd4linux.nl) jaunty Release                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty Release                                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                            
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                        
Ign [http://www.ftd4linux.nl](http://www.ftd4linux.nl) jaunty/main Packages                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                                  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed Release                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                       
Hit [http://www.ftd4linux.nl](http://www.ftd4linux.nl) jaunty/main Packages                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                          
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                       
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Packages                             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Packages                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/main Sources                              
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Packages                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/universe Sources                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Packages                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty/multiverse Sources                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Packages                     
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Packages               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/restricted Sources                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Packages                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/universe Sources                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Packages               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-updates/multiverse Sources                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/restricted Packages              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/main Packages                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/multiverse Packages              
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-proposed/universe Packages                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/restricted Packages             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/multiverse Packages             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) jaunty-backports/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources                                  
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Sources
Reading package lists... Done
jan@2-Quad:~$

---

### Post by tommcd on 2009-07-04
I don't see any errors or problems in the output you posted.
 I can't test using aptitude to hold packages on my system right now since my system is currently up to date.

I don't know why using aptitude to hold packages is not working. This has been reported before, as in the thread I linked to in my last post.
 This is supposed to work, at least in Debian anyway. The Ubuntu devs patch and 'Ubuntu-ize' the Debian packages that are used in Ubuntu, so perhaps something is lost along the way.

Try using the **dpkg --set-selections** method in the Ubuntu Geek tutorial.

You have quite a bit of stuff in your sources.list! This is not the problem though, at least in this case.

---

