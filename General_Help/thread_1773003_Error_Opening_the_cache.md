---
title: "Error: Opening the cache"
date: 2011-06-01
forum: General Help
---

### Post by Clex19 on 2011-06-01
I'm using Lubuntu 11.04. Every time I boot up my computer, a do not enter sign appears right next to the clock. When I hover my mouse over it, it says: 

"An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was:'Error: Opening the cache (E:Read error - read (5:Input/output error),E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies"

I tried opening Package Manager by right-clicking the icon like it said, but nothing happened.

I tried this in the Terminal:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

I found those commands here: [http://ubuntuforums.org/showthread.php?t=1753585](http://ubuntuforums.org/showthread.php?t=1753585)

The above commands didn't seem to do anything.

I also tried:

sudo apt-get -f install

I found that command here: [https://answers.launchpad.net/ubuntu/+question/50944](https://answers.launchpad.net/ubuntu/+question/50944)

The above command resulted in:

"Reading package lists...Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened."

Please help. Any ideas are welcome.

---

### Post by linuxinstalledfromhdd on 2011-06-01
Before the last time this happened did you add software or enable any new repositories?

---

### Post by Clex19 on 2011-06-01
@linuxinstallfromhdd

I don't think I did.

---

### Post by linuxinstalledfromhdd on 2011-06-01
How old is the system. Which version.  What PPA's or repositories have you installed since you installed the system?  Any changes made to the system in the last 3 months?  Any information would be very very very helpful.

---

### Post by Clex19 on 2011-06-01
@linuxinstalledfromhdd

The system is new. I installed it on May 24th of this year. It is Lubuntu 11.04 Natty Narwhal. I'm not quite sure what PPA's are...but I know I haven't installed any additional repositories. I have installed packages like Firefox, Skype, OpenShot Video Editor, and OpenJDK. I also installed then uninstalled some other packages like Opera and a couple of games.

---

### Post by linuxinstalledfromhdd on 2011-06-01
In terminal, type:

sudo apt-get update

Can you cut and paste the result please?

---

### Post by Clex19 on 2011-06-01
Here is the result:

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
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
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by linuxinstalledfromhdd on 2011-06-01
> **Clex19 said:**
> Here is the result:

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
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
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

First make sure that update-manager, synaptic, etc... are all closed and not running somewhere.
 Then open a Terminal and enter the following commands:
 sudo mkdir /var/lib/apt/lists/partial
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f

---

### Post by Clex19 on 2011-06-01
Result of the first command:

mkdir: cannot create directory `/var/lib/apt/lists/partial': File exists

The second command didn't have a displayed result.

Result of the other three commands:

sudo: apititude: command not found

---

### Post by linuxinstalledfromhdd on 2011-06-01
Bump

---

### Post by Clex19 on 2011-06-01
I don't know if this will help, but I clicked the red icon and selected "Show updates". That opened the Update Manager and then a window that said: 

"Could not initialize the package information. An unresolvable problem occurred while initializing the package information. Please report this bug against the 'update-manager' package and include the following error message: 'E:Read error - read (5:Input/output error),E:The package lists or status file could not be parsed or opened.'"

How do I "report this bug against the 'update-manager' package," etc.?

---

### Post by no2498 on 2011-06-01
can you close the  red icon
thats part of your problem its like having two terminal's open at the same time
retry the codes they give you in a terminal

---

### Post by Clex19 on 2011-06-01
@no2498

I don't know how to close the red icon at all. 

If I right-click it, a menu appears, and all it says is "Show updates," "Install all updates," "Check for updates," "Start package manager," "Show notifications," and "Preferences." The options with "updates" all open the Update Manager, which just gives the error from my previous post. "Start package manger" gives an error message with the Synaptic Package Manager. "Show notifications" doesn't do anything. "Preferences" just gives options for the software sources, not the red icon itself. 

And if I left-click the red icon, it just opens up Update Manager with that same error message.

I just tried rebooting, and it took A LOT longer than it usually does (almost 10 ten minutes, instead of one or two).

---

### Post by Clex19 on 2011-06-01
Okay, I figured out how to get rid of the red icon! I followed the steps that sikander3786 gave here [http://ubuntuforums.org/showthread.php?t=1642574](http://ubuntuforums.org/showthread.php?t=1642574) which were:

```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

sudo apt-get update

```

Now my question is did this permanently fix the error? Is the error likely to happen again, and is there a way to prevent it from happening again?

---

