---
title: "Flashplugin non-free is not working (Ubuntu 9.10)"
date: 2009-11-21
forum: General Help
---

### Post by C_Chin on 2009-11-21
Hello, Im new to Ubuntu/ linux. Anyways I installed ubuntu today and realized that i couldn't install the flash player. I went to the adobe website, looked through lots of forums and i think I made my problem worse because now I have package installer icon (which was not there before) that keeps on giving me the error message E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal. However when I do a search for the file there is not such file on my comp with flash or plugin the name. And I also tried to fix the broken packages but that did not work either. I found a command that I thought would remove the flashplugin non-free=> I went to the terminal and entered sudo dpkg --force-uninstall-reinstreq flashplugin-nonfree and it doesn't work. Any ideas? please help! thanks :D

---

### Post by hwttdz on 2009-11-21
What do you get when you run 
"sudo apt-get purge flashplugin-nonfree"?

---

### Post by Scott753 on 2009-11-21
have you tried sudo apt-get install flashplugin?

---

### Post by C_Chin on 2009-11-21
I entered that command and this is what came up 
crystal@crystal-laptop:~$ sudo apt-get purge flashplugin-nonfree
[sudo] password for crystal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 160kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
crystal@crystal-laptop:~$ 

doesn't work

---

### Post by hwttdz on 2009-11-21
What about
"sudo aptitude reinstall flashplugin-nonfree"?

---

### Post by C_Chin on 2009-11-21
When I type in that first command this is what happens? What should I do next?

