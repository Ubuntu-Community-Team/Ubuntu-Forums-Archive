---
title: "Upgrading, installing problems, etc..."
date: 2009-07-31
forum: General Help
---

### Post by SweatyBanana on 2009-07-31
Take a look at my screenshot and explain to me what I'm doing wrong. New user to Ubuntu after so many Windows failures...


For whatever reason, I can't install some applications... A lot of them as a matter of fact.

> AMD Athlon 64 Dual-Core Processor 3800+
1024 MB RAM
NVIDIA GeForce 6150 LE

HP Pavilion a1600n
Prod #: RJ181AA
S/N: CNH6340BPF


```
matt@MattsPC:~$ sudo apt-get update
[sudo] password for matt: 
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US      
Get:1 http://archive.canonical.com jaunty Release.gpg [189B]         
Ign http://archive.canonical.com jaunty/partner Translation-en_US    
Hit http://security.ubuntu.com jaunty-security Release.gpg           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Get:2 http://archive.canonical.com jaunty Release [10.5kB]           
Hit http://us.archive.ubuntu.com jaunty Release                            
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US  
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release                     
Hit http://us.archive.ubuntu.com jaunty-updates Release                    
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Get:3 http://archive.canonical.com jaunty/partner Packages [1289B]   
Hit http://us.archive.ubuntu.com jaunty/main Packages                      
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Fetched 12.0kB in 3s (3679B/s)
Reading package lists... Done
matt@MattsPC:~$ sudo apt-get install linux-image-2.6.15-26-686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.15-26-686
matt@MattsPC:~$ sudo apt-get update
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_US   
Hit http://us.archive.ubuntu.com jaunty Release.gpg                 
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Hit http://archive.canonical.com jaunty Release                      
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release                     
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://archive.canonical.com jaunty/partner Packages             
Hit http://us.archive.ubuntu.com jaunty/main Packages                
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Reading package lists... Done
matt@MattsPC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

```

---

### Post by running_rabbit07 on 2009-07-31
"sudo apt-get install linux-image-2.6.15-26-686"

Is that a kernal you are trying to install?

I have the same AMD and NVIDIA as you and my Kernal is 2.6.28-14.

Did you install via the AMD64 ISO?

---

### Post by oldos2er on 2009-07-31
The oldest available kernel for Jaunty is 2.6.28.11; why do you want to install an older one?

---

### Post by SweatyBanana on 2009-08-01
Eh like I said, I'm new to ubuntu. Just following some instructions I found from users on here.. Sorry for the total nubness of my ability to use ubuntu, but I need to learn.

---

### Post by running_rabbit07 on 2009-08-01
> **SweatyBanana said:**
> Eh like I said, I'm new to ubuntu. Just following some instructions I found from users on here.. Sorry for the total nubness of my ability to use ubuntu, but I need to learn.

I don't know much about Kubuntu since I've never used it but, yeah, as far as Kernals go just let your system pick the newest one. I know some people are using kernals that are higher numerically, but they do their own code to make them work.

Anyway, lets see what the problems are. I see your screenshot and it looks like your are having some major issues. 

When you downloaded your CD image was it the AMD64 ISO?

Is it installed within partitions or via Wubi?

---

### Post by SweatyBanana on 2009-08-01
I downloaded the[COLOR=Red] 'UBUNTU 9.04 AMD 64 ISO'[/COLOR]

---

### Post by running_rabbit07 on 2009-08-01
It appears you have it installed via Wubi?

---

### Post by SweatyBanana on 2009-08-01
I have no idea what wubi is, but I partitioned my entire hard drive as far as I know when I installed ubuntu.

At least use entire drive is what I selected when I installed...

---

### Post by running_rabbit07 on 2009-08-01
Wubi is a way of installing Ubuntu as a program within Windows.

The only thing that comes to mind is that you have a bad install and may need to reinstall.

 I would recommend downloading the ISO again and burning at the slowest speed.

If your system id still usable I would wait a little while and see if there are any other recommendations.

---

### Post by oldos2er on 2009-08-01
Well, the "Unable to lock the download directory" can be caused by having more than one package manager program open at once. Assuming you've got an internet connection, try again with the command
```
sudo apt-get update && sudo apt-get upgrade
```

To install proprietary video drivers, go to menus KMenus, System, Hardware Drivers Manager, and tick the appropriate box.

---

### Post by SweatyBanana on 2009-08-01
```
matt@MattsPC:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for matt:                                  
Hit http://security.ubuntu.com jaunty-security Release.gpg 
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://archive.canonical.com jaunty Release.gpg                  
Ign http://archive.canonical.com jaunty/partner Translation-en_US    
Hit http://us.archive.ubuntu.com jaunty Release.gpg                  
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US       
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US  
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release                     
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US       
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US         
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US       
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg                
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US     
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://archive.canonical.com jaunty Release                             
Hit http://us.archive.ubuntu.com jaunty Release                             
Hit http://us.archive.ubuntu.com jaunty-updates Release
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
```

---

### Post by michy99 on 2009-08-01
What happens if you run this in a terminal?```
sudo dpkg --configure -a
```

---

### Post by SweatyBanana on 2009-08-02
```
matt@MattsPC:~$ sudo dpkg --configure -a
[sudo] password for matt:
Setting up avg85flx (8.5.287) ...
Installing 'avgd' service initscripts...
ln: creating symbolic link `/etc/init.d/avgd': File exists
dpkg: error processing avg85flx (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 avg85flx


```

---

### Post by michy99 on 2009-08-02
You could try:```
sudo apt-get install -f
```By the way, I hope you are aware that AVG 8.5 for linux is command-line only. It has no GUI interface.

---

### Post by SweatyBanana on 2009-08-02
Yes I wasn't aware before hand :confused:


```
matt@MattsPC:~$ sudo apt-get install -f
[sudo] password for matt:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up avg85flx (8.5.287) ...
Installing 'avgd' service initscripts...
ln: creating symbolic link `/etc/init.d/avgd': File exists
dpkg: error processing avg85flx (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 avg85flx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

