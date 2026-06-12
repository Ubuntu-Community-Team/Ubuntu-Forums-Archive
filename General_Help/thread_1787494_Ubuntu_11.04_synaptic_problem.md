---
title: "Ubuntu 11.04 synaptic problem"
date: 2011-06-21
forum: General Help
---

### Post by bolkonski on 2011-06-21
Hi Guys,
I upgraded from 10.4 to 11.04 but have no access to sftware center or synaptic manager. I admit I did play around with gedit and removed the last 8 lines leaving the text at the bottom of this message. Unsuccessful as you can see. I screwed up. I hope someone out there can help me with this nightmare. Appreciate any help you can give.
Regards
bolkonski

When typing the text below I received the Answer:
                                 

Terminal: sudo gedit /etc/apt/sources.list
 

 Answer:
 (gedit:8177): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.P44KXV': No such file or directory 
  
 (gedit:8177): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 
 

 

 

 

 

 This is text from terminal 2 days ago:
 # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted 
 # deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
 deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty main restricted 
 deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
 deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty universe 
 deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty universe 
 deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-updates universe 
 deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty multiverse 
 deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty multiverse 
 deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
 deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-updates multiverse 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
 # deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner 
 # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main 
 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main 
 deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) natty 
 deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) natty 
 deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) natty 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
  
 ## Uncomment the following two lines to add software from the 'backports' 
 ## repository. 
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 # deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse 
 # deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

---

### Post by coffeecat on 2011-06-21
> **bolkonski said:**
> 
When typing the text below I received the Answer:
                                 
Terminal: sudo gedit /etc/apt/sources.list
 
 Answer:
 (gedit:8177): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.P44KXV': No such file or directory 
  
 (gedit:8177): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 

You are not alone:
 
```
$ sudo gedit /etc/apt/sources.list
[sudo] password for coffeecat: 

(gedit:3339): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.85ONXV': No such file or directory

(gedit:3339): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3339): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BYXGXV': No such file or directory

(gedit:3339): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```Ignore those messages - it will not prevent you from running gedit as the administrator. However, you should be using gksudo, not sudo for graphical apps. See:

[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)

You will still see those blood-curdling messages:

```
$ gksudo gedit /etc/apt/sources.list

(gedit:3353): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.LA5JXV': No such file or directory

(gedit:3353): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```Again - ignore them.

But to your sources.list. I can't see anything wrong in it, but I may have missed something. What were you trying to change? Run this from a terminal and post the output:

```
sudo apt-get update
```What happens when you try to open Synaptic or Software Centre?

---

### Post by Beacon11 on 2011-06-21
bolkonski, you say you don't have access to the software center or synaptic, but then you go on to talk about your sources. Could you please clarify? What happens when you try to run software center or synaptic?

EDIT: Dangit coffeecat, you beat me.

---

### Post by bolkonski on 2011-06-21
Hi 
This is what I get when I write sudo apt-get update

E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
The error 

E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
comes up when trying to get into synaptic package manager and the software center doesn't load. Thewheel keeps turning so to speak.Thanks for your help
bolkonski

---

