---
title: "Linux images and other install fails."
date: 2010-10-12
forum: General Help
---

### Post by jameshampshire on 2010-10-12
No matter what i want to install no matter how big or small the package.
I am constantly bombarded with annoying error messages that stop me in my tracks and will NOT let me do anything to my computer or install anything.
Here's some of them


E: linux-image-2.6.32-24-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-24-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-25-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-25-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured


And other error messages and such that i can't copy and paste because its a synaptic package manager install error saying basically the same thing with like maxreports reached etc etc.

Someone please reply to me urgently i really do need urgent help if possible.
Thank you.

---

### Post by Gavin77 on 2010-10-12
Open a terminal and try these one at a time:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by jameshampshire on 2010-10-12
james@james-desktop:~/Documents$ 
james@james-desktop:~/Documents$ sudo apt-get update
[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg                           
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper/free Translation-en_AU               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources                    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper/non-free Translation-en_AU           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg                           
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty/free Translation-en_AU               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty/non-free Translation-en_AU           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_AU               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_AU           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_AU      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_AU            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release                               
Ign [http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/](http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid/multiverse Translation-en_AU    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Reading package lists... Done
james@james-desktop:~/Documents$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
james@james-desktop:~/Documents$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
james@james-desktop:~/Documents$ 



still no dice.

---

### Post by Gavin77 on 2010-10-12
Make sure you close Synaptic before you use apt-get in the terminal.  They can't run at the same time.

---

### Post by jameshampshire on 2010-10-12
Yeah it was closed when i did that.
Same error shows up when i sudo su and then do that.
Whatever i try to install or you know with updates and stuff too they always fail at the end because of the same old remove linux-image-2.6.32-24-generic error message.
I tried uninstalling it and i got an error message. then it showed up as uninstalled.
but its still not letting me do nothing.

---

### Post by jameshampshire on 2010-10-12
I also tried EVERYTHING that was offered in this thread and it did nothing.

[http://ubuntuforums.org/showthread.php?t=1578513](http://ubuntuforums.org/showthread.php?t=1578513)

---

### Post by Gavin77 on 2010-10-12
I notice that your sources list seems to have a mix of distros.. lucid, dapper, intrepid etc.  

Try going into synaptic and click on Settings - Repositories - Other Software and uncheck everything other than the lucid ones then click reload. See if it makes any difference.

---

### Post by jameshampshire on 2010-10-12
Sorry but also when i open synaptic package manager i get this error message [B]W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
[/B]

I don't know if it helps


Tried just installing something for the hell of it again.
And got this:

E: linux-image-2.6.32-24-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-25-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured


This has been going on for a long time.
I really need valid help. Ubuntu is starting to really get me down.

---

### Post by jameshampshire on 2010-10-12
I did that then and the same deal say i tried to install kdm theme manager which i am.

i get 

E: linux-image-2.6.32-24-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.32-25-generic-pae: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic-pae: dependency problems - leaving unconfigured
E: linux-generic-pae: dependency problems - leaving unconfigured

and the same deal happens with everything else i try to install.
:(

---

### Post by Gavin77 on 2010-10-12
In synaptic, try Edit... Fix Broken Packages.
If that doesn't work I'm not sure what to try as I'm no expert.

---

### Post by jameshampshire on 2010-10-12
Didn't work mate, thanks for trying anyway.
Still bumping for help.

---

### Post by jameshampshire on 2010-10-12
Bumping

---

### Post by jameshampshire on 2010-10-12
Ok I read on other forums it could be a graphics related problem so I tried this and got this.


james@james-desktop:~/Documents$ sudo apt-get remove nvidia-common
[sudo] password for james: 
Sorry, try again.
[sudo] password for james: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
james@james-desktop:~/Documents$ sudo su
root@james-desktop:/home/james/Documents# sudo apt-get remove nvidia-common
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@james-desktop:/home/james/Documents# sudo apt-get purge nvidia-common
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@james-desktop:/home/james/Documents# ^C
root@james-desktop:/home/james/Documents# sudo apt-get remove nvidia-commonReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-common
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 184kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 314478 files and directories currently installed.)
Removing nvidia-common ...
Setting up linux-image-2.6.32-24-generic-pae (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@james-desktop:/home/james/Documents# sudo apt-get install nvidia-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/13.9kB of archives.
After this operation, 184kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package nvidia-common.
(Reading database ... 314458 files and directories currently installed.)
Unpacking nvidia-common (from .../nvidia-common_0.2.23_i386.deb) ...
Setting up linux-image-2.6.32-24-generic-pae (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-common (0.2.23) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already

Processing triggers for python-central ...
Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@james-desktop:/home/james/Documents# apt-get update
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release.gpg
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_AU          
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_AU    
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_AU  
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_AU
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates Release                         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Packages                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/main Sources                            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/](http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_AU                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_AU   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_AU       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Packages               
Ign [http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/](http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_AU
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_AU
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_AU
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages [8,588B]
Fetched 15.6kB in 4s (3,130B/s)   
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



Obviously as you can see running apt-get update will do exactly what is shown above.

Need help!

---

### Post by jameshampshire on 2010-10-12
Here is something else I tried.


james@james-desktop:~/Documents$ aptitude reinstall util-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
james@james-desktop:~/Documents$ sudo aptitude reinstall util-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  util-linux 
The following partially installed packages will be configured:
  linux-generic-pae linux-image-2.6.32-24-generic-pae linux-image-2.6.32-25-generic-pae linux-image-generic-pae 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 532kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid/main util-linux 2.17.2-0ubuntu1 [532kB]
Fetched 532kB in 1min 12s (7,314B/s)                                                                                         
(Reading database ... 314387 files and directories currently installed.)
Preparing to replace util-linux 2.17.2-0ubuntu1 (using .../util-linux_2.17.2-0ubuntu1_i386.deb) ...
Unpacking replacement util-linux ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Setting up util-linux (2.17.2-0ubuntu1) ...

Setting up linux-image-2.6.32-24-generic-pae (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                           Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-24-generic-pae (2.6.32-24.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic-pae
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-24-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-25-generic-pae (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 28: Syntax error: EOF in backquote substitution
User postinst hook script [/usr/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.32-25-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-25-generic-pae; however:
  Package linux-image-2.6.32-25-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.25.27); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-24-generic-pae
 linux-image-2.6.32-25-generic-pae
 linux-image-generic-pae
 linux-generic-pae
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

james@james-desktop:~/Documents$

---

### Post by jameshampshire on 2010-10-13
Bumping.

---

### Post by jameshampshire on 2010-10-13
Don't know how to change what linux version i'm talking about.
But this doesn't work on Ubuntu, Kubuntu + the rest i have installed.
So all ubuntu versions.

---

