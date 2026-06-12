---
title: "Update Manager can't connect to Internet"
date: 2011-05-06
forum: General Help
---

### Post by TurtleKing on 2011-05-06
All of a sudden Update Manager cannot connect to Internet. I just recently fixed a problem I had with playdeb not installing the games due to a internet connection problem (fixed by downloading the script instead of terminal method), this is the only big change I done recently other than downloading documents and pictures.

Here is the detail as to where or why it cannot connect:
```
W:Failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```
I would ignore it, but this happens every time I run the program.

---

### Post by TurtleKing on 2011-05-06
bump.

---

### Post by matt_symes on 2011-05-06
Hi

Open a terminal and type

```
cat /etc/apt/sources.list
```

Copy and paste the results back here between code tags. 

If you look at this [http://ppa.launchpad.net/lorenzo-carbonell/](http://ppa.launchpad.net/lorenzo-carbonell/) you will see that the ppa is empty, hence your error.

Kind regards

---

### Post by TurtleKing on 2011-05-07
Hopefully there is a fix for it as I now notice somethings will not install (weather applet).
```
replaced@replaced:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main
deb http://archive.getdeb.net/ubuntu lucid-getdeb games
deb-src http://archive.getdeb.net/ubuntu lucid-getdeb games
replaced@replaced:~$ 
```

---

### Post by matt_symes on 2011-05-07
Hi

The offending lines are not in your sources.list file. This means they will be in one of your apt sub files. 

To find out which file please post the output of (case sensitive)

```
grep -R "ppa.launchpad.net/lorenzo-carbonell" /etc/apt/*
```

The easiest way is to just copy and paste the above text into a terminal.

We will then be able to delete the offending file.

Kind regards

---

### Post by TurtleKing on 2011-05-07
```
replaced@replaced:~$ grep -R "ppa.launchpad.net/lorenzo-carbonell" /etc/apt/*
grep: /etc/apt/secring.gpg: Permission denied
/etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list:deb http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu natty main
/etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list:deb-src http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu natty main
/etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list.save:deb http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu natty main
/etc/apt/sources.list.d/lorenzo-carbonell-atareao-natty.list.save:deb-src http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu natty main
grep: /etc/apt/trustdb.gpg: Permission denied
replaced@replaced:~$ 
```

---

### Post by matt_symes on 2011-05-07
Hi

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/lorenzo-carbonell-atareao*
```

It's easiest to copy and paste this into a terminal.

Then enter

```
sudo apt-get update
```

Kind regards

---

### Post by TurtleKing on 2011-05-07
Thanks,:) there are no errors now, upon using update manager.

---

### Post by TurtleKing on 2011-05-08
Grrr the problem is back. I recommend nobody (unless they actually tested them) install the indicator applets suggested on OMGUbuntu-Top 10 things to do after installing.

If you wouldn't mind giving me assistance once again (sorry):
```
W:Failed to fetch http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I tried using the previous fix, but it says the file doesn't exist or cannot be found (i guess it solved that particular one only).

---

### Post by matt_symes on 2011-05-08
Hi

Open a terminal and copy and paste into the terminal

```
grep -R -E "http://ppa.launchpad.net/fredp|http://ppa.launchpad.net/lorenzo-carbonell" /etc/apt/*
```

Post the results back here. 

Kind regards

---

### Post by TurtleKing on 2011-05-08
Glad your still around. :)
```
replaced@replaced:~$ grep -R -E "http://ppa.launchpad.net/fredp|http://ppa.launchpad.net/lorenzo-carbonell" /etc/apt/*
grep: /etc/apt/secring.gpg: Permission denied
/etc/apt/sources.list.d/fredp-ppa-natty.list:deb http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
/etc/apt/sources.list.d/fredp-ppa-natty.list:deb-src http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
/etc/apt/sources.list.d/fredp-ppa-natty.list.save:deb http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
/etc/apt/sources.list.d/fredp-ppa-natty.list.save:deb-src http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
grep: /etc/apt/trustdb.gpg: Permission denied
replaced@replaced:~$
```

---

### Post by spacebunny on 2011-05-08
I'm experiencing the exact same problem with Update Manager, with the exact same output in Terminal, on my Sony Vaio using 11.04 64-bit.

---

### Post by matt_symes on 2011-05-08
Hi

@TurtleKing

Open a terminal and type..

```
sudo rm /etc/apt/sources.list.d/fredp-ppa-natty*
sudo apt-get update
```

That should fix the fred problem. 

I cannot see any reference to [noparse]http://ppa.launchpad.net/lorenzo-carbonell[/noparse]

so if you still have issues after the commands above, please post the output of

```
ls /etc/apt/sources.list.d/
```

@spacebunny

Open a terminal and type

```
sudo apt-get update
```

Please post the output back here between code tags. If you are unsure how to use code tags then post back telling me that first.