### Post by Beacon11 on 2011-06-21
Alright, that helps a lot. It may have a problem with your geekconnection.org repos. Take a look at [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html) and [http://www.geekconnection.org/remastersys/repository/](http://www.geekconnection.org/remastersys/repository/) and notice there doesn't seem to be an option for natty. Try either using karmic or commenting those repos out, and see what happens.

---

### Post by bolkonski on 2011-06-21
Hi Beacon11 and Coffeecat,
I've done everything  from the terminal so far- through ignorance. In the script I was trying to change the last few lines thinking I was eliminating unneccessary commands. The script looked identical to mine (I saw this on another thread) so I took the advice and eliminated it in gedit.
Regards
bolkonski

---

### Post by Beacon11 on 2011-06-21
Oh that's okay-- real Linux users use the terminal! Are you saying eliminating the geekconnection.org repos fixed the problem?

Edit: Oops, we're just posting at the same time :P

---

### Post by bolkonski on 2011-06-21
Thanks Beacon11,
I'll try that
Bolkonski

---

### Post by bolkonski on 2011-06-21
"...geekconnection.org repos fixed the problem?"
I'm afraid I don't know how to go about it!
I 'm in a maze of imformation that I can't process. Could you please treat me like a real dummy.
bolkonski

---

### Post by Beacon11 on 2011-06-21
Haha, don't feel like a dummy! This stuff takes a while to get used to. Okay, answer a couple questions for me. If I have the right idea, you've really been messing with /etc/apt/sources.list, correct? Is there any particular reason why?

---

### Post by bolkonski on 2011-06-21
yes, i have out of desperation

---

### Post by Beacon11 on 2011-06-21
> **bolkonski said:**
> yes, i have out of desperation

Trying to fix this very problem, you mean? Okay, then I would try reverting back to a necessities-only sources.list. I'll generate one for you if you can tell me the country you're presently in.

---

### Post by bolkonski on 2011-06-21
[Hi Beacon11]("http://ubuntuforums.org/member.php?u=441287")
I'm in Spain. 
Thanks for your help.
bolkonski

---

### Post by Beacon11 on 2011-06-21
Hey my pleasure.

Okay, first of all, make a backup of your current sources.list:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

Now, open your sources.list in whatever editor you like; to use gedit, do

```
gksudo gedit /etc/apt/sources.list
```

Now delete everything in there, and paste this in:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://es.archive.ubuntu.com/ubuntu/ natty main restricted universe multiverse 
deb-src http://es.archive.ubuntu.com/ubuntu/ natty main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://es.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse 
deb http://es.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse 
deb-src http://es.archive.ubuntu.com/ubuntu/ natty-security main restricted universe multiverse 
deb-src http://es.archive.ubuntu.com/ubuntu/ natty-updates main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner
```

Now, try running update again:

```
sudo apt-get update
```

EDIT: By the way, in case you would rather not blindly trust me ( ;) ), I used the generator at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) .

---

### Post by bolkonski on 2011-06-21
Beacon11,
Brilliant man. I have full access to synaptic package manager and software center. 
There was this right at the foot of the text. Should I worry?:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Anyway, you've saved my bacon. You've earned a san fermin night out here in Pamplona.
Best regards 
bolkonski

---

### Post by Beacon11 on 2011-06-21
> **bolkonski said:**
> ... NO_PUBKEY 2EBC26B60C5A2783...

Glad I could help! As for the key issue, try this:

```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
```

Followed by this:

```
gpg &#8211;-export &#8211;-armor 2EBC26B60C5A2783 | sudo apt-key add -
```

EDIT: Note that the hyphen at the end of the last command is not a typo.

EDIT 2: This post has been updated to fix a typo in the last command.

---

### Post by bolkonski on 2011-06-21
Hi Beacon11
Here's the text I got;
steve@steve-MS-7366:~$ gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
steve@steve-MS-7366:~$ gpg –export –armor 2EBC26B60C5A2783 | sudo apt-key add -
usage: gpg [options] [filename]
Is that finalised?
bolkonski

---

### Post by Beacon11 on 2011-06-21
Agh, no, because I can't type. The first step was good, but the second step needs to be this:

```
gpg &#8211;-export &#8211;-armor 2EBC26B60C5A2783 | sudo apt-key add -
```

(note the double-hyphens). Sorry! Then try updating again as before.

EDIT: Note that post 16 has been updated to be correct.

---

### Post by bolkonski on 2011-06-21
Beaccon11 
I got this after entering your code.
usage: gpg [options] [filename]
gpg: no valid OpenPGP data found.
bolkonski

---

### Post by Beacon11 on 2011-06-21
Hmm... you ran the two commands one after the other?

---

### Post by bolkonski on 2011-06-21
yep .afraid I did.

---

### Post by Beacon11 on 2011-06-21
Well shoot, I was looking so good. Referring to Google, I've got [http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/](http://www.thegeekstuff.com/2009/05/apt-get-update-how-to-solve-no-public-key-available/) . The only difference between what they've got and what I've got is that they turned recv into recv-keys. Try that (given below with your key and Ubuntu's key server):

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg --armor --export 2EBC26B60C5A2783 | sudo apt-key add -
sudo apt-get update
```

EDIT: You should probably use Ubuntu's key server, so I changed it slightly.

---

### Post by bolkonski on 2011-06-21
Beacon11,

gave following
steve@steve-MS-7366:~$ $ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys [key]
$: command not found
steve@steve-MS-7366:~$ $ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys
$: command not found
steve@steve-MS-7366:~$ $ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys
$: command not found
steve@steve-MS-7366:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys
steve@steve-MS-7366:~$ gpg --armor --export [key] | apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
steve@steve-MS-7366:~$ OK
OK: command not found
steve@steve-MS-7366:~$ apt-get update

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bolkonski

---

### Post by Beacon11 on 2011-06-21
> **bolkonski said:**
> steve@steve-MS-7366:~$ $ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys [key]

Hahaha, I'm sorry, I meant the [key] to be a placeholder-- I just updated the comment; check it out again.

---

### Post by bolkonski on 2011-06-21
Beacon11
Her's the reply:
steve@steve-MS-7366:~$ gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
steve@steve-MS-7366:~$ gpg --armor --export 2EBC26B60C5A2783 | apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
steve@steve-MS-7366:~$ sudo apt-get update
bolkonski

---

### Post by Beacon11 on 2011-06-21
> **bolkonski said:**
> 
steve@steve-MS-7366:~$ gpg --armor --export 2EBC26B60C5A2783 | apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
steve@steve-MS-7366:~$ sudo apt-get update

Oh so close! I updated the post one last time (I'm telling you, it'll work now).

---

### Post by bolkonski on 2011-06-21
Beacon11
It gave this:
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Is this ok?
bolkonski

---

### Post by Beacon11 on 2011-06-21
Run all three commands again and paste the output here please.

---

### Post by bolkonski on 2011-06-21
beacon11,
Could this be it? 
steve@steve-MS-7366:~$ gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
steve@steve-MS-7366:~$ gpg --armor --export 2EBC26B60C5A2783 | sudo apt-key add -
OK
bolkonski

---

### Post by Beacon11 on 2011-06-21
Yeah that looks like it finally worked correctly. But when you run ```
sudo apt-get update
``` you still get complaints about NO_PUBKEY?

---

### Post by bolkonski on 2011-06-21
beacon11
here's the full text: I can't see any key queries.

steve@steve-MS-7366:~$ sudo apt-get update
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty InRelease
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security InRelease           
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates InRelease             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release.gpg          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release                         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Sources                            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Sources              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Sources         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Sources   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Sources               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Sources             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main i386 Packages   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe i386 Packages         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse i386 Packages       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main TranslationIndex          
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse TranslationIndex    
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted TranslationIndex    
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,092 B]
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en
Fetched 1 B in 4s (0 B/s)
Reading package lists... Done
steve@steve-MS-7366:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security InRelease                      
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates InRelease             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release.gpg                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release.gpg                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release.gpg                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release                         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Sources                            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Sources              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Sources 
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main i386 Packages 
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Sources             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main i386 Packages             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted i386 Packages       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe i386 Packages         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse i386 Packages       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Tsteve@steve-MS-7366:~$ sudo apt-get update
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty InRelease
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security InRelease           
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates InRelease             
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release.gpg          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release                         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Sources                            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Sources              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Sources         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Sources   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Sources               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Sources             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main i386 Packages   
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe i386 Packages         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse i386 Packages       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main TranslationIndex          
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse TranslationIndex    
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted TranslationIndex    
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main i386 Packages    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main TranslationIndex 
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,092 B]
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en
Fetched 1 B in 4s (0 B/s)
Reading package lists... Done
steve@steve-MS-7366:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease                   
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty InRelease                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security InRelease                      
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates InRelease             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free i386 Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free i386 Packages       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release.gpg                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release.gpg                    
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release.gpg                     
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security Release                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates Release                         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Sources                            
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Sources                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Sources              
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Sources 
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main i386 Packages 
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Sources             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main i386 Packages             
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted i386 Packages       
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe i386 Packages         
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse i386 Packages       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_US             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
ranslation-en_US             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Sources
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-security/universe Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) natty-updates/universe Translation-en
Reading package lists... Done
cautiously optimistic 
regards
bolonski

---

### Post by Beacon11 on 2011-06-21
Ah! That looks more like it; I declare you fixed. Sorry that took so long :) .

---

### Post by bolkonski on 2011-06-21
Beacon11,
Thanks fro your time and effort I really appreciate it. The San Fermin thing still stands,
Best regards
bolkonski

---

### Post by Beacon11 on 2011-06-22
Hey no problem. Maybe I'll take you up on that one day ;) .

---