crystal@crystal-laptop:~$ sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
--2009-11-21 21:56:29--  [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 272         --.-K/s   in 0s      

2009-11-21 21:56:30 (12.9 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [37.1kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [17.1kB]
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages [3,268B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [5,217B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [6,729B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [793B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [14B]
Get:13 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages [6,154B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [14B]
Fetched 86.0kB in 0s (89.2kB/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hwttdz on 2009-11-21
That actually offers a couple of possibilities first try
sudo apt-get -f install
then 
sudo apt-get install flashplugin-installer

Let us know.  The gpg fix can be found pretty easily through google, I have to look it up every time.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> What about
"sudo aptitude reinstall flashplugin-nonfree"?
This is what happens when i type in the command sudo aptitude reinstall flashplugin-nonfree ... still not working 

crystal@crystal-laptop:~$ sudo aptitude reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  flashplugin-nonfree 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the flashplugin-nonfree package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the flashplugin-nonfree package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

### Post by hwttdz on 2009-11-21
Ok this command will certainly break flash (but I understand that's already sort of the case).  It finds all the flash libraries on your machine and removes them all.

sudo find / -name libflashplayer.so -print0|xargs -0 sudo rm

Then you can try the commands above to purge/reinstall, I don't really suspect that to make much of a difference.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> That actually offers a couple of possibilities first try
sudo apt-get -f install
then 
sudo apt-get install flashplugin-installer

Let us know.  The gpg fix can be found pretty easily through google, I have to look it up every time.
Hello I tried both of those commands and this is what came back ... not sure what to do next 

 sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
crystal@crystal-laptop:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
crystal@crystal-laptop:~$

---

### Post by Scott753 on 2009-11-21
I think the problem is that you need to update.

Try sudo apt-get update

and then

sudo apt-get upgrade

and then try 

sudo apt-get install flashplugin-nonfree 

again.

---

### Post by michy99 on 2009-11-21
This problem usually occurs because the partner repositories are not enabled. Go to System->Administration->Software Sources and click the Other Software tab. Make sure the lines with the word 'partner' are checked.

---

### Post by C_Chin on 2009-11-21
> **Scott753 said:**
> I think the problem is that you need to update.

Try sudo apt-get update

and then

sudo apt-get upgrade

and then try 

sudo apt-get install flashplugin-nonfree 

again.
Hi scott i tried those commands and it said i have unmet dependencies 

crystal@crystal-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 198B in 0s (272B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
crystal@crystal-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
crystal@crystal-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
crystal@crystal-laptop:~$

---

### Post by C_Chin on 2009-11-21
> **michy99 said:**
> This problem usually occurs because the partner repositories are not enabled. Go to System->Administration->Software Sources and click the Other Software tab. Make sure the lines with the word 'partner' are checked.
the lines with partner are checked ... but I still flashplugin is still not working

---

### Post by hwttdz on 2009-11-21
Removed due to previous post answering question.

---

### Post by Scott753 on 2009-11-21
Sorry if my advice isn't working out so far. I guess we can only keep trying. :D Or maybe someone wiser will step in and give you a hand. 

Could you post the results from

sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update

---

### Post by C_Chin on 2009-11-21
> **Scott753 said:**
> Sorry if my advice isn't working out so far. I guess we can only keep trying. :D Or maybe someone wiser will step in and give you a hand. 

Could you post the results from

sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude update
Should I continue ?? 

crystal@crystal-laptop:~$ sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude upgrade
[sudo] password for crystal: 
Writing extended state information... 1%
Writing extended state information... Done
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                 
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 198B in 0s (260B/s)
Reading package lists... Done             
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  medibuntu-keyring 
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 49.2kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  medibuntu-keyring 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":

---

### Post by hwttdz on 2009-11-21
Did you try the 
find|rm command I gave a while back?

Also what did you do to get yourself to this state? maybe that will help some?  At the command line you can just type "history" and grab any commands related to you "installing" flash.  This sound like something that will be work-out-able so I wouldn't go too crazy just yet.

---

### Post by hwttdz on 2009-11-21
Did you enter "yes" to install the keyring?  You should, they're not that untrustworthy <wink>

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Did you enter "yes" to install the keyring?  You should, they're not that untrustworthy <wink>
Haha I entered yes and this is what happens

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
E: I wasn't able to locate file for the flashplugin-nonfree package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the flashplugin-nonfree package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

### Post by hwttdz on 2009-11-21
Try this one

sudo find / -name libflashplayer* -print0|xargs -0 -t sudo rm

then try the purge/reinstall commands.  You can probably post just the last few lines from each command.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Did you try the 
find|rm command I gave a while back?

Also what did you do to get yourself to this state? maybe that will help some?  At the command line you can just type "history" and grab any commands related to you "installing" flash.  This sound like something that will be work-out-able so I wouldn't go too crazy just yet.
This is what happened when i typed the find|rm command

crystal@crystal-laptop:~$ sudo find / -name libflashplayer.so -print0|xargs -O sudo rm
xargs: invalid option -- 'O'
Usage: xargs [-0prtx] [--interactive] [--null] [-d|--delimiter=delim]
       [-E eof-str] [-e[eof-str]]  [--eof[=eof-str]]
       [-L max-lines] [-l[max-lines]] [--max-lines[=max-lines]]
       [-I replace-str] [-i[replace-str]] [--replace[=replace-str]]
       [-n max-args] [--max-args=max-args]
       [-s max-chars] [--max-chars=max-chars]
       [-P max-procs]  [--max-procs=max-procs] [--show-limits]
       [--verbose] [--exit] [--no-run-if-empty] [--arg-file=file]
       [--version] [--help] [command [initial-arguments]]

Report bugs to <bug-findutils@gnu.org>.

---

### Post by hwttdz on 2009-11-21
This is why one copies and pastes rather than types (and uses a font that draws a dot in a zero), the letter oh is in fact a digit zero.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Try this one

sudo find / -name libflashplayer* -print0|xargs -0 -t sudo rm

then try the purge/reinstall commands.  You can probably post just the last few lines from each command.
Is that two separate commands or just one? I used copy pasted it into the terminal as one command and it says
sudo rm 
rm: missing operand

---

### Post by hwttdz on 2009-11-21
No that's perfectly reasonable output (if a little surprising), it's just saying that there is no flash library found on your machine.

---

### Post by Scott753 on 2009-11-21
hwttdz is right. please type history and paste the results.

---

### Post by C_Chin on 2009-11-21
> **Scott753 said:**
> hwttdz is right. please type history and paste the results.
crystal@crystal-laptop:~$ history
    1  sudo apt-get install flashplugin-nonfree
    2  /usr/lib/adobe-flashplugin/libflashplayer.so
    3  sudo apt-get install flashplugin-nonfree
    4  sudo apt-get remove --purge flashplugin-nonfree
    5  wget [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)
    6  sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
    7  sudo aptitude install libnspr4-dev libnss 3-dev ubuntu-restricted-extras
    8  sudo aptitude install-f
    9  sudo aptitude update
   10  sudo aptitude dist-upgrade
   11  sudo dpkg -i opera_9.10-20061214.6-shared-qt_en_i386.deb
   12  sudo aptitude remove flashplugin-nonfree
   13  sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
   14  rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
   15  dpkg --remove --force-remove-reinstreq flashplugin-nonfree
   16  dpkg --purge --force-remove-reinstreq flashplugin-nonfree
   17  $ sudo apt-get install flashplugin-nonfree
   18  sudeo apt-get install flashplugin-nonfree
   19  sudo apt-get install flashplugin-nonfree
   20  sudo apt-get -f install
   21  /var/lib/dpkg/alternatives/*flash* -type f -size 0 | xargs sudo rm
   22  sudo /var/lib/dpkg/alternatives/*flash* -type f -size 0 | xargs sudo rm
   23  sudo apt-get purge flashplugin-nonfree
   24  sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
   25  sudo aptitude reinstall flashplugin-nonfree
   26  sudo apt-get install flashplugin-nonfree
   27  sudo aptitude reinstall flashplugin-nonfree
   28  sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
   29  sudo apt-get -f install
   30  sudo apt-get install flashplugin-installer
   31  sudo apt-get update
   32  sudo apt-get upgrade
   33  sudo apt-get install flashplugin-nonfree
   34  sudo aptitude update && sudo aptitude install medibuntu-keyring && sudo aptitude upgrade
   35  find|rm
   36  sudo find / -name libflashplayer.so -print0|xargs -0 sudo rm
   37  sudo find / -name libflashplayer.so -print0|xargs -0
   38  sudo find/-name libflashplayer.so -print0|xargs -0 sudo rm
   39  sudo find / -name libflashplayer.so -print0|xargs -0
   40  sudo find / -name libflashplayer.so -print0|xargs -O sudo rm
   41  sudo find / -name libflashplayer* -print0|xargs -0 -t sudo rm
   42  sudo find / -name libflashplayer* -printO|xargs -O -t 
   43  sudo rm
   44  sudo find|rm
   45  sudo find / -name libflashplayer* -print0|xargs -0 -t sudo rm
   46  sudo find / -name libflashplayer* -print0|xargs -0
   47  sudo find / -name libflashplayer* -print0|xargs -0 -t sudo rm
   48  rm --help
   49  history

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> No that's perfectly reasonable output (if a little surprising), it's just saying that there is no flash library found on your machine.
Crystal@crystal-laptop:~$ sudo apt-get purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 160kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
crystal@crystal-laptop:~$ sudo aptitude reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 160kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
dpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

Current status: 1 update [+1].

What do I do now?

---

### Post by hwttdz on 2009-11-21
What about this?
sudo find / -name *flash*|grep -Ev "icons|media|vlc"

Also what architecture is your machine? "uname -a"

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> What about this?
sudo find / -name *flash*|grep -Ev "icons|media|vlc"

Also what architecture is your machine? "uname -a"
The following is what i get from both of those commands. 

crystal@crystal-laptop:~$ sudo find / -name *flash*|grep -Ev "icons|media|vlc"
/lib/modules/2.6.31-14-generic/kernel/drivers/mtd/devices/mtd_dataflash.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/mtd/maps/ts5500_flash.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/mtd/maps/scb2_flash.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/usr/lib/openoffice/basis3.1/program/libflashli.so
/usr/lib/python2.6/dist-packages/twisted/web/woven/flashconduit.pyc
/usr/lib/python2.6/dist-packages/twisted/web/woven/flashconduit.py
/usr/lib/libvisual-0.4/morph/morph_flash.so
/usr/lib/flashplugin-nonfree
/usr/bin/btcflash
/usr/src/linux-headers-2.6.31-14/arch/arm/include/asm/mach/flash.h
/usr/src/linux-headers-2.6.31-14/arch/arm/include/asm/nwflash.h
/usr/src/linux-headers-2.6.31-14/arch/cris/include/asm/axisflashmap.h
/usr/src/linux-headers-2.6.31-14/arch/mips/include/asm/mach-excite/excite_nandflash.h
/usr/src/linux-headers-2.6.31-14/arch/sparc/include/asm/jsflash.h
/usr/src/linux-headers-2.6.31-14/include/linux/mtd/flashchip.h
/usr/src/linux-headers-2.6.31-14/include/linux/spi/flash.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/mtd/dataflash.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/mtd/dataflash
/usr/src/linux-headers-2.6.31-14-generic/include/config/mtd/scx200/docflash.h
/usr/src/linux-headers-2.6.31-14-generic/include/config/mtd/scb2/flash.h
/usr/share/mime/application/x-shockwave-flash.xml
/usr/share/pyshared/twisted/web/woven/flashconduit.py
/usr/share/lintian/overrides/flashplugin-nonfree
/usr/share/doc/flashplugin-nonfree
/usr/share/app-install/desktop/flashblock.desktop
/usr/share/app-install/desktop/flashplugin-installer.desktop
/usr/share/man/man8/btcflash.8.gz
/tmp/install_flash_player_10_linux.deb
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.md5sums
/var/lib/dpkg/info/flashplugin-nonfree.templates
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/update-rc.d/flashplugin-nonfree
/var/lib/flashplugin-nonfree
/var/cache/apt/archives/flashplugin-installer_10.0.32.18ubuntu1_i386.deb
/var/cache/apt/archives/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb
/var/cache/flashplugin-nonfree
/var/crash/flashplugin-nonfree.0.crash
/var/crash/flashplugin-installer.0.crash
crystal@crystal-laptop:~$ uname -a
Linux crystal-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by Scott753 on 2009-11-21
Hey, I think I found it. There was a previous user who had a similar problem. 

[http://newyork.ubuntuforums.org/showthread.php?t=1293913&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1293913&page=2)

One of the posts says:

"This is a rather risky attempt to solve your problem."

But apparently, it worked. So, if you do the:

sudo gedit /var/lib/dpkg/status 

Then hit Ctrl + F and go to flashplugin-nonfree

and delete from "Package:" to "Description:" and hit save.

Then do sudo apt-get install flashplugin-installer

the problem should be fixed.

Edit: hwttdz is right, you should probably try to find another solution first.

---

### Post by hwttdz on 2009-11-21
"cat /var/crash/flashplugin-nonfree.0.crash /var/crash/flashplugin-installer.0.crash" if you don't get crazy binary output, post the output here.  If you do, saying "I got crazy binary output" is more than sufficient.

I wouldn't suggest doing what's mentioned above just yet.  And if we decide that's a good way to go there are a bunch of those files we're going to want to remove at the same time.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> "cat /var/crash/flashplugin-nonfree.0.crash /var/crash/flashplugin-installer.0.crash" if you don't get crazy binary output, post the output here.  If you do, saying "I got crazy binary output" is more than sufficient.

I wouldn't suggest doing what's mentioned above just yet.  And if we decide that's a good way to go there are a bunch of those files we're going to want to remove at the same time.
Alas no crazy binary output

crystal@crystal-laptop:~$ cat /var/crash/flashplugin-nonfree.0.crash /var/crash/flashplugin-installer.0.crash
cat: /var/crash/flashplugin-nonfree.0.crash: Permission denied
cat: /var/crash/flashplugin-installer.0.crash: Permission denied

---

### Post by hwttdz on 2009-11-21
Add sudo before the cat command, odds of crazy output are still 50/50.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Add sudo before the cat command, odds of crazy output are still 50/50.
I got crazy binary output ... last few lines look like this

DistroRelease: Ubuntu 9.10
InstallationMedia: Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
ProcVersionSignature: Ubuntu 2.6.31-14.48-generic
Title: package flashplugin-installer (not installed) failed to install/upgrade: conflicting packages - not installing flashplugin-installer
Uname: Linux 2.6.31-14-generic i686

---

### Post by hwttdz on 2009-11-21
Ok, final question before I recommend drastic action
sudo find / -name *flashplugin*

My plan is check that list of files, remove the files, attempt to reinstall, edit /var/lib/dpkg/status, attempt to reinstall.  That's as far as the plan goes.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Ok, final question before I recommend drastic action
sudo find / -name *flashplugin*

My plan is check that list of files, remove the files, attempt to reinstall, edit /var/lib/dpkg/status, attempt to reinstall.  That's as far as the plan goes.
Results from command

crystal@crystal-laptop:~$ sudo find / -name *flashplugin*
/usr/lib/flashplugin-nonfree
/usr/share/lintian/overrides/flashplugin-nonfree
/usr/share/doc/flashplugin-nonfree
/usr/share/app-install/icons/adobeflashplugin.png
/usr/share/app-install/desktop/flashplugin-installer.desktop
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.md5sums
/var/lib/dpkg/info/flashplugin-nonfree.templates
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/update-rc.d/flashplugin-nonfree
/var/lib/flashplugin-nonfree
/var/cache/apt/archives/flashplugin-installer_10.0.32.18ubuntu1_i386.deb
/var/cache/apt/archives/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb
/var/cache/flashplugin-nonfree
/var/crash/flashplugin-nonfree.0.crash
/var/crash/flashplugin-installer.0.crash

---

### Post by hwttdz on 2009-11-21
Ok the command that I would run, were I in your situation is

sudo find / -name *flashplugin* -print0|xargs -0 -n 1 -t sudo rm -rf

realize at this point this is pretty destructive, it's searching your filesystem for everything that contains "flashplugin" in the name, and removing it.  Realize that there is no "undo" button for this command, the list of files in your above post is the exact list of files that will be removed.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Ok the command that I would run, were I in your situation is

sudo find / -name *flashplugin* -print0|xargs -0 -n 1 -t sudo rm -rf

realize at this point this is pretty destructive, it's searching your filesystem for everything that contains "flashplugin" in the name, and removing it.  Realize that there is no "undo" button for this command, the list of files in your above post is the exact list of files that will be removed.
crystal@crystal-laptop:~$ sudo find / -name *flashplugin* -print0|xargs -0 -n 1 -t sudo rm -rf
sudo rm -rf /usr/lib/flashplugin-nonfree 
sudo rm -rf /usr/share/lintian/overrides/flashplugin-nonfree 
sudo rm -rf /usr/share/doc/flashplugin-nonfree 
sudo rm -rf /usr/share/app-install/icons/adobeflashplugin.png 
sudo rm -rf /usr/share/app-install/desktop/flashplugin-installer.desktop 
sudo rm -rf /var/lib/dpkg/info/flashplugin-nonfree.postrm 
sudo rm -rf /var/lib/dpkg/info/flashplugin-nonfree.postinst 
sudo rm -rf /var/lib/dpkg/info/flashplugin-nonfree.md5sums 
sudo rm -rf /var/lib/dpkg/info/flashplugin-nonfree.templates 
sudo rm -rf /var/lib/dpkg/info/flashplugin-nonfree.config 
sudo rm -rf /var/lib/dpkg/info/flashplugin-nonfree.list 
sudo rm -rf /var/lib/update-rc.d/flashplugin-nonfree 
sudo rm -rf /var/lib/flashplugin-nonfree 
sudo rm -rf /var/cache/apt/archives/flashplugin-installer_10.0.32.18ubuntu1_i386.deb 
sudo rm -rf /var/cache/apt/archives/flashplugin-nonfree_10.0.32.18ubuntu1_i386.deb 
sudo rm -rf /var/cache/flashplugin-nonfree 
sudo rm -rf /var/crash/flashplugin-nonfree.0.crash 
sudo rm -rf /var/crash/flashplugin-installer.0.crash 


Thats the output I got

---

### Post by hwttdz on 2009-11-21
Now attempt to remove
$ sudo apt-get remove flashplugin-nonfree
then install
$ sudo apt-get install flashplugin-nonfree
we're probably going to need to edit the other file mentioned in order to let the system know that what it thinks is installed we removed with brute force.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Now attempt to remove
$ sudo apt-get remove flashplugin-nonfree
then install
$ sudo apt-get install flashplugin-nonfree
we're probably going to need to edit the other file mentioned in order to let the system know that what it thinks is installed we removed with brute force.
... it keeps saying that there are unmet dependencies? what does that mean? 

The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by hwttdz on 2009-11-21
Packages (what we install or remove), sometimes depend on other packages, the packages they depend upon are called their dependencies.  flashplugin-nonfree depends on flashplugin-installer, but usually the package manager takes care of all this nitty gritty for you.  In fact there's a package "ubuntu-desktop" which has as dependencies pretty much everything that is installed by default, which means that if you have for some reason removed a lot of things that are in the default desktop, and later decide you want some of that back and don't want to remember every little thing (...cue police...) all you have to do is install ubuntu-desktop.  And now returning to our regularly scheduled programming.  

Try 
$ sudo apt-get -f install

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Packages (what we install or remove), sometimes depend on other packages, the packages they depend upon are called their dependencies.  flashplugin-nonfree depends on flashplugin-installer, but usually the package manager takes care of all this nitty gritty for you.  In fact there's a package "ubuntu-desktop" which has as dependencies pretty much everything that is installed by default, which means that if you have for some reason removed a lot of things that are in the default desktop, and later decide you want some of that back and don't want to remember every little thing (...cue police...) all you have to do is install ubuntu-desktop.  And now returning to our regularly scheduled programming.  

Try 
$ sudo apt-get -f install
crystal@crystal-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  flashplugin-installer flashplugin-nonfree
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins msttcorefonts ttf-bitstream-vera
  ttf-dejavu ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
The following packages will be upgraded:
  flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 21.4kB of archives.
After this operation, 69.6kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse flashplugin-installer 10.0.32.18ubuntu1 [19.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse flashplugin-nonfree 10.0.32.18ubuntu1 [1,766B]
Fetched 21.4kB in 0s (39.9kB/s)              
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

output from last command

---

### Post by hwttdz on 2009-11-21
Also so you can get an idea of what the commands I'm running are doing

sudo - gives you admin permissions, if you get a permissions error and you're sure you want to do what you're telling it to do use sudo
cat - stands for concatenate, dumps the contents of a file to standard out (what you see), at least that's what I understand
rm - stands for remove, deletes files
find - kind of obvious
apt - apt is the package manager, it's supposed to be smart and know how to install and remove packages, it's botching things up pretty well in this case
| - pipe, pipes are awesome, they allow one to use the output of one command as the input to another
xargs - xargs is also involved in piping and creating commands that are a little too complicated, say I want to find a file named bar, then display the contents, what I want is "cat (find / -name bar)", but the command line doesn't understand order of operations as such, so instead I run "find / -name bar|xargs cat", which says find things named bar, then send the output of this command to the input of the next, and xargs takes standard-in, what you type or what the pipe gives it and uses it as an argument to the next command.  It's one of the more complicated commands, took me a while to get a hang of it.  Feel free to ask if you have other questions.

---

### Post by C_Chin on 2009-11-21
> **hwttdz said:**
> Also so you can get an idea of what the commands I'm running are doing

sudo - gives you admin permissions, if you get a permissions error and you're sure you want to do what you're telling it to do use sudo
cat - stands for concatenate, dumps the contents of a file to standard out (what you see), at least that's what I understand
rm - stands for remove, deletes files
find - kind of obvious
apt - apt is the package manager, it's supposed to be smart and know how to install and remove packages, it's botching things up pretty well in this case
| - pipe, pipes are awesome, they allow one to use the output of one command as the input to another
xargs - xargs is also involved in piping and creating commands that are a little too complicated, say I want to find a file named bar, then display the contents, what I want is "cat (find / -name bar)", but the command line doesn't understand order of operations as such, so instead I run "find / -name bar|xargs cat", which says find things named bar, then send the output of this command to the input of the next, and xargs takes standard-in, what you type or what the pipe gives it and uses it as an argument to the next command.  It's one of the more complicated commands, took me a while to get a hang of it.  Feel free to ask if you have other questions.
thanks that clarifies some stuff... i've used windows all my life and am not that tech savvy so doing all this command stuff (which i never did on windows) is taking some time to get adjusted to ... any ideas of what to do next? should i do what scott suggested earlier?

---

### Post by hwttdz on 2009-11-22
Yup, that's where we are now.  I'm sort of looking through my /var/lib/dpkg file right now to see if we can make that method a little more elegant.  Either way, you should certainly make a copy of your /var/lib/dpkg file

$ sudo cp /var/lib/dpkg/status ~/dpkg-status.backup

because odds are unfortunately high that we're going to need the backup.

And seeing I used a command I didn't tell you what it does, cp is copy.

Edit: didn't include filename in command.

---

### Post by hwttdz on 2009-11-22
Once you have the file backed up, delete everything in the blocks for flashplugin-nonfree and flashplugin-installer, so first line to go is 
Package: flashplugin-whatever, and delete all the way to the space in the file.  
$ sudo gedit /var/lib/dpkg/status
ctrl + f "flashplugin"
then delete the entire block, try again to make sure there isn't another block referencing the other package (i.e. installer vs nonfree).

Edit: after making these changes save, then 
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get remove flashplugin-nonfree flashplugin-installer
if it asks you to run "apt-get -f install then
$ sudo apt-get -f install

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> Yup, that's where we are now.  I'm sort of looking through my /var/lib/dpkg file right now to see if we can make that method a little more elegant.  Either way, you should certainly make a copy of your /var/lib/dpkg file

$ sudo cp /var/lib/dpkg/status ~/dpkg-status.backup

because odds are unfortunately high that we're going to need the backup.

And seeing I used a command I didn't tell you what it does, cp is copy.

Edit: didn't include filename in command.
Hello, I made followed that command and no output came up ... is that normal? Also in order to back up do I need a CD or flash drive? Sorry for the late response

---

### Post by hwttdz on 2009-11-22
Post the output of the command
ls ~/*.backup
if you get
/home/username/dpkg-status.backup 
then the backup succeeded.

Generally on the command line silence is golden.  What we're doing to backup the file is copying it from the root file tree to our home file tree, that way if we really botch up the copy on the root file tree, we can just replace it with the old copy.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> Post the output of the command
ls ~/*.backup
if you get
/home/username/dpkg-status.backup 
then the backup succeeded.

Generally on the command line silence is golden.  What we're doing to backup the file is copying it from the root file tree to our home file tree, that way if we really botch up the copy on the root file tree, we can just replace it with the old copy.
crystal@crystal-laptop:~$ sudo cp /var/lib/dpkg/status ~/dpkg-status.backup
[sudo] password for crystal: 
crystal@crystal-laptop:~$ ~/*.backup
bash: /home/crystal/dpkg-status.backup: Permission denied
 

Not sure what I did wrong ...

---

### Post by hwttdz on 2009-11-22
So that actually tells me that the backup command worked.  You tried to execute the file ~/dpkg-status.backup, which is not an executable, so you got a permission denied error.  If you run "ls ~/dpkg-status.backup" you should get /home/username/dpkg-status.backup (ls is the command for list).

So now you can go ahead and remove the blocks relating to flashplugin (i.e. nonfree and installer, don't remove ubuntu restricted extras or anything else, though we may have to try that later) from /var/lib/dpkg/status then save then try the apt-get commands again. 

$ sudo apt-get update
$ sudo apt-get -f install
$ sudo apt-get remove flashplugin-nonfree flashplugin-installer

And once we get a clean starting point we'll worry about installing.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> So that actually tells me that the backup command worked.  You tried to execute the file ~/dpkg-status.backup, which is not an executable, so you got a permission denied error.  If you run "ls ~/dpkg-status.backup" you should get /home/username/dpkg-status.backup (ls is the command for list).

So now you can go ahead and remove the blocks relating to flashplugin (i.e. nonfree and installer, don't remove ubuntu restricted extras or anything else, though we may have to try that later) from /var/lib/dpkg/status then save then try the apt-get commands again. 

$ sudo apt-get update
$ sudo apt-get -f install
$ sudo apt-get remove flashplugin-nonfree flashplugin-installer

And once we get a clean starting point we'll worry about installing.
ok just to make sure I delete the entire block that mentions flashplugin ... the block begins with 
Package: ...
Status: ...
Priority: ...
Section: ...
(some other stuff) => then ends with
Description: ...

---

### Post by hwttdz on 2009-11-22
Well the next block starts with Package again, and there's a blank line between the two, so delete all the way to the next Package line and leave a blank line between the last line of the previous block the the Package line of the next block.  Here's what I see in mine

```
.
.
Original-Maintainer: Ross Burton <ross@debian.org>

Package: flashplugin-installer
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 184
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: amd64
Source: flashplugin-nonfree
Version: 10.0.32.18ubuntu1
Replaces: flashplugin (<< 6), flashplugin-nonfree
Provides: flashplugin-nonfree
Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1), ia32-libs (>= 2.2ubuntu18), debconf | debconf-2.0, wget, fontconfig
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-nonfree (<< 10.0.22.87ubuntu2~), libflashsupport, xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from the net.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: http://wiki.ubuntu.com/FlashPlayer9
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player (http://www.adobe.com)
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>

Package: human-icon-theme
.
.
```

So the entire block in the middle gets removed.  Everything between ross@debian and Package: human-icon-theme, and just leave one blank line between the two (this is why we backed up the file before hacking at it).  Anyways, description is sometimes the last part of a block, but not always.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> Well the next block starts with Package again, and there's a blank line between the two, so delete all the way to the next Package line and leave a blank line between the last line of the previous block the the Package line of the next block.  Here's what I see in mine

```
.
.
Original-Maintainer: Ross Burton <ross@debian.org>

Package: flashplugin-installer
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 184
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: amd64
Source: flashplugin-nonfree
Version: 10.0.32.18ubuntu1
Replaces: flashplugin (<< 6), flashplugin-nonfree
Provides: flashplugin-nonfree
Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1), ia32-libs (>= 2.2ubuntu18), debconf | debconf-2.0, wget, fontconfig
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (<< 6), flashplugin-nonfree (<< 10.0.22.87ubuntu2~), libflashsupport, xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from the net.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
Homepage: http://wiki.ubuntu.com/FlashPlayer9
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player (http://www.adobe.com)
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>

Package: human-icon-theme
.
.
```

So the entire block in the middle gets removed.  Everything between ross@debian and Package: human-icon-theme, and just leave one blank line between the two (this is why we backed up the file before hacking at it).  Anyways, description is sometimes the last part of a block, but not always.
Okay I think I have a clean start I've attached the output from the end of the 1st command and then the other two commands. 

Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
crystal@crystal-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
crystal@crystal-laptop:~$ sudo apt-get remove flashplugin-nonfree flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
Package flashplugin-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by hwttdz on 2009-11-22
Ok I think the command for the key errors is 

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783

And then you'll finally be on to installing a clean version of flash.  Whew, that was a crazy one.  As a first move I recommend using synaptic to reinstall ubuntu-restricted-extras.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> Ok I think the command for the key errors is 

$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783

And then you'll finally be on to installing a clean version of flash.  Whew, that was a crazy one.  As a first move I recommend using synaptic to reinstall ubuntu-restricted-extras.
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

Output from last command ... should I go on the adobe website and try to install the flash plugin? Also what is synaptic?

---

### Post by hwttdz on 2009-11-22
For the time being let's avoid installing anything in a fashion bypassing the package manager.  

Synaptic is a gorgeous frontend for the ubuntu package manager.  To fire it up run 
$ sudo synaptic
then you should be able to type ubuntu-restricted-extras into the quicksearch box (which is admittedly tempermental, and you may have to do a real search), then right click on ubuntu restricted extras, and select reinstall, then hit the checkmark on the toolbar marked apply.  A little box should pop up and hopefully it won't give you any errors.  After doing this check flash using firefox and your website of choice and let us know the status.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> For the time being let's avoid installing anything in a fashion bypassing the package manager.  

Synaptic is a gorgeous frontend for the ubuntu package manager.  To fire it up run 
$ sudo synaptic
then you should be able to type ubuntu-restricted-extras into the quicksearch box (which is admittedly tempermental, and you may have to do a real search), then right click on ubuntu restricted extras, and select reinstall, then hit the checkmark on the toolbar marked apply.  A little box should pop up and hopefully it won't give you any errors.  After doing this check flash using firefox and your website of choice and let us know the status.
I installed ubuntu restricted extras but when I got to Pandora or Youtube it still says I need a flashplugin

---

### Post by hwttdz on 2009-11-22
And when you look at the flashplugin-installer in synaptic is it checked? if not check it and hit apply and retest.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> And when you look at the flashplugin-installer in synaptic is it checked? if not check it and hit apply and retest.
neither  flashplugin installer nor flashplugin non-free is checked ...should i check both or just installer?

---

### Post by hwttdz on 2009-11-22
Check the installer, it should mark both, then apply.  Test again.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> Check the installer, it should mark both, then apply.  Test again.
It doesn't automatically check the flashplugin non-free ... should i just download the installer for now?

---

### Post by hwttdz on 2009-11-22
Check both then apply, then test (restart firefox, visit flash site).  Don't download anything yet, that's sort of how you ended up in this situation.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> Check both then apply, then test (restart firefox, visit flash site).  Don't download anything yet, that's sort of how you ended up in this situation.
ok checked apply and screen comes up that says it will remove adobe-flashplugin and install flashplugin-installer and flashplugin-nonfree ... im on the right track?

---

### Post by hwttdz on 2009-11-22
No, were they unmarked?

You want both marked, so you may have to mark only one of the two, if either is already marked mark it for a reinstall.  Then apply, then test.

---

### Post by C_Chin on 2009-11-22
> **hwttdz said:**
> No, were they unmarked?

You want both marked, so you may have to mark only one of the two, if either is already marked mark it for a reinstall.  Then apply, then test.
Ok Im slightly confused in the synaptics package manager I searched for flashplugin-installer and two things came up.
Flashplugin installer - Description: Adobe Flashplugin installer
Flashplugin nonfree - Description: Adobe Flashplugin installer (transitional package) 

I checked both of those because checking flashplugin installer doesn't automatically check the non free on my computer. When I hit apply a screen comes up that says it will  delete the adobe flashplugin and install the two packages shown above. However, when I just searched flashplugin in the synaptics package mgr 4 files come up, 1 of which is the adobe flashplugin description: adobe flash player plugin version 10 and it is shown as being marked for removal (although I haven't marked any file for removal). The other three files are a sound file and the 2 files shown above. Could it be that its downloaded on my computer but my computer doesn't recognize it?

---

### Post by hwttdz on 2009-11-22
Yes, I'm pretty sure you want to remove adobe flashplugin, so the net effect of installing flashplugin nonfree and flashplugin installer is to (+add, -remove)
+flashplugin nonfree
+flashplugin installer
-adobe flashplugin
Which is what we want.

---

### Post by C_Chin on 2009-11-22
ok i did that tried again on pandora and youtube and still the same issue ... it says i need the latest version of adobe flashplayer ...

---

### Post by wojox on 2009-11-22
```

#Remove Flash
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way

```

---

### Post by C_Chin on 2009-11-23
THanks wojox it worked :D !!!

---

