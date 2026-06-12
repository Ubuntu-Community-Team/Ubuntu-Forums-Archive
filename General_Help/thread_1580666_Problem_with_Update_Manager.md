---
title: "Problem with Update Manager"
date: 2010-09-23
forum: General Help
---

### Post by kkelly77 on 2010-09-23
When Update Manager automatically runs on my system I get the following message. I'm still relatively new to Linux. Can anyone shed some light? My laptop is connected to the net when updates are trying to run.

K.

---

### Post by CharlesA on 2010-09-23
Can you post yer /etc/apt/sources.list in [noparse]```
 
```[/noparse] tags please.

---

### Post by kkelly77 on 2010-09-23
> **CharlesA said:**
> Can you post yer /etc/apt/sources.list in [noparse]&#91;code&#93; &#91;/code&#93;[/noparse] tags please.

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ie.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

### Post by CharlesA on 2010-09-23
It looks fine. Are you able to ping ie.archive.ubuntu.com?

```
ping -c 4 ie.archive.ubuntu.com
```

---

### Post by kkelly77 on 2010-09-23
> **CharlesA said:**
> It looks fine. Are you able to ping ie.archive.ubuntu.com?

```
ping -c 4 ie.archive.ubuntu.com
```

Yeah, no problems.

---

### Post by CharlesA on 2010-09-23
Ok, try running update manager again, it could be that the host was down when you tried before.

---

### Post by lkjoel on 2010-09-23
> **kkelly77 said:**
> When Update Manager automatically runs on my system I get the following message. I'm still relatively new to Linux. Can anyone shed some light? My laptop is connected to the net when updates are trying to run.

K.
The server may be down.

---

### Post by Vigh on 2010-09-23
Another important note is you can actually select the linux server closest to you, which will allow for a better more stable connection when updating. My ISP even has a server so doesn't use up my internet quota.

---

### Post by kkelly77 on 2010-09-23
> **CharlesA said:**
> Ok, try running update manager again, it could be that the host was down when you tried before.

Keep getting this message when it tries to run

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ie.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

Also when it is downloading package info, it it failing for certain files. I've no idea why.

---

### Post by kkelly77 on 2010-09-23
> **Vigh said:**
> Another important note is you can actually select the linux server closest to you, which will allow for a better more stable connection when updating. My ISP even has a server so doesn't use up my internet quota.

How do you select a specific server?

---

### Post by Vigh on 2010-09-23
Are you using 10.04 or anything before that? Its slightly different in the current beta version. Go to system- administration- software sources.

Then under the first tab of software sources Ubuntu Software. There should be an option download from: Select your country, then select the closest location to you or your own ISP. Hope this helps.

Regards

Ant

On beta 10.10 go to administration- synaptic- settings- repositories

---

### Post by lkjoel on 2010-09-23
System->Administration->Software Sources.
You check the sources that you want, and uncheck the sources that you do not want.

---

### Post by kkelly77 on 2010-09-23
> **Vigh said:**
> Are you using 10.04 or anything before that? Its slightly different in the current beta version. Go to system- administration- software sources.

Then under the first tab of software sources Ubuntu Software. There should be an option download from: Select your country, then select the closest location to you or your own ISP. Hope this helps.

Regards

Ant

On beta 10.10 go to administration- synaptic- settings- repositories

No luck unfortunately

---

### Post by Vigh on 2010-09-23
Are you actually running karmic koala? Or Lucid Lynx, it is possible you have some broken package links in software sources, which would mean you can safely ignore this message- try going back to software sources, click other software (2nd tab) get rid of anything that is not related to your distro. that is if your running lucid for example, get rid of any karmic software sources etc.

Make sure the first 4 boxes are ticked under the first tab

go to update click check (reload or refresh) and then try installing updates

otherwise under the 2nd tab, you could try clicking properties on all of the software sources listed and make sure in the properties they are pointing to the correct distro eg. lucid, just type the first word of the distro in to get it to work properly- eg. gutsy, karmic, lucid etc. in the distribution section, for the components section just type in- main, comment section can be left blank

go to update click check (reload or refresh) and then try installing updates

failing that, need to reconfigure the software sources file- sources.list

which im not 100% sure with, as I use my own server, not the one best for or closest to you

GOODLUCK

---

### Post by CharlesA on 2010-09-23
Can you run this in a terminal and post the output, please:

```
sudo apt-get update
```

@Vigh: All the karmic stuff is commented out in the sources.list file so I don't know why they are getting that error.

---

