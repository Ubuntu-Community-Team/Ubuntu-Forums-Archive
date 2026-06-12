---
title: "Help!"
date: 2009-12-08
forum: General Help
---

### Post by Irishst on 2009-12-08
I've never used linux before, but I have a laptop which won't boot into windows (says critical file is missing bla bla, tried everything)

Anyway I have ubuntu downloaded, if I was to boot ubuntu from disk, would I be able to get files that were in My Documents while I was using windows?

Thanks

---

### Post by callan79 on 2009-12-08
> **Irishst said:**
> Anyway I have ubuntu downloaded, if I was to boot ubuntu from disk, would I be able to get files that were in My Documents while I was using windows?


Yep - if you boot from an Ubuntu Live CD, then click PLACES >> COMPUTER, you should see icons that refer to your computer's hard disk. Just double click to open these drives.

Then, put a USB stick into your machine, and copy all the data to the USB stick.

Once you're done, double click the INSTALL icon on your desktop, and let the partitioner do a "side by side" install - this way when your computer starts you'll be given the choice of Windows or Ubuntu.

Of course if you want to just get rid of Windows and run Ubuntu only, tell the partitioner to use the entire disk. Just make sure you've got ALL your data copied elsewhere first!

Cheers
Callan

---

### Post by Irishst on 2009-12-08
> **callan79 said:**
> Yep - if you boot from an Ubuntu Live CD, then click PLACES >> COMPUTER, you should see icons that refer to your computer's hard disk. Just double click to open these drives.

Then, put a USB stick into your machine, and copy all the data to the USB stick.

Once you're done, double click the INSTALL icon on your desktop, and let the partitioner do a "side by side" install - this way when your computer starts you'll be given the choice of Windows or Ubuntu.

Of course if you want to just get rid of Windows and run Ubuntu only, tell the partitioner to use the entire disk. Just make sure you've got ALL your data copied elsewhere first!

Cheers
Callan

Thanks just copied my data to usb.

If I want to run Ubuntu only and leave no traces of windows and all its associated files, will following you're method do the job?

---

### Post by Palanthas on 2009-12-08
> **Irishst said:**
> 
If I want to run Ubuntu only and leave no traces of windows and all its associated files, will following you're method do the job?

Yup! If you do as callan79 said and choose to use the entire disk for install, Ubuntu will format the drive and then install.

Hope it goes well for you! Welcome to Ubuntu! ;)

---

### Post by Irishst on 2009-12-08
Thanks!

---

### Post by Irishst on 2009-12-08
Further help needed please.

I'm trying to get VLC Media Player for Ubuntu 9.10

I click applications>accesories>terminal
and type in 
sudo apt-get install vlc vlc-plugin-esd
but it won't work. Any ideas?

---

### Post by rahilm on 2009-12-08
Try Applications>Ubuntu Software Center and then search for vlc

---

### Post by Irishst on 2009-12-08
No Terminal Commands ever work for me, and I'm pretty sure I'm typing everything in properly. Any suggestions or ways of checking what I'm doing wrong?

---

### Post by lisati on 2009-12-08
> **rahilm said:**
> Try Applications>Ubuntu Software Center and then search for vlc

+1: it doesn't normally need the command line/terminal, and is done from the graphical desktop.

---

### Post by Irishst on 2009-12-08
This is what I get when I try through Software Center


[IMG]http://img691.imageshack.us/img691/2330/screenshotubuntusoftwar.png[/IMG]

---

### Post by Palanthas on 2009-12-08
Hmm... odd... There should be a button below the "Price: Free" line.

Can you install any other programs through Ubuntu Software Center, or is it just VLC that is missing the install button?

---

### Post by Palanthas on 2009-12-08
```
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
```

Give that a shot...

---

### Post by callan79 on 2009-12-08
> **Palanthas said:**
> ```
sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc
```

Give that a shot...


If I had to guess, I might say that your repositories aren't up to date.

If you still have trouble installing the above, can you do this :

```
cat /etc/apt/sources.list
```

and post the results here.

Also do 

```
sudo apt-get update
```

and report any errors ...

Cheers
CD

---

### Post by Irishst on 2009-12-09
> **callan79 said:**
> If I had to guess, I might say that your repositories aren't up to date.

