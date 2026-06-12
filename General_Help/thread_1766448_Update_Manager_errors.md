---
title: "Update Manager errors"
date: 2011-05-24
forum: General Help
---

### Post by gamendorf on 2011-05-24
This is my first experience with Linux, and I am so far very pleased, but a little overwhelmed. I downloaded and installed Ubuntu 11.4 from CD on release day. About 2 weeks later my Update Manager started having problems:

**Could not download all repository indexes**

[COLOR=Navy]The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/COLOR]

[COLOR=Red]Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.[/COLOR]

[COLOR=Black]Here is a list of the things that I have tried from various forum threads: (all have failed)
1.  Change the repository software source to Main, United States, UT Austin, U. Chicago, and even hit "Select Best Server."  Same errors for all.

2.    [/COLOR]sudo rm /var/lib/apt/lists/* -vf
       sudo apt-get update
                 Same errors as before

3.   Some of the other threads have requested the sources.list file.  Here is my output (if there is a problem somewhere in this, I don't know what I'm looking for..)

[COLOR=Blue]# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-updates main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-updates universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-updates multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-security main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-security main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-security universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-security universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-security multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main[/COLOR]

---

### Post by ivanovnegro on 2011-05-24
You have two PPAs that are showing a 404 error, I would remove these PPAs from your sources list and it should update the system normally.

---

### Post by oldos2er on 2011-05-24
> [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/natty/main/source/Sources)

Shouldn't that be [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/main/source/Sources) ? Look in /etc/apt/sources.list.d/

---

### Post by matt_symes on 2011-05-24
Hi

Your problem in your sources.d directory. Please post the output of (from a terminal)

```
grep "http://ppa.launchpad.net/ubuntu-win" /etc/apt/sources.list.d/*
```

The ppa is referring to win and not wine i think, but the above command will confirm this.

Kind regards
[COLOR=Red] [/COLOR]

---

### Post by gamendorf on 2011-05-24
Results of grep "http://ppa.launchpad.net/ubuntu-win" /etc/apt/sources.list.d/*


/etc/apt/sources.list.d/ubuntu-win-ppa-natty.list:deb [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu) natty main
/etc/apt/sources.list.d/ubuntu-win-ppa-natty.list:deb-src [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu) natty main
/etc/apt/sources.list.d/ubuntu-win-ppa-natty.list.save:deb [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu) natty main
/etc/apt/sources.list.d/ubuntu-win-ppa-natty.list.save:deb-src [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu) natty main

---

### Post by Frogs Hair on 2011-05-24
Hi and Welcome

Your first two errors indicate it can't find  sources for two PPAs . Check to see if those PPAs are compatible with your version of Ubuntu .

If you just remove the source the PPA will no longer update but I should clear the error.

---

### Post by gamendorf on 2011-05-24
> **Frogs Hair said:**
> Hi and Welcome

Your first two errors indicate it can't find  sources for two PPAs . Check to see if those PPAs are compatible with your version of Ubuntu .

If you just remove the source the PPA will no longer update but I should clear the error.

How do I tell if they are compatible?

---

### Post by matt_symes on 2011-05-24
Hi

> **gamendorf said:**
> Results of grep "http://ppa.launchpad.net/ubuntu-win" /etc/apt/sources.list.d/*

/etc/apt/sources.list.d/ubuntu-win-ppa-natty.list:deb [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu) natty main
/etc/apt/sources.list.d/ubuntu-win-ppa-natty.list:deb-src [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu) natty main


Open a terminal and type 

```
sudo nano /etc/apt/sources.list.d/ubuntu-win-ppa-natty.list
```Enter your password. It will not be echoed to the screen. This is normal. Edit the file so it becomes
```

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu") natty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu") natty main

```(Notice **ubuntu-win** has changed to **ubuntu-wine**)

Press ctrl + o to save and ctrl + x to exit. Then type

```
sudo apt-get update
```Kind regards

---

### Post by ivanovnegro on 2011-05-24
> **gamendorf said:**
> How do I tell if they are compatible?

Normally I look on the Launchpad site if the PPA is first, active, and second, for my system, for example 11.04 and not for an older version etc.
I think removing them is the way to go. I was on the site, it does not exist. 
Sometimes the PPA can also outdate and sometimes the servers can be down also.

---

### Post by matt_symes on 2011-05-24
Hi

Natty is in there

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/natty/)

Kind regards

---

### Post by ivanovnegro on 2011-05-24
> **matt_symes said:**
> Hi



Open a terminal and type 

```
sudo nano /etc/apt/sources.list.d/ubuntu-win-ppa-natty.list
```Enter your password. It will not be echoed to the screen. This is normal. Edit the file so it becomes
```

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu") natty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu") natty main

```(Notice **ubuntu-win** has changed to **ubuntu-wine**)

Press ctrl + o to save and ctrl + x to exit. Then type

```
sudo apt-get update
```Kind regards

I did not realize this, Win and Wine. :)
Then this suggestion is also a good one if he really wanted to install Wine but typed it wrong.
But Wine is also in the repositories, this makes things easier for new users.

---

### Post by gamendorf on 2011-05-24
> **matt_symes said:**
> Hi



Open a terminal and type 

```
sudo nano /etc/apt/sources.list.d/ubuntu-win-ppa-natty.list
```Enter your password. It will not be echoed to the screen. This is normal. Edit the file so it becomes
```

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu") natty main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu") natty main

```(Notice **ubuntu-win** has changed to **ubuntu-wine**)

Press ctrl + o to save and ctrl + x to exit. Then type

```
sudo apt-get update
```Kind regards


Did the above, and here is the result of sudo apt-get update
```

Ign http://mirror.anl.gov natty InRelease
Ign http://mirror.anl.gov natty-updates InRelease                              
Ign http://mirror.anl.gov natty-security InRelease                             
Hit http://mirror.anl.gov natty Release.gpg                                    
Hit http://mirror.anl.gov natty-updates Release.gpg                            
Hit http://mirror.anl.gov natty-security Release.gpg                           
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://mirror.anl.gov natty Release                                        
Ign http://extras.ubuntu.com natty InRelease                                   
Hit http://mirror.anl.gov natty-updates Release                                
Hit http://mirror.anl.gov natty-security Release                               
Get:1 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://mirror.anl.gov natty/main Sources                                   
Get:2 http://ppa.launchpad.net natty Release [9,744 B]                         
Hit http://archive.canonical.com natty Release                                 
Hit http://mirror.anl.gov natty/restricted Sources                             
Hit http://mirror.anl.gov natty/universe Sources                               
Hit http://mirror.anl.gov natty/multiverse Sources                             
Hit http://extras.ubuntu.com natty Release                                     
Hit http://mirror.anl.gov natty/main i386 Packages                             
Hit http://mirror.anl.gov natty/restricted i386 Packages                       
Hit http://mirror.anl.gov natty/universe i386 Packages                         
Hit http://mirror.anl.gov natty/multiverse i386 Packages                       
Ign http://mirror.anl.gov natty/main TranslationIndex                          
Ign http://mirror.anl.gov natty/multiverse TranslationIndex                    
Ign http://mirror.anl.gov natty/restricted TranslationIndex                    
Ign http://mirror.anl.gov natty/universe TranslationIndex                      
Hit http://mirror.anl.gov natty-updates/main Sources                           
Hit http://mirror.anl.gov natty-updates/restricted Sources                     
Hit http://mirror.anl.gov natty-updates/universe Sources                       
Hit http://mirror.anl.gov natty-updates/multiverse Sources                     
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Ign http://ppa.launchpad.net natty Release                                     
Hit http://mirror.anl.gov natty-updates/main i386 Packages                     
Hit http://mirror.anl.gov natty-updates/restricted i386 Packages               
Hit http://mirror.anl.gov natty-updates/universe i386 Packages                 
Hit http://mirror.anl.gov natty-updates/multiverse i386 Packages               
Ign http://mirror.anl.gov natty-updates/main TranslationIndex                  
Ign http://mirror.anl.gov natty-updates/multiverse TranslationIndex            
Ign http://mirror.anl.gov natty-updates/restricted TranslationIndex            
Ign http://mirror.anl.gov natty-updates/universe TranslationIndex              
Hit http://archive.canonical.com natty/partner i386 Packages                   
Hit http://mirror.anl.gov natty-security/main Sources                          
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://mirror.anl.gov natty-security/restricted Sources                    
Hit http://mirror.anl.gov natty-security/universe Sources                      
Hit http://mirror.anl.gov natty-security/multiverse Sources                    
Get:3 http://ppa.launchpad.net natty/main Sources [1,561 B]                    
Hit http://mirror.anl.gov natty-security/main i386 Packages                    
Hit http://mirror.anl.gov natty-security/restricted i386 Packages              
Hit http://mirror.anl.gov natty-security/universe i386 Packages                
Hit http://mirror.anl.gov natty-security/multiverse i386 Packages              
Ign http://mirror.anl.gov natty-security/main TranslationIndex                 
Ign http://mirror.anl.gov natty-security/multiverse TranslationIndex           
Ign http://mirror.anl.gov natty-security/restricted TranslationIndex           
Ign http://mirror.anl.gov natty-security/universe TranslationIndex             
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Get:4 http://ppa.launchpad.net natty/main i386 Packages [2,530 B]              
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://mirror.anl.gov natty/main Translation-en_US                         
Ign http://mirror.anl.gov natty/main Translation-en                            
Ign http://mirror.anl.gov natty/multiverse Translation-en_US                   
Ign http://mirror.anl.gov natty/multiverse Translation-en                      
Ign http://mirror.anl.gov natty/restricted Translation-en_US                   
Ign http://mirror.anl.gov natty/restricted Translation-en                      
Ign http://mirror.anl.gov natty/universe Translation-en_US                     
Ign http://mirror.anl.gov natty/universe Translation-en                        
Ign http://mirror.anl.gov natty-updates/main Translation-en_US                 
Ign http://mirror.anl.gov natty-updates/main Translation-en                    
Ign http://mirror.anl.gov natty-updates/multiverse Translation-en_US           
Ign http://mirror.anl.gov natty-updates/multiverse Translation-en              
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://mirror.anl.gov natty-updates/restricted Translation-en_US           
Ign http://mirror.anl.gov natty-updates/restricted Translation-en              
Ign http://mirror.anl.gov natty-updates/universe Translation-en_US             
Ign http://mirror.anl.gov natty-updates/universe Translation-en                
Ign http://mirror.anl.gov natty-security/main Translation-en_US                
Ign http://mirror.anl.gov natty-security/main Translation-en                   
Ign http://mirror.anl.gov natty-security/multiverse Translation-en_US          
Ign http://mirror.anl.gov natty-security/multiverse Translation-en             
Ign http://mirror.anl.gov natty-security/restricted Translation-en_US          
Ign http://mirror.anl.gov natty-security/restricted Translation-en             
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://mirror.anl.gov natty-security/universe Translation-en_US            
Ign http://mirror.anl.gov natty-security/universe Translation-en               
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Fetched 14.2 kB in 7s (1,902 B/s)                                              
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ natty/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_binary-i386_Packages)

```I also ran Update Manager again, and here is the new error:
**Requires installation of untrusted packages**
The action would require the installation of packages from not authenticated sources.
[COLOR=Blue]ttf-symbol-replacement-wine1.3 wine1.3-gecko[/COLOR]

---

### Post by Frogs Hair on 2011-05-24
> **gamendorf said:**
> How do I tell if they are compatible?

Go to the site where you found the PPAs it is usually stated what versions of Ubuntu they are compatible with. A PPA won't install itself so you would Know best where to find it.

It could also be a matter of enabling the independent repositories in the software sources list.

---

### Post by matt_symes on 2011-05-24
Hi

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

I also ran Update Manager again, and here is the new error:
Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
ttf-symbol-replacement-wine1.3 wine1.3-geckoThese 2 errors are related to each other and are due to the fact you don't have the correct GPG key.

It seems to me you are very new with Ubuntu so i think the best advice is to follow ivanovnegro's advice and use the software centre. When you are more comfortable with that then use ppas. So...

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/ubuntu-win-ppa-natty.*
sudo apt-get update
```Then install wine using synaptic package manager or software centre

Kind regards

---

### Post by gamendorf on 2011-05-24
> **Frogs Hair said:**
> Go to the site where you found the PPAs it is usually stated what versions of Ubuntu they are compatible with. A PPA won't install itself so you would Know best where to find it.

It could also be a matter of enabling the independent repositories in the software sources list.

 Here is my Ubuntu experience in a nutshell:
I decided that I wanted to get rid of Windows, and installed OpenSUSE. I had all sorts of problems, mostly with Yast and Yast2.  A friend suggested that I switch to Ubuntu.  I installed Ubuntu 11.4 and have been very pleased with it.  I have been trying out different programs to try to make my "Penguin Plunge" work out, basically just trying out different ones to see if the do what I want them to do (example: trying out GNU-Cash and KMoney as replacement for Quicken)  I ended up having to install XP in VMWare due to my business software being Windows dependent.  

As of right now, I am still a Ubuntu newb.  I am comfortable using the terminal for simple things, but i know that it is much more powerful than what I have done with it.  I have no idea what a PPA even is, or where it came from. All I know is that there is a built-in Update Manager with a GUI, and that it is not working. I would love to fix this stuff, but am completely lost.  

(sorry if any of that came out disrespectful or flame-ish. Didn't mean to if it did. Dont have time right now to go back and check it over.)

---

### Post by gamendorf on 2011-05-24
> **matt_symes said:**
> Hi



```
sudo rm /etc/apt/sources.list.d/ubuntu-win-ppa-natty.*
sudo apt-get update
```



That got it! Thanks for all the help!  This is all so different to me. Hopefully I'll get it all down sooner than later.

---

### Post by ivanovnegro on 2011-05-24
Im happy that you could solve your problem.
Usually its not as difficult.
If you want to install Windows apps, just use Wine but install it from the Software Center before you will be more comfortable with PPAs.
[Here]("https://help.launchpad.net/Packaging/PPA"), what a PPA is.
Normally PPAs are working great if you know how to use them and its not difficult either.
Google a little bit about Ubuntu and Linux etc on the web, there is an amount of information to learn.
I hope you will enjoy Ubuntu or whatever Linux. :)
Ask for help here on the forums, this community exists to support Ubuntu users and newbies.

---

### Post by gamendorf on 2011-05-24
Thanks again for the help.  As for Windows programs, I have experimented with Wine, Codeweaver's Crossover, and VMWare.  Unfortunately, none of them work in all situations.  I have to have both Crossover and VMWare to get things done.  I would love to just be done with Windows completely, but like I said, its my business applications that need it.  Oh well, it's not as convenient, but it works.

---

### Post by ivanovnegro on 2011-05-24
> **gamendorf said:**
> Thanks again for the help.  As for Windows programs, I have experimented with Wine, Codeweaver's Crossover, and VMWare.  Unfortunately, none of them work in all situations.  I have to have both Crossover and VMWare to get things done.  I would love to just be done with Windows completely, but like I said, its my business applications that need it.  Oh well, it's not as convenient, but it works.

That is the reason why actually most people are dual booting.

---

