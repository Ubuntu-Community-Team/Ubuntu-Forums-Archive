---
title: "Ubuntu 9.10 - Internet Dialup with Winmodem"
date: 2010-01-17
forum: General Help
---

### Post by Mukoi on 2010-01-17
Hi,
I am new to Ubuntu and Linux.
I think that I like Ubuntu, but I don't think it likes me!
I can't get onto the internet with my "old fashioned" dialup that is preinstalled in my Dell Latitude.
In fact I can't find any reference to a dialup modem in Ubuntu 9.10.
Have done some research and it appears that my winmodem will not work with linux, but there maybe some complex way around this problem.
Can it be done?
If so, will someone help me with a step by step way of getting my modem to work for me.
I have a Conexant HDA D110 MDC V.92 modem.

---

### Post by sliketymo on 2010-01-17
Heres the best I can do,good luck to you.

[http://linmodems.org/](http://linmodems.org/)

---

### Post by SPr on 2010-01-17
You'll have to buy the Linuxant driver to get full speed but Dell offer a free full speed driver of their own. [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb)

Download it.
Open a terminal
```

sudo dpkg -i hsfmodem_7.68.00.09oem_i386.deb

```
Follow the prompts.
Reboot. 
I've never set up a dial-up modem on Linux so I'm hazy about the process but you will need the programs
pppd
pon
poff
Check they are already installed with:
```

sudo which pppd
sudo which pon
sudo which poff

```
On Debian I need to run those commands as root so I'll assume it's the same for Ubuntu.

Edit: I can't find a driver for anything later than Hardy at [http://linux.dell.com/files/ubuntu](http://linux.dell.com/files/ubuntu)
This may well be of help as well: [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

---

### Post by Mukoi on 2010-01-17
> **SPr said:**
> You'll have to buy the Linuxant driver to get full speed but Dell offer a free full speed driver of their own. [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb)

Download it.
Open a terminal
```

sudo dpkg -i hsfmodem_7.68.00.09oem_i386.deb

```Follow the prompts.
Reboot. 
I've never set up a dial-up modem on Linux so I'm hazy about the process but you will need the programs
pppd
pon
poff
Check they are already installed with:
```

sudo which pppd
sudo which pon
sudo which poff

```On Debian I need to run those commands as root so I'll assume it's the same for Ubuntu.

Edit: I can't find a driver for anything later than Hardy at [http://linux.dell.com/files/ubuntu](http://linux.dell.com/files/ubuntu)
This may well be of help as well: [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
Thank you.
Downloaded the file onto a USB and copied the file to my Ubuntu download folder.
Opened the terminal and got the following response:
error processing hsfmodem_7.68.00.09oem_i386.deb (--install):
Cannot access achieve: no such file or directory
Errors were encounted while processing: hsf........

Looked at the help info suggested.  Talked about "Preparation" which I don't know what that means.  There is also another file mentioned.  Also a warning about the drivers failing and "sound will most likely break".  Is that referring to physical damage?  Sounds a bit scary!

Checked:
pppd - /usr/sbin/pppd
pon - /usr/bin/pon
poff - /usr/bin/poff

---

### Post by SPr on 2010-01-17
Did you cd (change directory) into the directory where you downloaded the .deb file? cd /path/to/directory
Did you also check the link I posted? [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
What are the full errors?

We are not mind readers and can not see what is happening on your computer - you have to tell us.

---

### Post by Mukoi on 2010-01-17
> **SPr said:**
> Did you cd (change directory) into the directory where you downloaded the .deb file? cd /path/to/directory
Did you also check the link I posted? [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)
What are the full errors?

We are not mind readers and can not see what is happening on your computer - you have to tell us.
Sorry, it is frustrating trying to help people, like me, who don't really know what they are doing.  I'll try to be your eyes and hands, but unfortunately, I don't have your knowledge.
Let's start again.
I have deleted the partitions on my hard drive that had Ununtu 9.10 and reinstalled it.  So everything is clean.
The file you asked me to download, *hsfmodem_7.68.00.09oem_i386.deb* has been downloaded to my USB and I have copied this file to my Ubuntu downloads folder.  I can see it there.
I went to the terminal and typed, *sudo dpkg -i hsfmodem_7.68.00.09oem_i386.deb* and got the following response:
[I]error processing hsfmodem_7.68.00.09oem_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encounted while processing: [/I][I]hsfmodem_7.68.00.09oem_i386.deb
[/I]
Now, I am not too sure what you mean by cd (change directory) or how to do it.
I have printed and read *[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)* and I don't feel 'confident' about what I read.  Some terminology I don't understand and I am afraid that some physical damage will occur.  Also, I notice that another file is mentioned - refer step 5.

Will the modem be installed if I double click on the downloaded file: *hsfmodem_7.68.00.09oem_i386.deb* sitting in my Ubuntu downloads folder?

---

### Post by SPr on 2010-01-18
Sorry if I scared you :) I don't mind helping people who show that they have tried to help themselves before asking others for help.

You will not break the modem hardware with the instructions at [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant).

After studying those instructions and scratching my head for a while I think I've worked it out :)

Download:
[http://packages.ubuntu.com/karmic/amd64/build-essential/download](http://packages.ubuntu.com/karmic/amd64/build-essential/download) **if the PC is 64 bit or**
[http://packages.ubuntu.com/karmic/i386/build-essential/download](http://packages.ubuntu.com/karmic/i386/build-essential/download) **if it's 32 bit.**
then on the Ubuntu PC run
```

uname -r

```
That will give the kernel version the PC is running. Make a note of it.

Go to [http://packages.ubuntu.com/karmic/allpackages](http://packages.ubuntu.com/karmic/allpackages) and scroll down to the entries called "linux-headers" you will need the package called:
linux-headers-X
The X will have to match the kernel version you found earlier.

Download [www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip](www.linuxant.com/alsa-driver/archive/alsa-driver-linuxant-1.0.20.3/alsa-driver-linuxant_1.0.20.3_all.deb.zip)

Download [http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip](http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip)

Copy those four files to the Ubuntu PC. Open the directory you copied them to and double click the three .deb files.

Right Click the .zip file and choose "extract here". It will create new directory called hsfmodem-7.80.02.05-DiacoEdition

Open a terminal:
```

cd /path/to/hsfmodem-7.80.02.05-DiacoEdition
sudo make install
sudo hsfconfig

```
It appears that installing this will break pulse audio so 
[http://ubuntuforums.org/showpost.php?p=8258559&postcount=21](http://ubuntuforums.org/showpost.php?p=8258559&postcount=21)
explains how to fix it.

I apologise for thinking those instructions were straight forward - they aren't.

---

### Post by Mukoi on 2010-01-19
A lot of activity happening while doing this!

Tried to edit the file mentioned in *[http://ubuntuforums.org/showpost.php?p=8258559&postcount=21](http://ubuntuforums.org/showpost.php?p=8258559&postcount=21)* but the changes were not allowed.  I just went into the file and tried to change it, but I am sure that there is a "correct" way of doing it.

Should I now get some sort of icon or display that allows me to connect to the internet?

---

### Post by SPr on 2010-01-19
```

gksudo gedit /etc/pulse/default.pa

```

Did the installation throw any errors?

You will need [wvdial]([url=http://packages.ubuntu.com/karmic/wvdial) and all the dependencies and [pppconfig](http://packages.ubuntu.com/karmic/pppconfig) and all the dependencies for that. They may be on the Live CD so put the CD in and
```

sudo apt-get install wvdial pppconfig

```
if that fails then manually download them.

To set the modem up follow [this link](http://ubuntuforums.org/showpost.php?p=6933922&postcount=4). Start from "Once that decision is made, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:".

---

### Post by Mukoi on 2010-01-19
Thank you for all your help.

Successfully edited the file.

There may have been some errors when installing the files, but it was going so fast to take note.

Can't get to your link for wvdial.

When I tried to install wvdial got the following response:
[I]Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Package wvdial is not available, but is referred to by another package
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package wvdial has no installation canditate
[/I]
Can find *pppconfig *in my installed files.

Have printed your link about setting up the modem.  Will spend some time reading.

Will come back to all this later.

I am stuck!  I wish that I had your knowledge.

Wvdial is on the installation cd.  I copied the folder to my *downloads* folder and tried to install it as we did with the *hsfmodem* above, but unsuccessful.

Sorry, this must be frustrating for you.

---

### Post by Mukoi on 2010-01-20
I have done the pppconfig according to the link that you supplied.

I want to be prompted for my password, so I will edit and delete the line that was suggested (about the password).

Just got to get wvdialconfig done.

---

### Post by SPr on 2010-01-20
> 
Wvdial is on the installation cd

```

sudo apt-get install wvdial

```
or open Synaptic and install wvdial from there. All dependencies will be resolved and the program installed automagically.

---

### Post by Mukoi on 2010-01-20
Install was unsuccessful.  Refer following error message:

[I]Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main libwvstreams4.6-base 4.6-2
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main libwvstreams4.6-extras 4.6-2
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main libuniconf4.6 4.6-2
  Could not resolve 'au.archive.ubuntu.com'
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main wvdial 1.60.1+nmu2ubuntu1
  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base_4.6-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base_4.6-2_i386.deb)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6-2_i386.deb)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6-2_i386.deb)  Could not resolve 'au.archive.ubuntu.com'
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.60.1+nmu2ubuntu1_i386.deb)  Could not resolve 'au.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/I]

Nearly there!

---

### Post by SPr on 2010-01-21
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bkp
gksudo gedit /etc/apt/sources.list

```
Place a # sign before every line except the one that references the CD.
```

apt-get update
apt-get install wvdial

```
After the installation either completes or fails:
```

sudo cp /etc/apt/sources.list.bkp /etc/apt/sources.list

```
After all this I hope the modem works.

---

### Post by Mukoi on 2010-01-22
Source.list before changes:

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe main #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

Sources.list after changes:

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic main
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates main
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic universe
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-updates universe

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
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe main #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

Code:
apt-get update

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

I tried code:
sudo apt-get update

Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

Still can't get into wvdial.

Thank you for all your help SPr.  And thank you for your patience.

---

### Post by SPr on 2010-01-22
Oh hell, I assumed the CD would be recognised already

Insert the CD then

```

sudo apt-cdrom add

```
or
```

sudo apt-cdrom -d /media/cdrom0 add

```
assuming that the cdrom is mounted on /media/cdrom. To find out:
```

sudo mount

```
and look for a line similar to:
> 
/dev/hdb on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=spr)

Comparing the results of "sudo mount" before and after inserting the CD will give the answer.

Then try
```

sudo apt-get update
sudo apt-get install wvdial

```

---

### Post by GeorgeVita on 2010-01-22
Hi **Mukoi** and **SPr**, regarding **wvdial** and dependencies these are NOT included into LiveCD from 9.04 but exist on the DVD (see full list of [contents]("http://cdimage.ubuntu.com/releases/karmic/release/ubuntu-9.10-dvd-i386.list"))

Various options (excluding 'get the DVD'):

a. download 4 packages and install them manually (for Ubuntu 9.10 **i386**):
1. [http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-base/download](http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-base/download)
2. [http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-extras/download](http://packages.ubuntu.com/karmic/i386/libwvstreams4.6-extras/download)
3. [http://packages.ubuntu.com/karmic/i386/libuniconf4.6/download](http://packages.ubuntu.com/karmic/i386/libuniconf4.6/download)
4. [http://packages.ubuntu.com/karmic/i386/wvdial/download](http://packages.ubuntu.com/karmic/i386/wvdial/download)


b. get my **[wvdial910.zip]("http://www.acomelectronics.com/GeorgeVita/wvdial910.zip")** (aprox 1MB) for **i386** architecture

c.use Synaptic, menu File > 'Generate Package Download Script'
(you need a linux internet connected pc to get them)
>>> [More info]("http://ubuntuforums.org/showpost.php?p=8654157&postcount=8")<<<

Regards,
George

---

### Post by SPr on 2010-01-23
Thanks for clearing that up. I was under the impression wvdial was on the CD. It makes sense for it to be on there but perhaps it's missing for reasons of space.

---

### Post by Mukoi on 2010-01-23
I have a DVD with Ubuntu 9.10, OpenSUSE 11.2 and Mandriva on it.  I can see wvdial on the disk.

SPr, I did sudo mount:

/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=mukoi)

Also, sudo apt-get update

Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_AU
Reading package lists... Done

And, sudo apt-get install wvdial

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wvdial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wvdial has no installation candidate

---

### Post by Mukoi on 2010-01-23
Spr,

It seems that what GerogeVita is saying explains the difficulty in getting wvdial from my disk.

Is it ok with you if I download his zip file and try to install the package(s) to do the wvdialconfig?

---

### Post by SPr on 2010-01-24
Those links look good to me :)

---

### Post by Mukoi on 2010-01-25
The installs seemed to go ok.

Code:
sudo wvdialconf /etc/wvdial.conf

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
ttySHSF0<*1>: ATQ0 V1 E1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 Z -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySHSF0<*1>: Modem Identifier: ATI -- 56000
ttySHSF0<*1>: Speed 4800: AT -- OK
ttySHSF0<*1>: Speed 9600: AT -- OK
ttySHSF0<*1>: Speed 19200: AT -- OK
ttySHSF0<*1>: Speed 38400: AT -- OK
ttySHSF0<*1>: Speed 57600: AT -- OK
ttySHSF0<*1>: Speed 115200: AT -- OK
ttySHSF0<*1>: Speed 230400: AT -- OK
ttySHSF0<*1>: Speed 460800: AT -- OK
ttySHSF0<*1>: Max speed is 460800; that should be safe.
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   SHSF1 SHSF2 SHSF3 SHSF4 SHSF5 
Modem Port Scan<*1>: SHSF6 SHSF7 

Found a modem on /dev/ttySHSF0, using link /dev/modem in config.
Modem configuration written to /etc/wvdial.conf.
ttySHSF0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

I then viewed  /etc/wvdial.conf

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/modem
Baud = 460800

To try to get the modem to work.
Code:
wvdial /etc/wvdial.conf

--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer /etc/wvdial.conf] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

How do I specify the parameters for the 'phone, login and password?  I tried to edit /etc/wvdial.conf to show the 'phone no, and so on using code: gksudo gedit /etc/wvdial.conf.  The response was the same.

I also rechecked my pppconfig and the 'phone no. to dial, logon name and password are there.

---

### Post by t4thfavor on 2010-01-25
When I was doing this there was a graphical front end for wvdial that allowed you to put in the passwords and whatnot. I eventually gave up on my winmodems (2-3 years ago) and put in an IPCOP server with a US Robotics serial modem. I then shared it via wireless so I could wander around and use my dialup.

I have since moved to where cable is, so I no longer need the dialup. 


I think the app was called Gnome-ppp

---

### Post by GeorgeVita on 2010-01-26
Hi **Mukoi, SPr, t4thfavor**. Extra GUI package is gnome-ppp **i386**:
[http://packages.ubuntu.com/karmic/i386/gnome-ppp/download](http://packages.ubuntu.com/karmic/i386/gnome-ppp/download)

To edit /etc/wvdial.conf: ```
gksudo gedit /etc/wvdial.conf
``` place there data 'similar to': ```
[Dialer Defaults]
Modem = /dev/ttySHSF0
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Phone = 1234567890
Password = password
Username = user@provider.xx
Stupid mode = yes

``` Semicolons '**;'** removed.
Place appropriate phone, username, password.
Sometimes username is your phone number or your 'email' (user@provider.xx), if you are not sure ASK your provider.
**Stupid mode = yes** line added to bypass 'old login'.

To connect use '**sudo wvdial**' (default setup & configuration file).
Disconnect by pressing **Ctrl-C** at the same terminal window.
Sometimes Firefox starts in 'offline mode'. Check this from **ALT-F W**

Good luck!
George

---

### Post by Mukoi on 2010-01-26
It worked!

This is my first activity using my dialup.

Thank you George for all your help.

A special thanks to SPr for being so helpful and patient.  You have been really great!

I have installed Ubuntu on a laptop that is mainly used for my work.  I occasionally am required to access the internet from various locations.

Will I have to go through a similar procedure to access a wireless network?  I have noticed that often at my home/office I am automatically connected to a nearby neighbour's wireless unsecured network.  I quickly disconnect from this network as I think that it is unethical to use someone's network without their permission.  I don't know who this neighbour is.  But at another person's place I can access their network, but not the internet.  I notice that there is a lot of discussion on the forum about this, so I will see what I can find.

Once again thank you for all the assistance.

---

### Post by SPr on 2010-01-26
You're welcome.

---

### Post by t4thfavor on 2010-01-26
> **Mukoi said:**
> It worked!

This is my first activity using my dialup.

Thank you George for all your help.

A special thanks to SPr for being so helpful and patient.  You have been really great!

I have installed Ubuntu on a laptop that is mainly used for my work.  I occasionally am required to access the internet from various locations.

Will I have to go through a similar procedure to access a wireless network?  I have noticed that often at my home/office I am automatically connected to a nearby neighbour's wireless unsecured network.  I quickly disconnect from this network as I think that it is unethical to use someone's network without their permission.  I don't know who this neighbour is.  But at another person's place I can access their network, but not the internet.  I notice that there is a lot of discussion on the forum about this, so I will see what I can find.

Once again thank you for all the assistance.

Wireless is much less evil than winmodems are, assuming you have a decent supported wifi card, you should have no problems. From what you said you have been connected in the past, which means you system knows how to use your card. No worries, that was probably your biggest hurdle and your already past it.

---

