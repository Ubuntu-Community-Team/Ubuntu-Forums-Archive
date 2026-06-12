---
title: "Update Manager PPA failed to Fetch ERROR (beginner)"
date: 2010-10-28
forum: General Help
---

### Post by awd01 on 2010-10-28
[SIZE=2]Hey folks, i have a small problem.
When the Update Manager is looking for updates i get an error that says:

[/SIZE][B][SIZE=3][COLOR=DarkOliveGreen]Could not download all repository indexes[/COLOR]
[/SIZE][/B]

[SIZE=2][COLOR=DarkOliveGreen]The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.[/COLOR]

[COLOR=DarkOliveGreen]Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/YOUR_UBUNTU_VERSION_HERE/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/YOUR_UBUNTU_VERSION_HERE/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/10.04/binary-i386/Packages.gz](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/10.04/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/LTS/binary-i386/Packages.gz](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/LTS/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR][/SIZE]


[SIZE=2]I remember some fails trying to install PPA in order to install J. Is this having to do with the error?[/SIZE]

---

### Post by plucky on 2010-10-28
> Not Found

The requested URL /jd-team/jdownloader/ubuntu/dists/YOUR_UBUNTU_VERSION_HERE/main/binary-i386/Packages.gz was not found on this server.
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80

That is the message given by the server you are trying to reach.

What version of Ubuntu are you running?

Your address doesn't have the version of Ubuntu you are using.

Edit your sources.list to include the version of Ubuntu you are running.

Good Luck

---

### Post by awd01 on 2010-10-28
> **plucky said:**
> That is the message given by the server you are trying to reach.

What version of Ubuntu are you running?

Your address doesn't have the version of Ubuntu you are using.

Edit your sources.list to include the version of Ubuntu you are running.

Good Luck

How can I edit this link? Where is it? Also, what is the proper way to write my ubuntu version in the link? I use ubuntu 10.04
Thank you very much for your time!

---

### Post by plucky on 2010-10-28
> How can I edit this link? Where is it? Also, what is the proper way to write my ubuntu version in the link? I use ubuntu 10.04
Thank you very much for your time! 

It depends where it is located.