If you still have trouble installing the above, can you do this :

```
cat /etc/apt/sources.list
```and post the results here.

```
stan@stan-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ie.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

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

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```> **callan79 said:**
> Also do 

```
sudo apt-get update
```and report any errors ...

Cheers
CD

I did this after the above one:

```
sudo apt-get update
[sudo] password for stan: 
0% [Connecting to ie.archive.ubuntu.com] [Connecting to security.ubuntu.com]
0% [Connecting to ie.archive.ubuntu.com] [Connecting to security.ubuntu.com]
Hit http://ie.archive.ubuntu.com karmic Release.gpg                         
Ign http://ie.archive.ubuntu.com karmic/main Translation-en_IE              
Ign http://ie.archive.ubuntu.com karmic/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com karmic/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com karmic/multiverse Translation-en_IE
Get:1 http://security.ubuntu.com karmic-security Release.gpg [189B]
Hit http://ie.archive.ubuntu.com karmic-updates Release.gpg
Ign http://ie.archive.ubuntu.com karmic-updates/main Translation-en_IE
Ign http://ie.archive.ubuntu.com karmic-updates/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com karmic-updates/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com karmic-updates/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com karmic Release
Ign http://security.ubuntu.com karmic-security/main Translation-en_IE
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_IE
Ign http://security.ubuntu.com karmic-security/universe Translation-en_IE
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com karmic-updates Release             
Get:2 http://security.ubuntu.com karmic-security Release [44.1kB]   
Hit http://ie.archive.ubuntu.com karmic/main Packages                     
Hit http://ie.archive.ubuntu.com karmic/restricted Packages               
Hit http://ie.archive.ubuntu.com karmic/main Sources  
Hit http://ie.archive.ubuntu.com karmic/restricted Sources
Get:3 http://security.ubuntu.com karmic-security/main Packages [33.2kB]
Get:4 http://ie.archive.ubuntu.com karmic/universe Packages [5,133kB]
Get:5 http://security.ubuntu.com karmic-security/restricted Packages [14B]     
Get:6 http://security.ubuntu.com karmic-security/main Sources [9,475B]         
Get:7 http://security.ubuntu.com karmic-security/restricted Sources [14B]      
Get:8 http://security.ubuntu.com karmic-security/universe Packages [13.6kB]
Get:9 http://security.ubuntu.com karmic-security/universe Sources [1,622B]     
Get:10 http://security.ubuntu.com karmic-security/multiverse Packages [1,666B] 
Get:11 http://security.ubuntu.com karmic-security/multiverse Sources [575B]
Get:12 http://ie.archive.ubuntu.com karmic/universe Sources [2,795kB]          
Get:13 http://ie.archive.ubuntu.com karmic/multiverse Packages [190kB]         
Get:14 http://ie.archive.ubuntu.com karmic/multiverse Sources [116kB]          
Get:15 http://ie.archive.ubuntu.com karmic-updates/main Packages [109kB]       
Get:16 http://ie.archive.ubuntu.com karmic-updates/restricted Packages [14B]   
Get:17 http://ie.archive.ubuntu.com karmic-updates/main Sources [32.5kB]       
Get:18 http://ie.archive.ubuntu.com karmic-updates/restricted Sources [14B]    
Get:19 http://ie.archive.ubuntu.com karmic-updates/universe Packages [63.4kB]  
Get:20 http://ie.archive.ubuntu.com karmic-updates/universe Sources [14.3kB]   
Get:21 http://ie.archive.ubuntu.com karmic-updates/multiverse Packages [1,616B]
Get:22 http://ie.archive.ubuntu.com karmic-updates/multiverse Sources [1,223B] 
Fetched 5,465kB in 55s (98.8kB/s)                                              
Reading package lists... Done
```

---

### Post by callan79 on 2009-12-09
Well, the good news is that your sources.list looks OK, and your 'update' went through just fine (no errors).

At the risk of trying something that's already failed, can you try :

```
apt-cache search vlc
```

And just for the sake of it :

```
apt-cache search mozilla
```

And then :

```
sudo apt-get install vlc
```

I know that last one has failed for you in the past, so I'd like to see what the others do.

Cheers
CD

---

