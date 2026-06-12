---
title: "Ubuntu isn't updating for last 20 days"
date: 2012-08-21
forum: General Help
---

### Post by uzumakifahim on 2012-08-21
Hi,
I'm facing a very annoying problem while trying to update my Ubuntu 12.04 for last 20 days. When I'm clicking the **Check** button in the Update Manager window, it starts to fetch the new update information but after almost 1 minute a new dialogue  box is opens and says that
```

Failed to download repository information

Check your Internet connection.


W:Failed to fetch http://ppa.launchpad.net/https/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/https/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```**Important point is that, my Internet connection is perfectly OK.** I can do browse and anything else. 

I don't understand why this is happening and how can I solve this. Please anyone help me. Thanks in advance.

---

### Post by papibe on 2012-08-21
Hi uzumakifahim.

It looks like there's a problem with the source files.

Could you post the result of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by uzumakifahim on 2012-08-21
Thanks for your quick reply. Here is the output 

```
/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
    41    deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
    42    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security universe
    43    deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
    44    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu precise partner
    51    deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main
    57    deb http://www.remastersys.com/ubuntu precise main

/etc/apt/sources.list.d/merlwiz79-cinnamon-ppa-precise.list


/etc/apt/sources.list.d/dropbox.list

     1    deb http://linux.dropbox.com/ubuntu precise main

/etc/apt/sources.list.d/spideroak.com.sources.list

     1    deb http://apt.spideroak.com/ubuntu-spideroak-hardy/ release restricted
     2    

/etc/apt/sources.list.d/https-ppa-precise.list

     1    deb http://ppa.launchpad.net/https/ppa/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/https/ppa/ubuntu precise main

/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list

     1    deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main

/etc/apt/sources.list.d/opera.list

     1    # This file makes sure that Opera Browser is kept up-to-date
     2    # as part of regular system upgrades
     3    
     4    deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
     5    
     6    # The line above will make sure you get all final public releases.
     7    # Uncomment the following line if you want to get alpha and beta
     8    # releases, too.
     9    
    10    # deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb http://dl.google.com/linux/talkplugin/deb/ stable main

```Hope this info will help you to understand the problem.

---

### Post by sandyd on 2012-08-21
> **uzumakifahim said:**
> Thanks for your quick reply. Here is the output 

```
/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
    41    deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
    42    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security universe
    43    deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
    44    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu precise partner
    51    deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main
    57    deb http://www.remastersys.com/ubuntu precise main

/etc/apt/sources.list.d/merlwiz79-cinnamon-ppa-precise.list


/etc/apt/sources.list.d/dropbox.list

     1    deb http://linux.dropbox.com/ubuntu precise main

/etc/apt/sources.list.d/spideroak.com.sources.list

     1    deb http://apt.spideroak.com/ubuntu-spideroak-hardy/ release restricted
     2    

/etc/apt/sources.list.d/https-ppa-precise.list

     1    deb http://ppa.launchpad.net/https/ppa/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/https/ppa/ubuntu precise main

/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list

     1    deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main

/etc/apt/sources.list.d/opera.list

     1    # This file makes sure that Opera Browser is kept up-to-date
     2    # as part of regular system upgrades
     3    
     4    deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
     5    
     6    # The line above will make sure you get all final public releases.
     7    # Uncomment the following line if you want to get alpha and beta
     8    # releases, too.
     9    
    10    # deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)

/etc/apt/sources.list.d/google-talkplugin.list

     1    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2    # You may comment out this entry, but any other modifications may be lost.
     3    deb http://dl.google.com/linux/talkplugin/deb/ stable main

```Hope this info will help you to understand the problem.
You have a https ppa, but the ppa itself does not exist.

Deleting it should fix the errors.
```

sudo rm /etc/apt/sources.list.d/https-ppa-precise.list
sudo apt-get update

```

---

### Post by uzumakifahim on 2012-08-21
WOW! Your solution works perfect for me. Thanks for this great help.

---

### Post by uzumakifahim on 2012-08-29
The previous problem was for my desktop, now I'm facing almost same problem with my laptop. Update Manager is again showing :


[B]Failed to download package files
check your internet connection[/B]

