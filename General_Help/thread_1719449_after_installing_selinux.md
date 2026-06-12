---
title: "after installing selinux"
date: 2011-04-01
forum: General Help
---

### Post by fadi hamadneh on 2011-04-01
Hi All,

I am Using Ubuntu 10.04 LTS 
everything was ok and i didn't face any problems, 
i am new in ubuntu ... i began using it since 1 year only .. 
Yesterday a friend of me told me that the package (selinux) is very important and must be installed in my laptop,
So i did what he said and installed it ... the system asked me to reboot .. i did .. and it took a long time rebooting with the message ( Relabeling Files) then it rebooted ,,
after that i noticed many strange things in my system .. such as : my update manager started to download package information , but many of them FAILED with the message : Authentication Failure.. 
I pasted this from the error box: 

[COLOR=Red]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

[COLOR=Black]I dont know what to do .. please help me in this issue ..:( 
thank you in advance 
waiting your replies
Fadi Hamadneh
[/COLOR]

---

### Post by 3Miro on 2011-04-01
Did you ask your friend what exactly did SELinux does?

SELinux provides many security enchantments, however, under Ubuntu those are handled by AppArmor (I guess 8.04 used SELinux, but now everything is AppArmor). Installing SELinux is far from a trivial task.

If I were you I would try to reinstall apparmor and apparmor-utils:
```
sudo apt-get install apparmor apparmor-utils
```
I hope this will remove SELinux and replace it with the default Ubuntu AppArmor, however, I don't know if this would work. I don't know enough about those two to mess with them.

General advice: use Google and read the package description as well as what it installs and removes. I am especially weary if a program would conflict with something current and replace it with something new, if I see that, then I double and triple check.

---

### Post by fadi hamadneh on 2011-04-01
> **3Miro said:**
> Did you ask your friend what exactly did SELinux does?

SELinux provides many security enchantments, however, under Ubuntu those are handled by AppArmor (I guess 8.04 used SELinux, but now everything is AppArmor). Installing SELinux is far from a trivial task.

If I were you I would try to reinstall apparmor and apparmor-utils:
```
sudo apt-get install apparmor apparmor-utils
```I hope this will remove SELinux and replace it with the default Ubuntu AppArmor, however, I don't know if this would work. I don't know enough about those two to mess with them.

General advice: use Google and read the package description as well as what it installs and removes. I am especially weary if a program would conflict with something current and replace it with something new, if I see that, then I double and triple check.

Thank you for your replyy :) i am afraid to make your command ... maybe it will remove applications ... i dont know what to do .. i need a more accurate answer ... and thank you again man ...

---

### Post by 3Miro on 2011-04-01
> **fadi hamadneh said:**
> Thank you for your replyy :) i am afraid to make your command ... maybe it will remove applications ... i dont know what to do .. i need a more accurate answer ... and thank you again man ...

I would wait for a second opinion on the whole issue, I am not 100% sure this would help.

sudo is a command that executes the following commands with administrative privileges. Changing system files and installing new software requires root/administrative privileges. 

apt-get is the command that manipulates software. apt-get install installs new programs, apt-get remove removes them (there is also apt-get purge that deletes config files)

```
sudo apt-get install some_program
```
this command installs software under Ubuntu. It is generally a safe command, however, it will first give you a list of things that it will do and then asks you whether or not to do them. Adding things should be fine, however, ask someone before you remove something.

apparmor is the default security program for Ubuntu (apparmor-utils goes with it).

My command is supposed to install apparmor back on your machine (in the process it should remove SELinux and basically restore everything back to where it was). However, I don't know enough about those two to be 100% sure.

You can also use Synaptic Package Manager to do the same thing as apt-get. You can try installing apparmor and apparmor-utils from there.

---

