---
title: "Update and Add Remove won't open"
date: 2010-02-10
forum: General Help
---

### Post by HappyOm on 2010-02-10
Hey friends, I have been so reluctant to actually make an account and after hours and hours and hours of searching and getting pieces of help here and there, google is out of answers. I present you with my situation:

I am working on a compaq laptop that has a tricked out version of Super Ubuntu (of Jaunty 9.04) installed on it in June. I got acquainted with it but left it behind to travel in August and regained it in November, with a couple brief uses of it passing through. Somewhere along the line I got a bad crash related to a hibernate issue or an update that screwed me and Ubuntu wouldn't load anymore. Eventually I figured out it was prompting me to type certain code and finally loaded again. Once loaded, I began to continue personalizing it and realized** that Add/Remove would no longer open, it would just say "Starting add/remove..." in the taskbar and disappear after a few seconds. Then I relized the update manager wasn't opening either** and I occassionally would get a wierd Opera related error ( i put on another broswer so I could have dual login for my partner and I in facebook/yahoo etc.. and could care less about opera, but it has caused problems.

Working with google and the terminal, I did some things to fix missing keys, lowering my error count, and tried to fix python by reinstalling it, but it doesn't seem to be broken yet shows up in some error. I have this silly error remaining that no one has written about "GPG error: [http://hacktolive.org](http://hacktolive.org) jaunty Release : The following signatures were invalid: KEYEXPIRED 1265785910 KEYEXPIRED 1265785910 KEYEXPIRED 1265785910"  that shows up with sudo apt-get update  and other errors. Still no use of update manager, add-remove, or access to the repositories in either the software sources area or through synaptic (though synaptic seems to work in its most basic sense, defying the administrative errors.)  



Here are a couple code entries in full with their errors:

[I]sudo apt-get update

Get:1 [http://hacktolive.org](http://hacktolive.org) jaunty Release.gpg [197B]
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/main Translation-en_US                        
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/restricted Translation-en_US                  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/multiverse Translation-en_US                  
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/universe Translation-en_US                    
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/partner Translation-en_US                     
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_US                      
Hit [http://hacktolive.org](http://hacktolive.org) jaunty Release                                       
Ign [http://hacktolive.org](http://hacktolive.org) jaunty Release                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US 
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/main Packages                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/restricted Packages                           
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/multiverse Packages                           
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/universe Packages                             
Ign [http://hacktolive.org](http://hacktolive.org) jaunty/partner Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://hacktolive.org](http://hacktolive.org) jaunty/main Packages                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://hacktolive.org](http://hacktolive.org) jaunty/restricted Packages                           
Hit [http://hacktolive.org](http://hacktolive.org) jaunty/multiverse Packages                           
Hit [http://hacktolive.org](http://hacktolive.org) jaunty/universe Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages                
Hit [http://hacktolive.org](http://hacktolive.org) jaunty/partner Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages                     
Fetched 197B in 7s (26B/s)                                                     
Reading package lists... Done
W: GPG error: [http://hacktolive.org](http://hacktolive.org) jaunty Release: The following signatures were invalid: KEYEXPIRED 1265785910 KEYEXPIRED 1265785910 KEYEXPIRED 1265785910
W: You may want to run apt-get update to correct these problems[/I]

(error repeats each time run, and I can't figure out how to direct the key recieve command to a server that understands that key... google does not show any entries for that particular "keyexpired 1265785910" chunk.)
-----
[I]
 sudo gnome-app-install

Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.6/dist-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: /var/lib/python-support/python2.6/gtk-2.0/gconf.so: invalid ELF header
[/I]

It seems like I need more than code, like I have to make some kind of change to a file by hand or like I need a web based upgrade or something. I waited for a long time to reach my ubuntu friend and can't find him and turn toward you. I would love to keep the settings and files and not have to reinstall from my cd, but will if I have too. Please help!  

Loren
ps: please tell me if I should change the prefix of the thread

---

### Post by zvacet on 2010-02-10
It look like you have mixed repos witch is not good idea.Please type

```
cat /etc/apt/sources.list
```

and post it here.You don't need any repo for Opera,just download it from [here.]("http://www.opera.com/browser/download/?os=linux-i386&ver=10.10&local=y")

---

### Post by jmszr on 2010-02-10
HappyOm,

This _may_ help with your Add/Remove and Update Manager issue:

```
sudo rm &#8236;/var/cache/apt/*&#8236;.bin
```

Worth a try.

Edit: And then run:

```

sudo apt-get update && sudo apt-get upgrade
```

---

### Post by HappyOm on 2010-02-10
Following the first set of instructions first (I feel more comfortable showing a file than performing a command I don't recognize that "may" help, especially when a much more senior user suggests something else... willing to try the rm command if nothing is working or if a story is presented with it)


I entered:   cat /etc/apt/sources.list
[I]
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free #medibuntu
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main #ubuntu-tweak
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free #opera
deb [http://ppa.launchpad.net/specto/ppa/ubuntu](http://ppa.launchpad.net/specto/ppa/ubuntu) jaunty main #specto[/I]

---

### Post by HappyOm on 2010-02-12
Still waiting somewhat patiently for help... the system does interesting things occasionally. Please someone play with me to fix it. Thanks!

---

### Post by dearingj on 2010-02-12
I notice that the blog on hacktolive.org mentions putting their GPG key(s) in a package called "super-os-repo". Maybe you don't have the latest version of that package.

I'd also recommend commenting out (put a # in front of) the last 4 lines of your sources.list. I don't think those particular repositories would cause any problems, but it is possible. You can use the command "sudo gedit /etc/apt/sources.list" to edit the file. When you're done, save the file and run "sudo apt-get update".

---

### Post by HappyOm on 2010-02-12
re-installed the super-os-repo package and commented out the last 4 lines of my sources. No change to the Key expired error, and more importantly no change to my inability to open the update manager or add/remove.

I did however learn a bit about terminal code and am perusing the ubuntu pocket guide ... still stuck...

---

### Post by jmszr on 2010-02-12
HappyOm,
 
The command that I proposed you try "sudo rm &#8236;/var/cache/apt/*&#8236;.bin" worked for me when my Add/Remove, Update Manager and Synaptic would only start to open and then would fade away. Here is a thread relating to use of it:[http://ubuntuforums.org/showthread.php?t=1333230](http://ubuntuforums.org/showthread.php?t=1333230) .

It won't harm your install if it doesn't work, it just won't fix it.

---

### Post by HappyOm on 2010-02-12
Hey, glad to see your currently online. I just began trying your path of action and although I got no result with that *.bin code (didn't appear to be in my system)   I am very glad to be in the middle of the second operation getting upgraded which still has 30 minutes remaining. I feel this might do it.

I also bothered to type "key" on the hacktolive search page and found a repository update for Super Ubuntu that includes this key. I think "keyexpired" was just a helpful (though confusing) feature forcing users to go to hacktolive.org and manually get the new repository. If the current process doesn't fix it on its own (and hopefully fix the python elf header error), I will go download it and hopefully be back up and running.

I will update in 30-45 minutes with new info. Very Hopeful :-)

*PS: I hope there was no offence in me not acting earlier... I just still had NO CLUE about unix code or the backend functionality of ubuntu (learning from the pocket guide now and will continue learning now that the process has begun) and didn't want to follow a *[FONT=Comic Sans MS]may work[/FONT]* piece of advice without more info... you saying it wouldn't hurt anything made me feel better about it, plus I was more ready to try anything.*

---

### Post by jmszr on 2010-02-12
HappyOm,

No offense taken - one always wants to be careful around any code that starts out "rm" . Too bad it didn't work for you. Hope you have everything on the right track now.

---

### Post by HappyOm on 2010-02-12
Well, I'm full of updates:

Firstly, the get upgrade that worked so hard also seemed to do nothing.

Second, the hacktolive.com repo+key I found fixed my error and apt-get update worked!

Third, no change to the add/remove launcher or to the update manager (which seems to be hanging in the background and causes the system to let me know the process is still going when trying to shutdown. )

Although my apt-get update brings no error, I still have this python import error

[I]sudo gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 27, in <module>
    from AppInstall.activation import main
  File "/usr/lib/python2.6/dist-packages/AppInstall/activation.py", line 20, in <module>
    import gconf
ImportError: /var/lib/python-support/python2.6/gtk-2.0/gconf.so: invalid ELF header
[/I]

I also am not sure if this is always the case, but I think it appeared recently   

I have a file named gconf in my user folder that has a lock on it, a PS document according to the properties. I mention this because import gconf is in the error message. Is this file somehow in the wrong place?

Gratefully awaiting continued assistance (and currently about to restart the OS again),
Loren

---

### Post by HappyOm on 2010-02-12
new errors 

apt-get update

W: GPG error: [http://hacktolive.org](http://hacktolive.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3984D5AD12877092
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems


I think I can fix these and will work on it, but am confused at how they suddenly popped up...

---

### Post by HappyOm on 2010-02-12
made some progress, stuck at finding a hacktolive key again:

[I]
loren@HapiestOhm:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                                        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US                          
Get:1 [http://hacktolive.org](http://hacktolive.org) karmic Release.gpg [197B]                                      
Ign [http://hacktolive.org](http://hacktolive.org) karmic/main Translation-en_US                                    
Ign [http://hacktolive.org](http://hacktolive.org) karmic/restricted Translation-en_US                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                           
Ign [http://hacktolive.org](http://hacktolive.org) karmic/multiverse Translation-en_US                             
Ign [http://hacktolive.org](http://hacktolive.org) karmic/universe Translation-en_US          
Ign [http://hacktolive.org](http://hacktolive.org) karmic/partner Translation-en_US           
Hit [http://hacktolive.org](http://hacktolive.org) karmic Release                                                   
Ign [http://hacktolive.org](http://hacktolive.org) karmic Release                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                                              
Ign [http://hacktolive.org](http://hacktolive.org) karmic/main Packages                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                                    
Ign [http://hacktolive.org](http://hacktolive.org) karmic/restricted Packages                                       
Ign [http://hacktolive.org](http://hacktolive.org) karmic/multiverse Packages                 
Ign [http://hacktolive.org](http://hacktolive.org) karmic/universe Packages                   
Ign [http://hacktolive.org](http://hacktolive.org) karmic/partner Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Sources
Hit [http://hacktolive.org](http://hacktolive.org) karmic/main Packages 
Hit [http://hacktolive.org](http://hacktolive.org) karmic/restricted Packages
Hit [http://hacktolive.org](http://hacktolive.org) karmic/multiverse Packages
Hit [http://hacktolive.org](http://hacktolive.org) karmic/universe Packages
Hit [http://hacktolive.org](http://hacktolive.org) karmic/partner Packages
Fetched 197B in 2s (72B/s)
Reading package lists... Done
W: GPG error: [http://hacktolive.org](http://hacktolive.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3984D5AD12877092
W: You may want to run apt-get update to correct these problems

[/I]**then I tried**[I]

loren@HapiestOhm:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3984D5AD12877092
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 3984D5AD12877092
gpg: requesting key 12877092 from hkp server keyserver.ubuntu.com
gpgkeys: key 3984D5AD12877092 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

[/I][B]Then tried

[/B][I] loren@HapiestOhm:~$ sudo apt-key adv --recv-keys --keyserver hacktolive.org 3984D5AD12877092
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver hacktolive.org 3984D5AD12877092
gpg: requesting key 12877092 from hkp server hacktolive.org

gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error[/I]


no change in system performance yet

---

### Post by HappyOm on 2010-02-14
figured out that I could enter the whole [http://hacktolive.org](http://hacktolive.org) karmic release" term in a key recieve and found a new error... heres the error from the end of my update, followed by the attempt to fix it and its error:
[I]

W: GPG error: [http://hacktolive.org](http://hacktolive.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3984D5AD12877092
W: You may want to run apt-get update to correct these problems

loren@HapiestOhm:~$ sudo gpg --keyserver [http://hacktolive.org](http://hacktolive.org) karmic release --recv-keys 3984D5AD12877092
gpg: WARNING: unsafe ownership on configuration file `/home/loren/.gnupg/gpg.conf'
usage: gpg [options] [filename]
loren@HapiestOhm:~$ 
[/I]

Help :-)?

---

### Post by HappyOm on 2010-02-14
My gconf file has the following permissions:

Owner: root  (read and write)

Group: root  (read only)

Others: [blank]  (read only)  

Maybe they need to be changed?

---

### Post by zvacet on 2010-02-14
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3984D5AD12877092
gpg --export --armor 3984D5AD12877092 | sudo apt-key add -
```

---

### Post by HappyOm on 2010-02-15
nothing

[I]loren@HapiestOhm:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3984D5AD12877092
gpg: requesting key 12877092 from hkp server subkeys.pgp.net
gpgkeys: key 3984D5AD12877092 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
loren@HapiestOhm:~$ gpg --export --armor 3984D5AD12877092 | sudo apt-key add -
gpg: no valid OpenPGP data found.
loren@HapiestOhm:~$ [/I]

---

### Post by HappyOm on 2010-02-15
I installed something via synaptic (which still seems to work for all basic purposes)  and although it said sucess, the following error came up right after the install:

dang it... seem to have lost it, I thought it copied, well shoot. Anyway, it said something about not being able to lock a directory that was related to dpkg... I'll try to trigger it again..

---

### Post by tugalsan on 2010-02-22
I have the same problem. I am using hacktolive for its right click script menu & nautlus root mode on apps menu. I need to run 9.04, becuase my comp is LG-S1 and 9.10 does not support sound issues. If anyone solves the problem please keep on posting. i hate to setup my system and discover amerika again and again

---

### Post by g3nghisk4hn on 2010-08-18
> **HappyOm said:**
> figured out that I could enter the whole [http://hacktolive.org](http://hacktolive.org) karmic release" term in a key recieve and found a new error... heres the error from the end of my update, followed by the attempt to fix it and its error:
[I]

W: GPG error: [http://hacktolive.org](http://hacktolive.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3984D5AD12877092
W: You may want to run apt-get update to correct these problems

loren@HapiestOhm:~$ sudo gpg --keyserver [http://hacktolive.org](http://hacktolive.org) karmic release --recv-keys 3984D5AD12877092
gpg: WARNING: unsafe ownership on configuration file `/home/loren/.gnupg/gpg.conf'
usage: gpg [options] [filename]
loren@HapiestOhm:~$ 
[/I]

Help :-)?

This post is somewhat outdated but I found it when I was searching for help when I had a similar problem when i updated from "karmic" to "lucid"...

I 'think' i fixed it by changing the sources for hacktolive.org from "karmic" to "lucid"

---