Details
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.5.3-0ubuntu3_all.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.5.3-0ubuntu3_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.9-1ubuntu2.1_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4_4.8.9-1ubuntu2.1_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity_2.10.19_i386.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity-frontend-debconf_2.10.19_all.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity-frontend-kde_2.10.19_all.deb 404  Not Found [IP: 91.189.91.30 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubiquity/ubiquity-ubuntu-artwork_2.10.19_all.deb 404  Not Found [IP: 91.189.91.30 80]

```

I found for errors in sources.list file, it seems everything is normal. There is not https entry, so previous solution of this thread is not works here. 

**Sources.list details:**

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://www.remastersys.com/ubuntu precise main
```

Anyone please help. Thanks to all.

---

### Post by QIII on 2012-08-29
The first file on your list does not exist, but libcups2_1.5.3-0ubuntu4_i386.deb does.

In the terminal, do

```
sudo apt-get update
```and then try 
```
sudo apt-get dist-upgrade
```

---

### Post by uzumakifahim on 2012-08-30
Thanks for your reply, but I don't understand what do you mean by "The first file on your list". Could you please clarify? I'll run the commands and post the updates here. Thanks again.

---

### Post by uzumakifahim on 2012-08-30
I have ran ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
```. It was successful, but still my update manager showing that "**package information was last updated 27 days ago**". No matter how many times I've clicked check button to update the information, the message is in there. Moreover, a new notification icon ( red exclamation sign) is now on the top panel, just beside the clock.  I don't know what is happening. Please anyone help me to solve this problem.

Thanks.

---

### Post by uzumakifahim on 2012-08-30
When I'm clicking on the **check** button, after a few seconds it' showing the following 
```
W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I can't solve this problem. Please anyone help me.

---

### Post by plucky on 2012-08-31
> **uzumakifahim said:**
> When I'm clicking on the **check** button, after a few seconds it' showing the following 
```
W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en  Encountered a section with no Package: header
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I can't solve this problem. Please anyone help me.

From a terminal run ```
sudo rm -vf /var/lib/apt/lists/partial/*
``` as that directory needs to be empty, and then run ```
sudo apt-get update && sudo apt-get upgrade
``` and post the output.

Good Luck

---

### Post by uzumakifahim on 2012-09-01
Really thanks for your reply. Here is the output. 
```
fahim@fahim-NF208:~$ sudo rm -vf /var/lib/apt/lists/partial/*
[sudo] password for fahim: 
removed `/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg.reverify'
removed `/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-security_Release.gpg.reverify'
removed `/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg.reverify'
removed `/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages.decomp.FAILED'
removed `/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en.decomp.FAILED'
fahim@fahim-NF208:~$ sudo apt-get update
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://deb.opera.com stable InRelease                                      
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://www.remastersys.com precise InRelease                               
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Get:2 http://linux.dropbox.com precise Release [2,603 B]                       
Hit http://deb.opera.com stable Release                                        
Hit http://www.remastersys.com precise/main i386 Packages                      
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:3 http://linux.dropbox.com precise/main i386 Packages [1,029 B]            
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://www.remastersys.com precise/main TranslationIndex                   
Ign http://us.archive.ubuntu.com precise-security InRelease                    
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Get:5 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]        
Hit http://us.archive.ubuntu.com precise Release                               
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:6 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://deb.opera.com stable/non-free Translation-en                        
Get:7 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://us.archive.ubuntu.com precise-backports Release                     
Ign http://www.remastersys.com precise/main Translation-en_US                  
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Ign http://www.remastersys.com precise/main Translation-en                     
Get:8 http://us.archive.ubuntu.com precise-security Release [49.6 kB]          
Ign http://linux.dropbox.com precise/main Translation-en                       
Get:9 http://us.archive.ubuntu.com precise-security Release [49.6 kB]          
Get:10 http://us.archive.ubuntu.com precise-security Release [49.6 kB]         
Get:11 http://us.archive.ubuntu.com precise-security Release [49.6 kB]         
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:12 http://us.archive.ubuntu.com precise-updates/main Sources [159 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/main Sources [159 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:15 http://us.archive.ubuntu.com precise-updates/universe Sources [50.1 kB] 
Get:16 http://us.archive.ubuntu.com precise-updates/universe Sources [50.1 kB] 
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:18 http://us.archive.ubuntu.com precise-updates/main i386 Packages [379 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/main i386 Packages [379 kB]
Get:20 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:21 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Get:22 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [127 kB]
Get:23 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                       
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                 
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                   
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                 
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex              
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Get:24 http://us.archive.ubuntu.com precise-security/main Sources [41.0 kB]
Get:25 http://us.archive.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:26 http://us.archive.ubuntu.com precise-security/universe Sources [12.2 kB] 
Get:27 http://us.archive.ubuntu.com precise-security/multiverse Sources [1,386 B]           
Get:28 http://us.archive.ubuntu.com precise-security/main i386 Packages [162 kB]            
Get:29 http://us.archive.ubuntu.com precise-security/restricted i386 Packages [3,968 B]     
Get:30 http://us.archive.ubuntu.com precise-security/universe i386 Packages [41.6 kB]       
Get:31 http://us.archive.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]     
Hit http://us.archive.ubuntu.com precise-security/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex               
Hit http://us.archive.ubuntu.com precise-security/restricted TranslationIndex               
Hit http://us.archive.ubuntu.com precise-security/universe TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/main Translation-en                                
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                          
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                          
Hit http://us.archive.ubuntu.com precise/universe Translation-en                            
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                        
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                  
Get:32 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [1,484 B]     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                    
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                      
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                  
Hit http://us.archive.ubuntu.com precise-security/main Translation-en                       
Hit http://us.archive.ubuntu.com precise-security/multiverse Translation-en                 
Hit http://us.archive.ubuntu.com precise-security/restricted Translation-en                 
Hit http://us.archive.ubuntu.com precise-security/universe Translation-en                   
Fetched 413 kB in 1min 30s (4,581 B/s)                                                      
Reading package lists... Done
fahim@fahim-NF208:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Please reply quickly. Thanks again.

---

### Post by NikTh on 2012-09-01
> **uzumakifahim said:**
>                
```
Fetched 413 kB in 1min 30s (4,581 B/s)                                                      
Reading package lists... Done
fahim@fahim-NF208:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```Please reply quickly. Thanks again.[/code]

Hello. 

It seems Ok. What is the problem now ? 

Thanks

---

### Post by fubar42 on 2012-09-01
I've been having similar problems for about 3 weeks in New Zealand. 3 Ubuntu machines all suffer the same problem (2 workstations and a server).

<code>

Err [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise-updates/multiverse i386 Packages
  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
  404  Not Found [IP: 91.189.92.190 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  ) [IP: 91.189.92.190 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.190 80]
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) precise/multiverse Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en_NZ
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  502  Proxy Error ( The Uniform Resource Locator (URL) does not use a recognized protocol. Either the protocol is not supported or the request was not typed correctly. Confirm that a valid protocol is in use (for example, HTTP for a Web request).  )

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://nz.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  404  Not Found
</code>

---

### Post by uzumakifahim on 2012-09-01
My problem was with the graphical Update Manager. When I was trying to update using graphical Update Manager, after some time it was showing it could not connect to the internet. Surprisingly, from today morning, it seems that problem has been solved, because graphical update manager works fine and showing that my system is fully updated and no new updates to install.

I don't know what's the reason behind this problem. Please could anyone tell me what's the reason?

Thanks.

---

### Post by plucky on 2012-09-02
> I don't know what's the reason behind this problem. Please could anyone tell me what's the reason?

The Update Manager left a file in the /partial directory that it was not able to correct as it didn't exist on the repositories.When you ran the "sudo rm" command,it deleted the file that the Update Manager was having problems with,so there was no more problems and Update Manager was able to run correctly.

This sometimes happens if there is a problem on the download repository or the repository is out of sync with the main repository.

Usually removing the .list files fixes the problem as the Update Manger has to download a new set of .list files.

Good Luck

---

### Post by uzumakifahim on 2012-09-02
> **plucky said:**
> The Update Manager left a file in the /partial directory that it was not able to correct as it didn't exist on the repositories.When you ran the "sudo rm" command,it deleted the file that the Update Manager was having problems with,so there was no more problems and Update Manager was able to run correctly.

This sometimes happens if there is a problem on the download repository or the repository is out of sync with the main repository.

Usually removing the .list files fixes the problem as the Update Manger has to download a new set of .list files.

Good Luck
Really thanks for your great reply. 

Good luck to you also.

---

### Post by uzumakifahim on 2012-09-23
Again I'm facing this irritating problem. I wasn't logged in Ubuntu for last 1 week, now I'm back to Ubuntu and facing problem with update. I'm getting the following error message.

```
W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I need a permanent solution to this problem. Help anyone, please.

---

### Post by uzumakifahim on 2012-09-24
Is there anyone, who can tell me, what's the meaning of this line.

```
W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
```

I would be really grateful to him.

Thanks in advance.

---

### Post by uzumakifahim on 2012-09-24
WOW! Problem is solved! Actually this problem is same as the previous one. It's my fault that I understand previously. Now issue is solved using the solution mentioned in this thread before. 

Thanks to everyone.

---

### Post by kaurie on 2012-09-25
:D

Thanks guys for your clear explanlations. 

I searched, found, and you solved my own problem.

It is nice when you are totally stuck to have this kind of good advice available!!

---

### Post by ChristopherAdams on 2012-10-06
I've been having problems updating Ubuntu as well. I tried the following command, as suggested above:
 
```
sudo rm -vf /var/lib/apt/lists/partial/*
```
 
This removed a bunch of files, but the OS still won't upgrade.
 
Here are the error messages I get from running "apt-get update --fix missing":
 
"W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. 
GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>
 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. 
GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 
Ubuntu Archive Automatic Signing Key <[EMAIL="ftpmaster@ubuntu.com"]ftpmaster@ubuntu.com[/EMAIL]>
 
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release) 
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release](http://security.ubuntu.com/ubuntu/dists/precise-security/Release) 
 
W: Some index files failed to download. They have been ignored, or old ones used instead."
 
Any help would be appreciated.
-Christopher Adams.

---

### Post by uzumakifahim on 2012-10-28
Again I'm facing problem with updating software. This time I've installed Ubuntu 12.04 newly on my laptop. After the installation I've run updates several times. I can install new software & updates, but every time when I'm attempt to check for new updates, it's showing the following message 

```
W: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

Interesting point is that after showing this message I'm getting new updates and can install those without problems.

**But my main problem is with Ubuntu One, when I'm running the Ubuntu One applet to setup Ubuntu One on my laptop, it's also showing the same message and installation is failed again and again.**

I've tried with the command below

```
sudo rm -vf /var/lib/apt/lists/partial/*
```

but the result is same. I need to solve this problem and install Ubuntu One on laptop. 

Please for your help. Thanks.

---

### Post by JohnDillinger43 on 2013-04-18
Just wanted to note that I was having the same problem, and this fixed it.  Thanks plucky!

---

### Post by vigyani on 2013-10-27
Hi

This worked for me.

thanks


> **plucky said:**
> From a terminal run ```
sudo rm -vf /var/lib/apt/lists/partial/*
``` as that directory needs to be empty, and then run ```
sudo apt-get update && sudo apt-get upgrade
``` and post the output.

Good Luck

---

### Post by alexandru-gnatiuc on 2014-06-07
> **vigyani said:**
> Hi,  This worked for me.  thanks

I tried the commands

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo rm -vf /var/lib/apt/lists/partial/*[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]
```

But still have the same error message:

> W:Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks for any help.

---

### Post by plucky on 2014-06-08
> W:Failed to fetch [http://ppa.launchpad.net/gwendal-leb...-i386/Packages](http://ppa.launchpad.net/gwendal-leb...-i386/Packages) 404 Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

Welcome to the forum.

That message usually means the repository is not available as the owner of the PPA has moved it or changed the name and it is not relevant anymore.

Open your **Software Sources** and disable the PPA by unticking the box.

The developer has changed the PPA from "cinnamon-stable" to cinammon-nightly"

See [Here](http://ppa.launchpad.net/gwendal-lebihan-dev/)

After you have disabled it,if you run ```
sudo apt-get update && sudo apt-get upgrade
``` and see if you get the same error.

Good Luck

---

### Post by MrSteve on 2014-06-08
i believe that ubuntu one has shut down and is no longer available ...

[https://one.ubuntu.com/shutdown/](https://one.ubuntu.com/shutdown/)

---

### Post by alexandru-gnatiuc on 2014-06-08
> **plucky said:**
> Welcome to the forum.

That message usually means the repository is not available as the owner of the PPA has moved it or changed the name and it is not relevant anymore.

Open your **Software Sources** and disable the PPA by unticking the box.

The developer has changed the PPA from "cinnamon-stable" to cinammon-nightly"

See [Here]("http://ppa.launchpad.net/gwendal-lebihan-dev/")

After you have disabled it,if you run ```
sudo apt-get update && sudo apt-get upgrade
``` and see if you get the same error.

Good Luck

Plucky, thanks for your quick reply and a very clear answer.
 I disabled the source link and I do not get any error message now.

But still I would like to ask if now I have to introduce there in the source list a new link with the updated link? It is not a critical link? The system will automatically find the new link it needed?

Thank you for the help and explanations.

---