Either **/etc/apt/sources.list** or **/etc/apt/sources.list.d/*.list**


To edit the file ```
gksudo gedit /etc/apt/sources.list
```
or ```
gksudo gedit /etc/apt/sources.list.d/<name of file>.list
```



Post output of ```
cat /etc/apt/sources.list
```

and ```
ls -l /etc/apt/sources.list.d/
```

so we can find the file that needs editing.

Or open Software Sources and find the PPA and edit it in that window.


Good Luck

---

### Post by awd01 on 2010-10-28
> **plucky said:**
> It depends where it is located.

Either **/etc/apt/sources.list** or **/etc/apt/sources.list.d/*.list**


To edit the file ```
gksudo gedit /etc/apt/sources.list
```or ```
gksudo gedit /etc/apt/sources.list.d/<name of file>.list
```Post output of ```
cat /etc/apt/sources.list
```and ```
ls -l /etc/apt/sources.list.d/
```so we can find the file that needs editing.

Or open Software Sources and find the PPA and edit it in that window.


Good Luck

[SIZE=2]I am confused.. I dont get it...:confused::confused: what am I doing now? I cant understand what I see. The results are these. First i have to tell you that i visit Software Sources, there was a line [http://ppa.launchpad.net/jd-team/jdownloader/YOUR_UBUNTU_VERSION](http://ppa.launchpad.net/jd-team/jdownloader/YOUR_UBUNTU_VERSION) and smth like that... edit the parts ''Distribution'' and ''Components'' now it is exactly like other 4... but why is there 4 same links? I installed it 4 times?? Pfff i am a n44b.

[SIZE=3]```
awd01@awd01-desktop:/$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu Ubuntu 10.04 LTS main
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu Ubuntu 10.04 LTS main
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu Ubuntu 10.04 LTS main
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu Ubuntu 10.04 LTS main
awd01@awd01-desktop:/$ ls -l /etc/apt/sources.list.d/
total 32
-rw-r--r-- 1 root root  67 2010-10-28 19:20 gwibber-daily-ppa-lucid.list
-rw-r--r-- 1 root root  65 2010-10-28 19:20 gwibber-daily-ppa-lucid.list.save
-rw-r--r-- 1 root root  69 2010-10-28 19:20 jd-team-jdownloader-lucid.list
-rw-r--r-- 1 root root  69 2010-10-28 19:20 jd-team-jdownloader-lucid.list.save
-rw-r--r-- 1 root root 172 2010-10-28 19:20 lucid-partner.list
-rw-r--r-- 1 root root 172 2010-10-28 19:20 lucid-partner.list.save
-rw-r--r-- 1 root root 269 2010-10-28 19:20 medibuntu.list
-rw-r--r-- 1 root root 269 2010-10-28 19:20 medibuntu.list.save
awd01@awd01-desktop:/$ 

```[/SIZE]       [/SIZE]

---

### Post by plucky on 2010-10-28
> # deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) Ubuntu 10.04 LTS main
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) Ubuntu 10.04 LTS main
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) Ubuntu 10.04 LTS main
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) Ubuntu 10.04 LTS main


The # in front of those lines means they are disabled.

Post output of ```
cat /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
``` as that is the one that is probably being used.

---

### Post by awd01 on 2010-10-28
[SIZE=2]> **plucky said:**
> The # in front of those lines means they are disabled.

Post output of ```
cat /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
``` as that is the one that is probably being used.[/SIZE] [SIZE=2]

Yes i disabled them after i fixed the ''YOUR_UBUNTU_VERSION''

The output is 
```
awd01@awd01-desktop:/$ cat /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
# deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu lucid main

```
[/SIZE]

---

### Post by plucky on 2010-10-28
> awd01@awd01-desktop:/$ cat /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list
# deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu lucid main](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu lucid main)

That is also disabled.Edit the file and remove the # from the line and then run ```
sudo apt-get update
``` to see if the problem has gone.

---

### Post by awd01 on 2010-10-28
[SIZE=2]> **plucky said:**
> That is also disabled.Edit the file and remove the # from the line and then run ```
sudo apt-get update
``` to see if the problem has gone.

I enabled the link [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) Ubuntu 10.04
and i removed the other 3 same links but i am still getting this message.

```
W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/10.04/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/LTS/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/Ubuntu/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
awd01@awd01-desktop:/$ 

```[/SIZE]

:confused:
[SIZE=2]



[/SIZE]

---

### Post by plucky on 2010-10-28
The address on those links are incorrect as the one in /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list is correct.```
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu lucid main
``` so either do what I said in the previous post or edit the one you left in sources.list to match the line above.

Good Luck

---

### Post by astrobob.tk on 2010-10-28
Speaking of such errors, i recently have been updating my system on a non secure wifi which I have been using just recently. I am now updating my system from my ethernet at home, but refreshing the repositories keeps giving me the error:
```
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```I didnt get such error before, though the disc was added.
Why did this happen & how can i solve it ?

---

### Post by plucky on 2010-10-29
> **astrobob.tk said:**
> Speaking of such errors, i recently have been updating my system on a non secure wifi which I have been using just recently. I am now updating my system from my ethernet at home, but refreshing the repositories keeps giving me the error:
```
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```I didnt get such error before, though the disc was added.
Why did this happen & how can i solve it ?

Please do not hijack someone else's thread as your error is completely different you should start your own.

To fix your problem,open **Software Sources** and un-tick the CDrom as a source,then reload the index files ```
sudo apt-get update
```

Good Luck

---

### Post by awd01 on 2010-10-29
[SIZE=2]> **plucky said:**
> The address on those links are incorrect as the one in /etc/apt/sources.list.d/jd-team-jdownloader-lucid.list is correct.```
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu lucid main
``` so either do what I said in the previous post or edit the one you left in sources.list to match the line above.

Good Luck[/SIZE] [SIZE=2]
[COLOR=DarkOrange]
Ok m8 i correct it and i dont occur any errors!! Thank you very much for your patience!!!!! Have a nice day![/COLOR][/SIZE]

---

### Post by astrobob.tk on 2010-10-29
> **plucky said:**
> Please do not hijack someone else's thread as your error is completely different you should start your own.

I'm sorry in this regard. You're absolutely write, but I thought the 2 problems might have a shared reason.


To fix your problem,open **Software Sources** and un-tick the CDrom as a source,then reload the index files ```
sudo apt-get update
```Good Luck[/QUOTE]

I already did this, but how can I keep my disc added ? When I tick it again, the error occurs, once more.

---

### Post by plucky on 2010-10-29
> I already did this, but how can I keep my disc added ? 

You can leave it ticked but you will always get the warning (not error) unless you actually put the CD in the drive when you do any updates or software installs.

Why do you want the CDrom to be a software source? 

The software on it has already been installed.

---

### Post by astrobob.tk on 2010-10-29
> **plucky said:**
> You can leave it ticked but you will always get the warning (not error) unless you actually put the CD in the drive when you do any updates or software installs.

that's when I get another error (below)


Why do you want the CDrom to be a software source? 

> The software on it has already been installed.

yeh, but not all packages. I might need certain packages that are already on the disc, thus saving me some time & network usage.


Here's what I get when I reload synaptic:

```
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386  (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386  (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

I tried "Add Cd-rom" in "Synaptic" but i get the error:

```
E: Failed to mount the cdrom.
```

& in terminal i get the error i posted before.

---

