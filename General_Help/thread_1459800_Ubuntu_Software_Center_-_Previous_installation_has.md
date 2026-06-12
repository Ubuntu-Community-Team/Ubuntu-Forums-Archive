---
title: "Ubuntu Software Center - Previous installation hasn't been completed?"
date: 2010-04-21
forum: General Help
---

### Post by rcweinkauf on 2010-04-21
When I'm in the Ubuntu software center and I try to install a new app / game, It gives me the message:

"The installation could have failed because of an error in the corresponding software package or it was canceled in an unfriendly way. You have to repair this before you can install or remove any further software."

How would I go about finding and repairing the problem?
I'm fairly new to Ubuntu, and would greatly appreciate some advice. THIS OS IS AMAZING!!  :)

---

### Post by zvacet on 2010-04-22
In applications>accessories>terminal type

```
sudo dpkg --configure -a
```

and 

```
sudo apt-get -f install
```

If you get any errors from these commands,please post them here.Also if you get errors post output of 

```
cat /etc/apt/sources.list
```

---

### Post by Akira Takano on 2010-04-25
Heres the ouptput of file /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

I upgraded from Karmic(9.10) to Lucid(10.4).

---

### Post by Sef on 2010-04-25
What happened when you tried the commands from post 2?

---

### Post by Akira Takano on 2010-04-25
Command: sudo dpkg --configure -a

Output: dpkg: parse error, in file '/var/lib/dpkg/updates/0009' near line 2:
 file details field `Size' not allowed in status file

command: sudo apt-get -f install

Output: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Akira Takano on 2010-04-27
Any help with this issue is greatly appreciated. This issue is preventing me from installing and removing software. That includes Update Manager.

---

### Post by Akira Takano on 2010-04-27
In the search for answers to this issue, I have found the reason my systems condition has deteriorated (at least in my case). I found evidence of a malicious Root-Kit on my system.

How ever, I am still devoted to this issue, and ensuring other members of the community know how to solve this issue.

---

### Post by nialui on 2010-05-02
thanks zvacet, that works for me

---

### Post by ubeautu on 2010-05-03
Yeah I stuffed software center up by installing a the flash plug in for Mozilla but i already had the plug-in installed for flash10 from 9.10 (I did the update to 10.04) and I didn't realise because it was further down the list of software. Now I have tried 

sudo dpkg --configure -a

a couple of times but it keeps failing to install. I will have to try to install all versions of flash from the terminal and start again I guess?

---

### Post by coc_21 on 2010-05-03
Thanks zvacet. it worked

---

### Post by Charbax on 2010-05-11
Thanks zvacet, that worked for me too.

Before this happened, I had a problem installing Filezilla (didn't work, didn't open) and before that I tried to install p2p streaming programs Veetle and Sopcast. I don't know if trying to do any of that triggered this error. (one of those online guides, I think sopcast, had me change the sources for software upgrades somewhere in the terminal)

---

### Post by pepper2u on 2010-05-18
Thank you zvacet.  This worked perfectly on a failed installation of Amarok.

---

### Post by KermEd on 2010-05-31
Zvacet;

Thank you.  Resolved the issue for me.  I had my work give me an old laptop that tends to die randomly because of a battery problem.  Go-figure it happened mid-install.  Thanks!

---

### Post by iEnthusiast on 2010-06-09
Thank you zvacet. That cleared up a problem with an incomplete package install.

---

### Post by wenfuli on 2010-06-16
zvacet: Worked for me too, I think. At least I can install software now. However, when I ran the commands in terminal, I was told to run "apt-get autoremove" to remove the installed programs that were no longer needed. When I did, I got a message saying 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)

E:  Unable to lock the administration directory (var/lib/dpkg), Are you root?

Should I be worried about that?

---

### Post by rhomany on 2010-06-21
Exact same problem here as well and it fixed it. Thanks :)

---

### Post by philnice on 2010-07-02
I've been having the same problem since yesterday when i tried to install java6. The proccess seem to freeze and so i stopped it while i knew i souldn't.
Finally the apt get command brought up the update manager, and a partial update which solved it. ;)

---

### Post by tjtaran on 2010-07-10
thanx a ton dear zvacet

---

### Post by capitalfear on 2010-07-11
> **zvacet said:**
> In applications>accessories>terminal type

```
sudo dpkg --configure -a
```and 

```
sudo apt-get -f install
```If you get any errors from these commands,please post them here.Also if you get errors post output of 

```
cat /etc/apt/sources.list
```

you there are a god among men thank you

---

### Post by nemsis on 2010-07-17
Thanks!

---

### Post by Olivrwendl on 2010-07-28
teamha@TeamHA-desktop:~$ sudo dpkg --configure -a
teamha@TeamHA-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package picasa needs to be reinstalled, but I can't find an archive for it.
teamha@TeamHA-desktop:~$ 

When I try to run software center and install a new program I get an error message saying it could not be completed and these are the details - 

E:I wasn't able to locate a file for the picasa package. This might mean you need to manually fix this package. (due to missing arch): 

Any help would be appreciated.
Thanks,
HA

---

### Post by onewho on 2010-07-30
worked for me too! :D

---

### Post by booboo64 on 2010-08-03
Thanks Zvacet, was receiving the same error message using the Software Centre but all works fine now. Ta muchly!

---

### Post by dil1857 on 2010-09-09
hello sir i have a probal in Ubuntu 10.4 lts
ubantu software center

plz halp me

---

### Post by Tobin709 on 2010-09-22
How exactly do I put in the codes?
When I open up the terminal this pops up   jordan@ubuntu:~$   so where do I put the code?

What I did was i put the first code in than hit enter and when I do that, It asks me for my password but as I type it in nothing appears as if im not really typing anything.  Help would be much appreciated.  I am having the same problem as the person posting this topic. Im trying to install Wine so I can run Photoshop.

In all honestly I would like to remove Ubuntu and go back to Windows XP but I can't figure out how so Im just trying to figure out how to work around it.

When I installed Ubuntu I didn't know what it was, If I did I wouldn't have installed.  HELP ASAP.


Thanks.

---

### Post by Tobin709 on 2010-09-26
Can anybody help me with this?

---

### Post by Tobin709 on 2010-10-31
Can somebody please help me I need to get itunes on this asap

---

### Post by tandrew on 2011-05-15
hi,
in an attempt to run wav files on my computer i inserted the following command into terminal "    	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  sudo aptitude install ubuntu-restricted-extras libdvdcss2 libdvdread3 w32codecs gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-pitfdll non-free-codecs

I get an MS agreement page and notice that there is some installation having to do with 'ttf" but the actual installation never seems to be completed.  Now, i get the 'previous installation hasnn't been completed.
while trying to install any other software.  turning off the computer does not solve the problem. I am not, obviously, very knowledgeable about all of this...had ubuntu installed by a family member who now lives elsewhere
so, i am lost.  any help would be appreciated.
thanks

---

### Post by mouchero08 on 2011-06-04
zvacet i thank you.

wentto download some software then had to shoot out
closed the laptop and got stuc with a failed installation

problem fixed following ur instructions

cheers:p

---

### Post by sanket900 on 2011-11-12
> **zvacet said:**
> In applications>accessories>terminal type

```
sudo dpkg --configure -a
```

and 

```
sudo apt-get -f install
```

If you get any errors from these commands,please post them here.Also if you get errors post output of 

```
cat /etc/apt/sources.list
```
@zvacet

thanks dude, it worked for me :)

---