Kind regards

---

### Post by TurtleKing on 2011-05-08
Yeah it is working again, thanks.

@spacebunny did you follow the instructions from OMG-Ubuntu for installing indicator applets on Ubuntu 11.04? If so, then the problem is not just on my end, but their end. I have the feeling they just copy and pasted the terminal commands without making sure they worked properly or didn't cause errors (like in my case).

---

### Post by RJ12 on 2011-05-08
Yeah, I was having the same exact errors with that launchpad repository, I think it may have been deleted or something?

---

### Post by matt_symes on 2011-05-08
Hi

The problem is there is no folder for natty for fredp. 

Take a look at this

[http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/](http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/)

and this ones does not seem to exist any more

[http://ppa.launchpad.net/lorenzo-carbonell](http://ppa.launchpad.net/lorenzo-carbonell)

Maybe that will change

Kind regards

---

### Post by TurtleKing on 2011-05-10
Marking thread solved. Hopefully spacebunny you got it fixed.

---

### Post by spacebunny on 2011-05-11
Fixed by removing the lorenzo PPA. Thanks for your help.

---

### Post by dhawal92 on 2011-06-22
> **matt_symes said:**
> Hi

@TurtleKing

Open a terminal and type..

```
sudo rm /etc/apt/sources.list.d/fredp-ppa-natty*
sudo apt-get update
```That should fix the fred problem. 

I cannot see any reference to [noparse]http://ppa.launchpad.net/lorenzo-carbonell[/noparse]

so if you still have issues after the commands above, please post the output of

```
ls /etc/apt/sources.list.d/
```@spacebunny

Open a terminal and type

```
sudo apt-get update
```Please post the output back here between code tags. If you are unsure how to use code tags then post back telling me that first.

Kind regards

Thanks man it works :D

---

### Post by goyard4x on 2011-11-01
Hi, I had 11.04 updating fine for over 8 months and then it just stopped working says "failed to Fetch" Here is the apt source list any help will be appreciated. It won't let me upgrade to 11.10 and I don't want to wipe my configuration if I don't have to.


# deb cdrom:[Kubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-proposed restricted main multiverse universe

---

### Post by matt_symes on 2011-11-01
Hi

```
deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
deb http://archive.ubuntu.com/ubuntu natty main restricted
```

Are you trying to upgrade from the cd rom or over the internet ? Any reason you have the 11.10 cdrom enabled in your sources.list file ?

Anhyway what is failing ? Please post the output of

```
sudo apt-get update
```

Kind regards

---

### Post by Fyllling on 2011-11-23
Hi.

I need some help regarding the same problem.
Heres the output of the command;
 
cat /etc/apt/sources.list
[PHP]# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://no.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-security main restricted
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-security universe
deb http://no.archive.ubuntu.com/ubuntu/ oneiric-security multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
[/PHP]I saved it inside the PHP tags due to it's largeness (excuse my poor english :P )


Best regards
Fyllling ;)

[FONT=monospace]
[/FONT]

---

### Post by matt_symes on 2011-11-23
Hi

@fylling

Open a terminal and type

```
sudo apt-get update
```Please post the results back here between code tags and not php tags. To  use code tags, use the # button above where you type your reply.

Kind regards

---

### Post by Fyllling on 2011-11-23
Ok. So I've typed the command and here is the results:

