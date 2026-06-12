---
title: "help managing packages!"
date: 2009-10-04
forum: General Help
---

### Post by blackmamba123 on 2009-10-04
what do i do with a package (in this case ubuntu tweak) that is "in an inconsistant state" that needs to be reinstalled (but no archive is found for it). or how do i remove the package?

---

### Post by fluffman86 on 2009-10-04
Go to System > Administration > Synaptic, then search for the package there, right-click, and reinstall.  If that doesn't work, then select completely remove, then you can reinstall afterward if you want.  That will remove all of your settings for the program, though.

---

### Post by blackmamba123 on 2009-10-04
it wont let me do anything in synaptic, it gives me an error about tweak then closes

---

### Post by tuxxy on 2009-10-04
Have you tried fixing broken packages using Synaptic.

---

### Post by blackmamba123 on 2009-10-04
nope, synaptic is unusable to me right now, it wont let me access anything in it until i fix the problem w/ tweak. this is what it tells me exactly: 

The package 'ubuntu-tweak' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system

how do i remove it without going into synaptic(because i cant) or reinstall it manually?

---

### Post by blackmamba123 on 2009-10-05
bump

---

### Post by earthpigg on 2009-10-05
well, ubuntu-tweak seems to be the problem. let's go ahead and remove it.

```
sudo apt-get remove --purge ubuntu-tweak
```

see if things work then.

if that fixes everything, then try re-installing ubuntu-tweak and see if things break again.

if they do break, then i suppose we know what software is causing problems...

---

### Post by blackmamba123 on 2009-10-05
i tried doing that and this is what i got:

the package ubuntu tweak needs to be reinstalled, but i cant find an archive for it.

i dont think that uninstalled it, any other ideas?

---

### Post by slakkie on 2009-10-05
dpkg -r ubuntu-tweak

You could add a flag --force-all to make sure it is really removed.

---

### Post by blackmamba123 on 2009-10-05
i dont know how to add a flag, but when i did the dpkg thing it said:

the package is in a very bad inconsistent state, you should reinstall it before attempting a removal.

so i went to [https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9) to reinstall and it gave me this error when it installed:

the package may be corrupted or you may not be able to open the file.check the permissions for the file

---

### Post by slakkie on 2009-10-05
Ok.. Could you post the output of the following commands for me?

lsb_release -a
apt-cache policy ubuntu-tweak

---

### Post by blackmamba123 on 2009-10-05
apt cache policy:

 Installed: 0.4.9-1~karmic1
  Candidate: 0.4.9-1~karmic1
  Version table:
 *** 0.4.9-1~karmic1 0
        100 /var/lib/dpkg/status


lsb release:

Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty

---

### Post by slakkie on 2009-10-05
> **blackmamba123 said:**
> apt cache policy:

 Installed: 0.4.9-1~karmic1
  Candidate: 0.4.9-1~karmic1
  Version table:
 *** 0.4.9-1~karmic1 0
        100 /var/lib/dpkg/status


lsb release:

Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
mkay...

So you installed a karmic package on Jaunty... I cannot find that package with all repo's of karmic enabled. Could you post your sources.list as well..

cat /etc/apt/sources.list

Ps. if you post apt-cache policy, please include all information shown by the command eg:

```

network-manager:
  Installed: (none)
  Candidate: 0.8~a~git.20090923t064445.b20cef2-0ubuntu2
  Version table:
     0.8~a~git.20090930t162132.866d48b-0ubuntu1~nmt1 0
        500 http://ppa.launchpad.net karmic/main Packages
     0.8~a~git.20090923t064445.b20cef2-0ubuntu2 0
        550 http://nl.archive.ubuntu.com karmic/main Packages

```

Makes it easier for others.

---

### Post by blackmamba123 on 2009-10-05
what i posted is exactly what it gave me for the cache policy, my sources.list is : 

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main

---

### Post by slakkie on 2009-10-05
Okay..

What you could try, and then I'm out of idea's.

First of all, download ubuntu-tweak for jaunty and karmic.

```

wget http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb
wget http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb

```

Then..

```

sudo dpkg -i ubuntu-tweak_0.4.9-1~jaunty1_i386.deb
dpkg: warning: downgrading ubuntu-tweak from 0.4.9-1~karmic1 to 0.4.9-1~jaunty1.
(Reading database ... 192673 files and directories currently installed.)
Preparing to replace ubuntu-tweak 0.4.9-1~karmic1 (using ubuntu-tweak_0.4.9-1~jaunty1_i386.deb) ...
Unpacking replacement ubuntu-tweak ...
Setting up ubuntu-tweak (0.4.9-1~jaunty1) ...

Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...

```

I hope that works. Otherwise try installing the karmic one:

```

sudo dpkg -i ubuntu-tweak_0.4.9-1~karmic1_i386.deb
# And remove it again
sudo dpkg -r --force-all ubuntu-tweak

```

You should file a bug, so this package is distributed via a PPA.

---

### Post by blackmamba123 on 2009-10-05
im still pretty new to ubuntu, so where would i put all of that? do i open my sources.list and add the 

wget [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb)
wget [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb)
to the end of it?

---

### Post by slakkie on 2009-10-06
> **blackmamba123 said:**
> im still pretty new to ubuntu, so where would i put all of that? do i open my sources.list and add the 

wget [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb)
wget [http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb)
to the end of it?

NO NO NO

You open a terminal and then execute those commands:

```

# Open a terminal

# make a temp directory
mkdir -p $HOME/tmp
cd $HOME/tmp

# Get the files
wget http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb
wget http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~karmic1_i386.deb

# Install jaunty version (the correct version):
dpkg -i ubuntu-tweak_0.4.9-1~jaunty1_i386.deb
# If it doesn't work.. 
dpkg -i ubuntu-tweak_0.4.9-1~karmic1_i386.deb
dpkg -r ubuntu-tweak

```

If it fails, please paste the output of the dpkg -i and -r commands between code tags: [ code] [ /code] (without the spaces).

---

### Post by blackmamba123 on 2009-10-06
i downloaded the two files, however it wouldnt let me execute the dkpg -r dkpg -i, it said:

```
bash: -i: command not found
```

---

### Post by earthpigg on 2009-10-06
d***_pk_***g, not pkpg

---

### Post by blackmamba123 on 2009-10-06
ok it said this:

```
dpkg: requested operation requires superuser privilege
```

so i tried it with sudo infront and it gave me this
```
dpkg: error processing ubuntu-tweak_0.4.9-1~jaunty1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ubuntu-tweak_0.4.9-1~jaunty1_i386.deb

```

---

### Post by blackmamba123 on 2009-10-06
bump :)

---

### Post by fluffman86 on 2009-10-06
please copy/paste (with the mouse...ctrl+v doesn't work in terminal)
sudo dpkg -i ubuntu-tweak_0.4.9-1~jaunty1_i386.deb

basically, you have to use sudo before a command whenever it's making system changes or you get a message about requiring the administrator.

---

### Post by blackmamba123 on 2009-10-07
with sudo infront and it gave me this
 
```
dpkg: error processing ubuntu-tweak_0.4.9-1~jaunty1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ubuntu-tweak_0.4.9-1~jaunty1_i386.deb
```

---

### Post by blackmamba123 on 2009-10-07
bump agin

---

### Post by Anarci on 2009-10-07
You can try restarting and entering recovery mode -  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
You will be able to choose from a list of options, try dpkg fix broken packages
[ ]("https://wiki.ubuntu.com/RecoveryMode")

---