### Post by mc4man on 2010-09-23
Maybe just run in a terminal (have seen something similar once and a rare while in 10.10
```
sudo apt-get update
```

---

### Post by kkelly77 on 2010-09-24
> **Vigh said:**
> Are you actually running karmic koala? Or Lucid Lynx, it is possible you have some broken package links in software sources, which would mean you can safely ignore this message- try going back to software sources, click other software (2nd tab) get rid of anything that is not related to your distro. that is if your running lucid for example, get rid of any karmic software sources etc.

Make sure the first 4 boxes are ticked under the first tab

go to update click check (reload or refresh) and then try installing updates

otherwise under the 2nd tab, you could try clicking properties on all of the software sources listed and make sure in the properties they are pointing to the correct distro eg. lucid, just type the first word of the distro in to get it to work properly- eg. gutsy, karmic, lucid etc. in the distribution section, for the components section just type in- main, comment section can be left blank

go to update click check (reload or refresh) and then try installing updates

failing that, need to reconfigure the software sources file- sources.list

which im not 100% sure with, as I use my own server, not the one best for or closest to you

GOODLUCK

I'm using Ubuntu 10.04 LTS - the Lucid Lynx. Will try some of those solutions.

---

### Post by kkelly77 on 2010-09-24
> **CharlesA said:**
> Can you run this in a terminal and post the output, please:

```
sudo apt-get update
```@Vigh: All the karmic stuff is commented out in the sources.list file so I don't know why they are getting that error.

```

Hit http://ie.archive.ubuntu.com lucid Release.gpg
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IE     
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IE  
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IE    
Hit http://ie.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://ie.archive.ubuntu.com/ubuntu/ karmic-backports/main Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ karmic-backports/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ karmic-backports/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ karmic-backports/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com lucid-security Release.gpg                
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com lucid-proposed Release.gpg                
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_IE
Hit http://ie.archive.ubuntu.com lucid-backports Release.gpg                   
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_IE
Ign http://ie.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_IE
Hit http://ie.archive.ubuntu.com lucid Release                                 
Hit http://ie.archive.ubuntu.com lucid-updates Release                         
Hit http://ie.archive.ubuntu.com karmic-backports Release                      
Hit http://ie.archive.ubuntu.com lucid-security Release                        
Hit http://ie.archive.ubuntu.com lucid-proposed Release                        
Hit http://ie.archive.ubuntu.com lucid-backports Release                       
Hit http://ie.archive.ubuntu.com lucid/main Packages                           
Hit http://ie.archive.ubuntu.com lucid/restricted Packages                     
Hit http://ie.archive.ubuntu.com lucid/main Sources                            
Hit http://ie.archive.ubuntu.com lucid/restricted Sources                      
Hit http://ie.archive.ubuntu.com lucid/universe Packages                       
Hit http://ie.archive.ubuntu.com lucid/universe Sources                        
Hit http://ie.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://ie.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://ie.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://ie.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://ie.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://ie.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://ie.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://ie.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://ie.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://ie.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://ie.archive.ubuntu.com karmic-backports/main Packages                
Hit http://ie.archive.ubuntu.com karmic-backports/restricted Packages          
Hit http://ie.archive.ubuntu.com karmic-backports/universe Packages            
Hit http://ie.archive.ubuntu.com karmic-backports/multiverse Packages          
Hit http://ie.archive.ubuntu.com karmic-backports/main Sources                 
Hit http://ie.archive.ubuntu.com karmic-backports/restricted Sources           
Hit http://ie.archive.ubuntu.com karmic-backports/universe Sources             
Hit http://ie.archive.ubuntu.com karmic-backports/multiverse Sources           
Hit http://ie.archive.ubuntu.com lucid-security/main Packages                  
Hit http://ie.archive.ubuntu.com lucid-security/restricted Packages            
Hit http://ie.archive.ubuntu.com lucid-security/main Sources                   
Hit http://ie.archive.ubuntu.com lucid-security/restricted Sources             
Hit http://ie.archive.ubuntu.com lucid-security/universe Packages              
Hit http://ie.archive.ubuntu.com lucid-security/universe Sources               
Hit http://ie.archive.ubuntu.com lucid-security/multiverse Packages            
Hit http://ie.archive.ubuntu.com lucid-security/multiverse Sources             
Hit http://ie.archive.ubuntu.com lucid-proposed/restricted Packages            
Hit http://ie.archive.ubuntu.com lucid-proposed/main Packages                  
Hit http://ie.archive.ubuntu.com lucid-proposed/multiverse Packages            
Hit http://ie.archive.ubuntu.com lucid-proposed/universe Packages              
Hit http://ie.archive.ubuntu.com lucid-backports/restricted Packages           
Hit http://ie.archive.ubuntu.com lucid-backports/main Packages                 
Hit http://ie.archive.ubuntu.com lucid-backports/multiverse Packages           
Hit http://ie.archive.ubuntu.com lucid-backports/universe Packages             
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_IE              
Hit http://linux.dropbox.com lucid Release                     
Hit http://linux.dropbox.com lucid/main Packages               
Err http://archive.canonical.com karmic Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Ign http://archive.canonical.com/ubuntu/ karmic/partner Translation-en_IE
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_IE
Hit http://archive.canonical.com karmic Release
Hit http://archive.canonical.com lucid Release
Hit http://archive.canonical.com karmic/partner Packages
Hit http://archive.canonical.com karmic/partner Sources
Hit http://archive.canonical.com lucid/partner Packages
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Vigh on 2010-09-24
Just delete the Karmic lines from sources.list, you should not get that error message again. Also I think your system is up to date, its just still trying to look at Karmic-packages for some reason. So its not a major error and your computer is up to date.

open terminal
cd /etc/apt
sudo gedit sources.list

delete all karmic koala entries

save sources.list file

close and try to to check for updates

especially this one- Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)


you should no longer receive this error message, although it is nothing to worry about, (I think!) had similar problems, deleted all un-necessary sources and no more errors

---

### Post by kkelly77 on 2010-09-24
> **Vigh said:**
> Just delete the Karmic lines from sources.list, you should not get that error message again. Also I think your system is up to date, its just still trying to look at Karmic-packages for some reason. So its not a major error and your computer is up to date.

open terminal
cd /etc/apt
sudo gedit sources.list

delete all karmic koala entries

save sources.list file

close and try to to check for updates

especially this one- Err [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)


you should no longer receive this error message, although it is nothing to worry about, (I think!) had similar problems, deleted all un-necessary sources and no more errors

Removed all references to Karmic Koala but still getting the error - 

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg](http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.

However, there is no reference to archive.canonical.com in the sources.list file

---

### Post by BOBSta on 2010-10-05
I've been getting a similar problem with my 10.04 (lucid) 64-bit Ubuntu since yesterday morning.  I'm running "**Kernel Linux 2.6.32-25-generic**".

When I run update manager, it goes through the Starting Update Manager - Building data structures startup progress bar and leaves me in a blank update manager screen with no updates listed and telling me "The package information was last updated 5 days ago."  If I [Check], it sits checking for about 10 secs then produces error:

An error occurred

The following details are provided:
```
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://gb.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://gb.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


I've tried running:
```
sudo apt-get update
```

which gives me this output:
```
Get: 1 http://archive.canonical.com lucid Release.gpg
Get: 2 http://security.ubuntu.com lucid-security Release.gpg         
Get: 3 http://gb.archive.ubuntu.com lucid Release.gpg                
Get: 4 http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB
99% [4 Translation-en_GB bzip2 0B] [Waiting for headers] [Connecting to archive.canonical.com] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB                                            
Get: 5 http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                                     
79% [5 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB                        
Get: 6 http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB                            
66% [6 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB                               
Get: 7 http://archive.canonical.com lucid Release                                                   
Err http://archive.canonical.com lucid Release                         
  
Get: 8 http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
62% [8 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Get: 9 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
55% [9 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB   
Get: 10 http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
49% [10 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Get: 11 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB  
45% [11 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB      
Get: 12 http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
41% [12 Translation-en_GB bzip2 0B] [Waiting for headers] [Connecting to security.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB           
Get: 13 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB              
38% [13 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB    
Get: 14 http://security.ubuntu.com lucid-security Release                      
Err http://security.ubuntu.com lucid-security Release
  
Get: 15 http://gb.archive.ubuntu.com lucid-updates Release.gpg
Get: 16 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
43% [16 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Get: 17 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
41% [17 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Get: 18 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
38% [18 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Get: 19 http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
36% [19 Translation-en_GB bzip2 0B] [Connecting to gb.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Get: 20 http://gb.archive.ubuntu.com lucid Release                       
Err http://gb.archive.ubuntu.com lucid Release            
  
Get: 21 http://gb.archive.ubuntu.com lucid-updates Release
Err http://gb.archive.ubuntu.com lucid-updates Release
  
Fetched 80.8kB in 3s (25.8kB/s)
Reading package lists... Done
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://gb.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://gb.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


I can ping all the following successfully :
```
archive.canonical.com
security.ubuntu.com
gb.archive.ubuntu.com
```


Here is my /etc/apt/sources.list :
```
deb http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb http://packages.medibuntu.org/ lucid free non-free # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu lucid main # disabled on upgrade to lucid
```


So, it looks like the servers are available as they are pingable and this has been going on for two days.

Do I need to update the authentication keys?

{UPDATE}  I've just removed the extra disabled repositories from Other Software, re-loaded the repositories and now get a slightly shorter error :

```
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://gb.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://gb.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by BOBSta on 2010-10-07
Please ignore my last posting.

I've just discovered that my company's internal systems department had blocked internet access from my Ubuntu workstation's IP address as they didn't recognise and couldn't access it remotely from US! :mad:

These are Windows / Active Directory admins...

The fact that this workstation has been on the corporate LAN in UK since early 2007 didn't seem to matter!  Of course, if they actually bothered to talk to their UK based colleagues (who know all about it) they might be a little more respected... :(

Problem sorted now.  Update Manager working again. :)

---