```
Ign http://no.archive.ubuntu.com oneiric InRelease
Ign http://no.archive.ubuntu.com oneiric-updates InRelease          
Ign http://no.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://no.archive.ubuntu.com oneiric-security InRelease                    
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.canonical.com lucid InRelease                               
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://no.archive.ubuntu.com oneiric Release.gpg                           
Hit http://no.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://no.archive.ubuntu.com oneiric-backports Release.gpg       
Ign http://deb.playonlinux.com maverick InRelease                    
Hit http://no.archive.ubuntu.com oneiric-security Release.gpg        
Hit http://no.archive.ubuntu.com oneiric Release                     
Hit http://no.archive.ubuntu.com oneiric-updates Release
Hit http://archive.canonical.com oneiric Release.gpg
Ign http://ppa.launchpad.net oneiric InRelease 
Hit http://ppa.launchpad.net oneiric Release.gpg
Hit http://deb.playonlinux.com maverick Release.gpg                   
Hit http://no.archive.ubuntu.com oneiric-backports Release                     
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://no.archive.ubuntu.com oneiric-security Release                      
Hit http://deb.playonlinux.com maverick Release                                
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://ppa.launchpad.net oneiric Release.gpg                      
Hit http://ppa.launchpad.net oneiric Release.gpg                      
Hit http://archive.canonical.com oneiric Release                      
Hit http://ppa.launchpad.net oneiric Release                          
Hit http://no.archive.ubuntu.com oneiric/main Sources                 
Hit http://no.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://no.archive.ubuntu.com oneiric/universe Sources                      
Hit http://no.archive.ubuntu.com oneiric/multiverse Sources           
Hit http://no.archive.ubuntu.com oneiric/main amd64 Packages          
Hit http://archive.canonical.com lucid Release                                 
Hit http://no.archive.ubuntu.com oneiric/restricted amd64 Packages    
Hit http://no.archive.ubuntu.com oneiric/universe amd64 Packages      
Hit http://no.archive.ubuntu.com oneiric/multiverse amd64 Packages
Hit http://no.archive.ubuntu.com oneiric/main i386 Packages
Hit http://no.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://no.archive.ubuntu.com oneiric/universe i386 Packages
Ign http://ppa.launchpad.net oneiric Release                          
Ign http://ppa.launchpad.net oneiric Release                          
Hit http://no.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://no.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://no.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://no.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://no.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://no.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://no.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://no.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://no.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://no.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://no.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://deb.playonlinux.com maverick/main amd64 Packages                    
Hit http://no.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://no.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://no.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://no.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://no.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://no.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://no.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://no.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://no.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://no.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://no.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://deb.playonlinux.com maverick/main i386 Packages                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://no.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://no.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://no.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://no.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://no.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Ign http://deb.playonlinux.com maverick/main TranslationIndex        
Hit http://no.archive.ubuntu.com oneiric-backports/universe amd64 Packages
Hit http://no.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages
Hit http://no.archive.ubuntu.com oneiric-backports/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://no.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://no.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://no.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://no.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://no.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://no.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://no.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://archive.canonical.com lucid/partner Sources
Hit http://archive.canonical.com lucid/partner amd64 Packages
Hit http://archive.canonical.com lucid/partner i386 Packages
Ign http://archive.canonical.com lucid/partner TranslationIndex
Hit http://no.archive.ubuntu.com oneiric-security/main Sources
Hit http://no.archive.ubuntu.com oneiric-security/restricted Sources 
Hit http://no.archive.ubuntu.com oneiric-security/universe Sources   
Hit http://no.archive.ubuntu.com oneiric-security/multiverse Sources 
Hit http://no.archive.ubuntu.com oneiric-security/main amd64 Packages
Hit http://no.archive.ubuntu.com oneiric-security/restricted amd64 Packages    
Hit http://no.archive.ubuntu.com oneiric-security/universe amd64 Packages      
Hit http://no.archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://no.archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://no.archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://no.archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://no.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://no.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://no.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://no.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://no.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://no.archive.ubuntu.com oneiric/main Translation-en
Hit http://no.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://no.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://no.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://no.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://no.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://no.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://no.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://no.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Hit http://no.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://no.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://no.archive.ubuntu.com oneiric-backports/universe Translation-en
Hit http://no.archive.ubuntu.com oneiric-security/main Translation-en          
Hit http://no.archive.ubuntu.com oneiric-security/multiverse Translation-en    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://no.archive.ubuntu.com oneiric-security/restricted Translation-en    
Hit http://no.archive.ubuntu.com oneiric-security/universe Translation-en
Err http://ppa.launchpad.net oneiric/main Sources                    
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages             
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages              
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://deb.playonlinux.com maverick/main Translation-en_US       
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-en_US          
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://deb.playonlinux.com maverick/main Translation-en          
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://archive.canonical.com lucid/partner Translation-en_US
Ign http://archive.canonical.com lucid/partner Translation-en
W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```



Thanks for the fast reply, I really appreciate it! :)



Best regards
Fylling ;)

---

### Post by matt_symes on 2011-11-24
Hi

@Fylling

```

deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
```

You are using Lucid repositories in your sources. You want to remove them. Open a terminal and copyb and paste this into it.

```
sudo sed -i '/lucid/d' /etc/apt/sources.list
```

Enter your password. It will not be echoed to the screen.

The other errors are caused invalid PPAs. They are stored in you sources.list.d directory. To find them openn a terminal and type (or copy and paste)

```
grep -E "tualatrix|sun-java-community-team|ppa.launchpad.net" /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by Fyllling on 2011-11-24
> **matt_symes said:**
> Hi

@Fylling

```

deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner
```You are using Lucid repositories in your sources. You want to remove them. Open a terminal and copyb and paste this into it.

```
sudo sed -i '/lucid/d' /etc/apt/sources.list
```Enter your password. It will not be echoed to the screen.

The other errors are caused invalid PPAs. They are stored in you sources.list.d directory. To find them openn a terminal and type (or copy and paste)

```
grep -E "tualatrix|sun-java-community-team|ppa.launchpad.net" /etc/apt/sources.list.d/*
```Kind regards

Ok, thank you! :D

So I should just remove them from the directory, right?
Which I just did, and the apt-get get update works fine, and so does the update manager!
Thank you once again! :D


Best regards
Fylling ;)

---

