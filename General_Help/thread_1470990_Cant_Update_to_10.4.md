---
title: "Cant Update to 10.4??"
date: 2010-05-03
forum: General Help
---

### Post by joek71 on 2010-05-03
Hi guys

I am trying to update to 10.4 and i am getting this message:

Could not calculate the upgrade

An unresilvable problem occurred while calculating the upgrade:

This can be caused by:
*Upgrading to a pre-release
*Running the current pre-release version of Ubuntu
*Unofficial software package not provided by Ubuntu

If none of this applies, then please report this bug agains the 'update-manager' package and include the files in /var/log/distupgrade/ in the bug report.

Can anyone please help me out.

thank you

---

### Post by philinux on 2010-05-03
> **joek71 said:**
> Hi guys

I am trying to update to 10.4 and i am getting this message:

Could not calculate the upgrade

An unresilvable problem occurred while calculating the upgrade:

This can be caused by:
*Upgrading to a pre-release
*Running the current pre-release version of Ubuntu
*Unofficial software package not provided by Ubuntu

If none of this applies, then please report this bug agains the 'update-manager' package and include the files in /var/log/distupgrade/ in the bug report.

Can anyone please help me out.

thank you

```
cat /etc/apt/sources.list
```
Post back the contents.

---

### Post by joek71 on 2010-05-03
mng@mng-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main # disabled on upgrade to lucid
# deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable disabled on upgrade to lucid
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games # disabled on upgrade to lucid
mng@mng-desktop:~$ ^C
mng@mng-desktop:~$ ^C
mng@mng-desktop:~$ clear

mng@mng-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
# deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main # disabled on upgrade to lucid
# deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable disabled on upgrade to lucid
# deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games # disabled on upgrade to lucid
mng@mng-desktop:~$

---

### Post by dino99 on 2010-05-03
only "lucid" lines are needed, remove the others

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
There are always so many problems with dist-upgrades I just tell people to put /home on its own partition (or back it up along with /etc and /var [if applicable] in a 7z) and do a fresh install of just the system every time. My setup is sda = 1: Windows 7 2: Reserve 3: /home 4: ext4 backup  sdb = 1: ntfs backup 2: ubuntu 10.04 hdc = 40GB ntfs for xfers

That way I can reinstall or whatever without affecting my user files.

---

### Post by joek71 on 2010-05-03
I am new to ubuntu and the great Linux world, how would I remove those lines?

Thank you

---

### Post by sarin_cv on 2010-05-03
> 
There are always so many problems with dist-upgrades I just tell people  to put /home on its own partition (or back it up along with /etc and  /var [if applicable] in a 7z) and do a fresh install of just the system  every time. My setup is sda = 1: Windows 7 2: Reserve 3: /home 4: ext4  backup  sdb = 1: ntfs backup 2: ubuntu 10.04 hdc = 40GB ntfs for xfers

That way I can reinstall or whatever without affecting my user files.

But in that case when you install applcations, it will overwrite the existing folders... right?

---

### Post by sarin_cv on 2010-05-03
> **joek71 said:**
> I am new to ubuntu and the great Linux world, how would I remove those lines?

Thank you

Goto System-> Software sources -> third party applications -> uncheck all the unwanted entries


or you can directly edit the file by running

[FONT=Verdana]sudo gedit /etc/apt/sources.list [/FONT]

---

### Post by joek71 on 2010-05-03
I removed those lines like you said and still same problem.

Thanks

---

### Post by philinux on 2010-05-03
> **sarin_cv said:**
> Goto System-> Software sources -> third party applications -> uncheck all the unwanted entries


or you can directly edit the file by running

[FONT=Verdana]sudo gedit /etc/apt/sources.list [/FONT]

Should be.

```
gksudo gedit /etc/apt/sources.list
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by joek71 on 2010-05-03
This is the file I got, everything has the ## sign next to it.

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic ##main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted ##universe multiverse
## deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main ##restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
##deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
##deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
@ sarin_cv : Yeah but the configuration for the softwares are in /home so you won't lose settings. I think most of what people need is there. I found that I need /etc and /var as well. Some may need /usr... I'm pretty sure it's the installed software causes the problems with upgrades.

@joek71 : Only comment out (put ## next to) the ones that say Karmic. You need the ones that say Lucid.

---

### Post by joek71 on 2010-05-03
I did uncomment only what you said and I still getting the same problem.

Is there a log I can upload her to show you what is going on.

Thank you,
Joe

---

### Post by joek71 on 2010-05-03
Maybe I should do a fresh install? Nothing is helping.

---

### Post by Sin@Sin-Sacrifice on 2010-05-03
In a command line type ```
sudo apt-get dist-upgrade
``` and copy/paste the output here. I have to go but I'm sure someone can help you from there.

Edit: Like I said before... a fresh install is your best bet. If you need your settings just back up your /home and /etc directories and replace them when done installing 10.04. That will bring everything back. I would leave out /etc/apt when replacing /etc though because that is more than likely the cause of the problems. You do NOT need any repos for karmic in lucid.

---

### Post by joek71 on 2010-05-03
Thank you, for all your help.  Worst case I will do reinstall.

Thank you,
Joe

---

