---
title: "Kernel errors present"
date: 2011-04-22
forum: General Help
---

### Post by Maintech on 2011-04-22
I keep getting errors from my file system.
> WARNING:  Kernel Errors Present
    [   19.119992] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro ...:  1 Time(s)
    [   22.860668] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,comm ...:  1 Time(s)

I usually have 10 or more errors during an 8 hour day. Anyone know what I need to do to solve this issue? The drive is good and I have checked for bad sectors. Nothing in smart about any drive issues. I didn't have this problem in 10.04. I am wondering if there is something about having my /home encrypted? In 10.04 I did not have it encrypted.

---

### Post by KegHead on 2011-04-22
Hi!

Just an idea;

Update your kernel via;

sudo apt-get update

sudo aptitude install linux-image -f

Restart if asked to.

Please advise if this helps you.

KegHead

---

### Post by Maintech on 2011-04-22
> **KegHead said:**
> Hi!

Just an idea;

Update your kernel via;

sudo apt-get update

sudo aptitude install linux-image -f

Restart if asked to.

Please advise if this helps you.

KegHead

Ok. I have tried to find what the '-f' option does. I can't find it anywhere in the man pages or even google. Before I do this, please explain exactly what this option will do. My assumption is that it will 'force' another install of the image.

---

### Post by KegHead on 2011-04-22
Hi!

From what I understand it will clear up any dependencies.

[COLOR="Red"]There is no harm or foul to your system.
[/COLOR]
I run this every morning.

KegHead

---

### Post by Maintech on 2011-04-22
> **KegHead said:**
> Hi!

From what I understand it will clear up any dependencies.

[COLOR="Red"]There is no harm or foul to your system.
[/COLOR]
I run this every morning.

KegHead

I have ksplice installed and it didn't ask me to reboot. I guess I will have to wait a while and see. I will give it 24 hours. Then I will let you know what happened....for good or no change.

By the way...thanks for the reply.  :)

---

### Post by KegHead on 2011-04-22
Hi!

This is what I run every morning.

I think a lot of others users do also!

jim@jim:~$ sudo apt-get update
[sudo] password for jim: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197 B]                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,077 B]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [864 kB]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,095 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,381 kB]           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,555 kB]        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [9,012 B]   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,020 kB]    
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 13.2 MB in 25s (512 kB/s)
Reading package lists... Done
jim@jim:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim:~$ sudo apt-get install linux-image -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@jim:~$ 

Hope this helps!

KegHead

---

### Post by Maintech on 2011-04-23
Nope. Did not work. This looks like something that is going to be hard to track down. Anyone have any ideas on how to trap the cause please let me know. These are all kernel errors.
> WARNING:  Segmentation Faults in these executables
    [  257.245197] npviewer.bin :  1 Time(s)
 
 WARNING:  Kernel Errors Present
    [   19.036057] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro ...:  1 Time(s)
    [   21.553354] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro ...:  1 Time(s)
    [   25.248310] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,comm ...:  1 Time(s)
    [   29.980215] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,comm ...:  1 Time(s)
    [   37.593267] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,comm ...:  1 Time(s)
 

These have occurred in the last 12 hours.

---