### Post by fadi hamadneh on 2011-04-02
another Problem happened :( :( 
when i try to open synaptic package manager
i get this error

[COLOR=Red]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/COLOR]


PLEASE HELP ME .. i want my ubutnu work well as before :( :(

---

### Post by jerome1232 on 2011-04-02
It's telling you what to do right in the error.


run that command it gives you.

```
sudo dpkg --configure -a
```

I don't have a clue how to fix your problem with having installed selinux.

---

### Post by fadi hamadneh on 2011-04-02
when i do : sudo apt-get update

the following error appear

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5

---

### Post by AlexDudko on 2011-04-02
Try to execute
> setenforce 0
in terminal (as root).
After that see if the problem exists. If everything's fine then set > SELINUX=disabled
in /etc/selinux/config This will disable SELinux in your system.
After that read more about SELinux and only then try to re-enable it.

P.S.  This error:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5
tells that you might have problems with your application sources.

---

### Post by ugm6hr on 2011-04-02
> **AlexDudko said:**
> tells that you might have problems with your application sources.

Judging by the output, you have mixed lucid and karmic repositories.
Have a look at your list of repositories (in Synaptic package manager) to see what is going on.
If you don't know what you're looking for - paste the contents here:
```
gedit /etc/apt/sources.list
```
Once this is resolved, we can try and sort the rest.

---

### Post by fadi hamadneh on 2011-04-02
> **ugm6hr said:**
> Judging by the output, you have mixed lucid and karmic repositories.
Have a look at your list of repositories (in Synaptic package manager) to see what is going on.
If you don't know what you're looking for - paste the contents here:
```
gedit /etc/apt/sources.list
```Once this is resolved, we can try and sort the rest.

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) lucid universe
# deb [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
# deb-src [http://blognux.free.fr/ubuntu](http://blognux.free.fr/ubuntu) hardy main
deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps

---

### Post by AlexDudko on 2011-04-02
Comment out these lines:
> deb [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bean123ch/burg/ubuntu](http://ppa.launchpad.net/bean123ch/burg/ubuntu) karmic main
and run
> apt-get update

---

### Post by HermanAB on 2011-04-02
Howdy,

SELinux is integrated with Red Hat Linux distros.  There are no decent SE Linux configuration tools on Ubuntu.

App Armor is integrated with Ubuntu.  So, you would do best by disabling SE Linux for now and one day when you re-install Ubuntu, select App Armor.  

Note that trying to remove SE Linux is probably not worth the effort - just disable it and reboot.

---

### Post by fadi hamadneh on 2011-04-02
> **AlexDudko said:**
> Comment out these lines:

and run

sorry .. :S but i am not professional in ubuntu ... 
what do u mean by comment out .. 
please describe for me what to do .. 
i'll be thankful

---

### Post by fadi hamadneh on 2011-04-02
> **HermanAB said:**
> Howdy,

SELinux is integrated with Red Hat Linux distros.  There are no decent SE Linux configuration tools on Ubuntu.

App Armor is integrated with Ubuntu.  So, you would do best by disabling SE Linux for now and one day when you re-install Ubuntu, select App Armor.  

Note that trying to remove SE Linux is probably not worth the effort - just disable it and reboot.

how to disable SE Linux??? 
please give it to me step by step

---

### Post by AlexDudko on 2011-04-02
> **HermanAB said:**
> Howdy,

SELinux is integrated with Red Hat Linux distros.  There are no decent SE Linux configuration tools on Ubuntu.


SELinux is a very good security tool for Linux. It IS integrated in the majority of modern distro's, not only Red Hat based. I personally use it in Debian but it's true it hasn't decent GUI configuration tools in both Debian and Ubuntu. And the "default" policy demands a lot  of command-line tweaking and customization.

---

### Post by AlexDudko on 2011-04-02
> **fadi hamadneh said:**
> sorry .. :S but i am not professional in ubuntu ... 
what do u mean by comment out .. 
please describe for me what to do .. 
i'll be thankful

Put "#" sign (without quotation marks, of course!) at  the beginning of the lines mentioned above. Or simply delete them from the file (sources.list).

---

### Post by ugm6hr on 2011-04-02
> **fadi hamadneh said:**
> sorry .. :S but i am not professional in ubuntu ... 
what do u mean by comment out .. 
please describe for me what to do .. 
i'll be thankful

```
gksudo gedit /etc/apt/sources.list
```
Just add a # symbol at the start of those 2 lines, and then save file.

---

### Post by AlexDudko on 2011-04-02
> **fadi hamadneh said:**
> how to disable SE Linux??? 
please give it to me step by step

To disable  SELinux temporarily run in terminal (as root, of course!):
> setenforce 0 


To disable it permanently edit /etc/selinux/config
and change the line:
> SELINUX=enforcing
to 
> SELINUX=disabled

---

### Post by fadi hamadneh on 2011-04-02
> **ugm6hr said:**
> ```
gksudo gedit /etc/apt/sources.list
```Just add a # symbol at the start of those 2 lines, and then save file.

i got this output from sudo apt-get update

[COLOR=Red]root@fadi-admin-laptop:/home/fadi-admin# sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                                                                                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                              
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) lucid/main Translation-en_US                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                                                                                              
Ign [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/) lucid/main Translation-en_US                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                                                                         
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                                                                              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                                                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                                                                                                    
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy Release.gpg                                                                                                                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                                                                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                                                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources                                           
Get:1 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg [836B]                      
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US                                               
Ign [http://blognux.free.fr/ubuntu/](http://blognux.free.fr/ubuntu/) hardy/main Translation-en_US                          
Get:2 [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release [7,240B]                                  
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                                                                      
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy Release                                                                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                             
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages                                           
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid Release.gpg             
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid Release
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates Release
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/main Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/main Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/universe Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/universe Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/restricted Packages       
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/main Sources              
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/restricted Sources        
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/universe Packages                                                                                            
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/universe Sources                                                                                             
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/multiverse Packages                                                                                          
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/multiverse Sources                                                                                           
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Sources                                                                                                               
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages                                                                                                              
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Sources                                                                                                               
Hit [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages                                                                                                              
Hit [http://blognux.free.fr](http://blognux.free.fr) hardy/main Sources
Fetched 837B in 13s (62B/s)
Reading package lists... Done
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF[/COLOR]

---

### Post by AlexDudko on 2011-04-02
Comment/remove those repositories (getdeb) as well.

---

### Post by fadi hamadneh on 2011-04-02
> **AlexDudko said:**
> Comment/remove those repositories (getdeb) as well.

i did .. and this is the new output:
[COLOR=Red]
fadi-admin@fadi-admin-laptop:~$ sudo apt-get update
[sudo] password for fadi-admin: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/s-lagui/ppa/ubuntu/](http://ppa.launchpad.net/s-lagui/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy Release.gpg                                   
Ign [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ps.archive.ubuntu.com/ubuntu/](http://ps.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/main Packages                 
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/main Sources                  
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/restricted Sources            
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/universe Packages             
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://ps.archive.ubuntu.com](http://ps.archive.ubuntu.com) lucid-updates/multiverse Sources        
Ign [http://blognux.free.fr/ubuntu/](http://blognux.free.fr/ubuntu/) hardy/main Translation-en_US          
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy Release           
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages     
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Sources      
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages     
Ign [http://blognux.free.fr](http://blognux.free.fr) hardy/main Sources      
Hit [http://blognux.free.fr](http://blognux.free.fr) hardy/main Packages     
Hit [http://blognux.free.fr](http://blognux.free.fr) hardy/main Sources      
Reading package lists... Done
fadi-admin@fadi-admin-laptop:~$ [/COLOR]

is this output means everything is ook???
and what is meant by Hit and Ign??? 
thank you very much

---

### Post by AlexDudko on 2011-04-02
Hit means that your local file is identical to the downloaded one.
Ign (ignore) means that the repository is ignored.

Now run:
> apt-get upgrade
and you'll have your system up-to-date.

---

### Post by 3Miro on 2011-04-02
The commands are:
```
sudo apt-get update
```
which downloads new information about all available programs and
```
sudo apt-get upgrade
```
which downloads the latest versions of those programs (and updates your system).

- Unless you are willing to read manuals on how to proprely setup SELinux, you should remove it and reinstall AppArmor (see my earlier posts about it). A machine is improperly set SELinux is less secure than one with properly set AppArmor.

- You are very careful about the commands that we tell you to run, which a good thing, however, it seems that you have already done quite a few things without asking proper questions. Unless you know what you are doing, don't install programs outside of the standard Ubuntu repository (i.e. don't add extra stuff, especially if they are for the wrong version of Ubuntu).

---

### Post by fadi hamadneh on 2011-04-02
> **3Miro said:**
> The commands are:
```
sudo apt-get update
```which downloads new information about all available programs and
```
sudo apt-get upgrade
```which downloads the latest versions of those programs (and updates your system).

- Unless you are willing to read manuals on how to proprely setup SELinux, you should remove it and reinstall AppArmor (see my earlier posts about it). A machine is improperly set SELinux is less secure than one with properly set AppArmor.

- You are very careful about the commands that we tell you to run, which a good thing, however, it seems that you have already done quite a few things without asking proper questions. Unless you know what you are doing, don't install programs outside of the standard Ubuntu repository (i.e. don't add extra stuff, especially if they are for the wrong version of Ubuntu).

Thanks for your advice i will be careful in the future

---

### Post by fadi hamadneh on 2011-04-02
> **AlexDudko said:**
> Hit means that your local file is identical to the downloaded one.
Ign (ignore) means that the repository is ignored.

Now run:

and you'll have your system up-to-date.

AlexDudko ... Thank you dude :D :D :D i am very thankful .. you solved my problem 
you rock! :D

---

