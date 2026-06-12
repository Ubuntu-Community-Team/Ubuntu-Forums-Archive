---
title: "Sources.list file is missing"
date: 2009-09-20
forum: General Help
---

### Post by hubertofliege on 2009-09-20
I have been having problems updating my system for the last two weeks.  I solved part of the problem (I updated my public keys), however I am still stuck with three error messages:

(GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
Some index files failed to download, they have been ignored, or old ones used instead.)

I was working toward a solution, however today I lost my sources.list file.  When I open it in the terminal, its blank and if I try to rewrite it or save anything in the file, it reports that the file is missing and can't be saved.  When I go into synaptic package manager I can find a list of repositories, but I can't open or modify my missing sources.list file.  Please help.

---

### Post by oldos2er on 2009-09-20
Try [http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php) to generate a new sources.list.

---

### Post by hubertofliege on 2009-09-21
Thank you, but the problem isn't that I don't have the repository data, its that I cannot find or modify the FILE, "sources.list".  When I open it through the terminal, its blank, and if I try and save something to it, it says that the file can't be found or rewritten.  I still have a bunch of repositories in my sources menu under "System", so I think the file is just inaccessible.  This feels like a pretty big problem.  Does anyone know how I can gain access to my sources.list file, or at least write a new one?  If I write a new one, I need to actually create a new file.  I have the sources themselves saved, I just can't alter the missing file.

---

### Post by drs305 on 2009-09-21
Are you trying to open it as root, and are you sure you have the proper path and spelling:
```

gksudo gedit /etc/apt/sources.list

```

Since it is a system file, you won't be able to save any changes unless you are editing it as 'root'. Opening it with the above command will allow you to edit the file if sources.list is in the standard location (/etc/apt/).

---

### Post by sisco311 on 2009-09-21
to edit the file:
```
gksu gedit /etc/apt/sources.list
```

this is the content of the default sources.list:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://archive.ubuntu.com/ubuntu/ jaunty universe                      
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe                  
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe              
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe          

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse                     
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse                 
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse             
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse         

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
# deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
# deb http://archive.canonical.com/ubuntu jaunty partner                 
# deb-src http://archive.canonical.com/ubuntu jaunty partner             

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe           
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe       
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse         
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
```

---

### Post by pastalavista on 2009-09-21
The file is located in /etc/apt/sources.list.

You need to be root to edit it. Use this command in terminal...```
gksu gedit /etc/apt/sources.list
```

To install pubkey for repository use this in terminal

```
gpg --keyserver keyserver.ubuntu.com --recv DCF9F87B6DFBCBAE
gpg --export --armor DCF9F87B6DFBCBAE | sudo apt-key add -
```

---

### Post by hubertofliege on 2009-09-21
Okay, I figured it out, I think.  I followed the instructions in the second post of this thread:
[http://ubuntuforums.org/showthread.php?t=863216](http://ubuntuforums.org/showthread.php?t=863216)

(1) find out the permissions on the sources.list
 	Code:
 	ls -al /etc/apt/sources.list 
(2) move the sources.list
 	Code:
 	sudo mv /etc/apt/sources.list /etc/apt/sources.list.org 
(3) create an empty one
 	Code:
 	sudo touch /etc/apt/sources.list 
(4) set correct permissions
 	Code:
 	sudo chmod 0644 /etc/apt/sources.list


Then I repopulated the list using a backup copy.  Can anyone shed some light on what this means, and if the problem is fixed?  I hate not fully understanding things that I do to my computer.

---

