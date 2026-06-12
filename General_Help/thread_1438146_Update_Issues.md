---
title: "Update Issues"
date: 2010-03-24
forum: General Help
---

### Post by nightwolf2k5 on 2010-03-24
Hi guys,

Five days back, i got a notification on top right side mentioning "The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail."

So, i go ahead and click it.. it says it is downloading 1 of 19 files and after some time, i get the error mentioning "W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out"

I went into Software Sources and tried different servers from different countries, but there wasn't any luck.
I also unchecked the repository that was giving the problem but nothing was getting downloaded from other repositories as well.

I thought it would sort itself out but apparently it isn't. Please help.

I've attached a few screenshots.

---

### Post by Serpher on 2010-03-24
Try setting everything up back to it's default settings and run the following commands. Post the output if it doesn't work.

```
sudo apt-get upgrade
sudo apt-get update
```

---

### Post by nightwolf2k5 on 2010-03-24
Thanks but still does not work. The output is as shown below

```
avinashish@avinashish-laptop:~$ sudo apt-get upgrade
[sudo] password for avinashish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
avinashish@avinashish-laptop:~$ sudo apt-get update
Err http://archive.canonical.com karmic Release.gpg                                                                                   
  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out
Err http://archive.canonical.com karmic/partner Translation-en_GB                                                                     
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic Release.gpg                                                                                   
  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out
Err http://gb.archive.ubuntu.com karmic/main Translation-en_GB                            
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB                      
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic/universe Translation-en_GB                        
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB                      
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-updates Release.gpg                               
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB                    
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB              
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB                
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB              
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-security Release.gpg                              
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-security/main Translation-en_GB
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-security/restricted Translation-en_GB
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-security/universe Translation-en_GB
  Unable to connect to 87.89.43.193 3128:
Err http://gb.archive.ubuntu.com karmic-security/multiverse Translation-en_GB
  Unable to connect to 87.89.43.193 3128:
Err http://dl.google.com stable Release.gpg   
  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out
Err http://dl.google.com stable/main Translation-en_GB
  Unable to connect to 87.89.43.193 3128:
Reading package lists... Done                 
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release.gpg  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out

W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not connect to 87.89.43.193:3128 (87.89.43.193), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_GB.bz2  Unable to connect to 87.89.43.193 3128:

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas?

---

### Post by Ancanus on 2010-03-24
Hello,

please post the contents of ```
 /etc/apt/sources.list 
```

---

### Post by nightwolf2k5 on 2010-03-24
My sources.list file

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

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
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

---

### Post by john newbuntu on 2010-03-25
Your machine seems to be connecting to the wrong IP when queried for archive.canonical.com.  The correct IP is 91.189.88.33  .  This makes me feel that there is something wrong with the DNS lookup.
Try restarting your networking service
sudo /etc/init.d/networking restart
or
service networking restart
and see if that helps.  I am assuming you have rebooted your computer at least once in the last 5 days that you have been getting this message.  If not, it is worth a reboot.

If none of this solves your issue, I'll defer this issue to someone else who has experienced and solved this.

---

### Post by nightwolf2k5 on 2010-03-25
Thanks. I did everything you asked.. sudo /etc/init.d/network restart, i rebooted my laptop and also switched off and switched on my router but i am still faced with the same issue.

It was updating normally last week and i did not make any change so what could have changed?

---

### Post by nightwolf2k5 on 2010-03-26
sorry to bump..

But anybody with any ideas on how to get this working?

---

### Post by nightwolf2k5 on 2010-03-26
Hello,

After a lot of head banging listening to Metallica, a light bulb inside my head switched on and I have finally managed to fix this issue.

The problem was with a network proxy. Around two weeks ago, I had been playing around with the network proxy thing (System --> Preferences --> Network Proxy) and at some point during the "playing around" i had clicked "Apply System Wide". And when i wasn't able to get the proxy working, i switched back to Direct Internet Connection without clicking the "Apply System Wide" button again. And since the internet seemed to work, i thought everything was good (But apparently the updates weren't).

So i went back to network proxy and clicked on the Apply System Wide button again and checked for updates. And it worked!! :)

When in doubt.. headbang!! :P

Thanks guys.

---

