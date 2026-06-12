---
title: "Problems with Software Center and Synaptic"
date: 2011-03-23
forum: General Help
---

### Post by gardy0701 on 2011-03-23
I am new at this and I am having problems with the software center and synaptic package manager

here are the errors I am getting:
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.

Any help would be much appreciated.

---

### Post by Sef on 2011-03-23
Applications > Accessories > Terminal

Then copy and paste this command below:

```
sudo apt-get install abiword
```

Then copy and paste any errors that you get.

Note: [Abiword]("http://abiword.org/") is a word processor.

---

### Post by gardy0701 on 2011-03-23
In the terminal I get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by maghoxfr on 2011-03-23
> **gardy0701 said:**
> In the terminal I get this error:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You have to close synaptic and software center and then Open the terminal

---

### Post by gardy0701 on 2011-03-23
> **maghoxfr said:**
> You have to close synaptic and software center and then Open the terminal

Neither of them are open. Mozilla is open, Evolution is open, the Terminal is open and VirtualBox is open.

---

### Post by maghoxfr on 2011-03-23
> **gardy0701 said:**
> Neither of them are open. Mozilla is open, Evolution is open, the Terminal is open and VirtualBox is open.

Maybe try rebooting, and doing what Sef told you straight away, sometimes some daemon keeps running on the background.

---

### Post by matt_symes on 2011-03-23
Hi

I expect rebooting will fix it but if not the lock can be manually removed.

Kind regards

---

### Post by maghoxfr on 2011-03-23
> **matt_symes said:**
> Hi

I expect rebooting will fix it but if not the lock can be manually removed.

Kind regards

Oh, mate, go ahead, I'm just a noob and I was just sharing my solution to this kind of thing according to my experience. But I'd love to know how to manually unlock it also!

---

### Post by gardy0701 on 2011-03-23
> **maghoxfr said:**
> Maybe try rebooting, and doing what Sef told you straight away, sometimes some daemon keeps running on the background.

I tried rebooting earlier today, which is why I posted my problem... I had looked all over for my specific issue and since the reboot did nothing I could see I decided to ask for help. :P

---

### Post by maghoxfr on 2011-03-23
> **gardy0701 said:**
> I tried rebooting earlier today, which is why I posted my problem... I had looked all over for my specific issue and since the reboot did nothing I could see I decided to ask for help. :P

I meant, rebooting and then doing what sef told you:

1) Reboot
2)Applications > Accessories > Terminal

Then copy and paste this command below:

sudo apt-get install abiword

---

### Post by SexySara on 2011-03-23
It sounds to me that the repositories are messed up. I had this happened to me a few times and learned how to fix them when something went wrong. What I usually do is have a copy of all my repositories in a text file then I run this command in terminal...
```
sudo gedit /etc/apt/sources.list
```That will bring up ur repositories. In fact you should copy and past them so we can see what you have, that will help narrow down ur problems. 

If you get key errors while add to your broken repository then run this command to add the keys.
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <key here>
```[Read this too...]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu")

What version of Ubuntu are you running? Run this command to find out, unless you already know.
```
cat /etc/issue
```

---

### Post by gardy0701 on 2011-03-23
> **Sef said:**
> Applications > Accessories > Terminal

Then copy and paste this command below:

```
sudo apt-get install abiword
```Then copy and paste any errors that you get.

Note: [Abiword]("http://abiword.org/") is a word processor.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by gardy0701 on 2011-03-23
> **SexySara said:**
> It sounds to me that the repositories are messed up. I had this happened to me a few times and learned how to fix them when something went wrong. What I usually do is have a copy of all my repositories in a text file then I run this command in terminal...
```
sudo gedit /etc/apt/sources.list
```That will bring up ur repositories. In fact you should copy and past them so we can see what you have, that will help narrow down ur problems. 

If you get key errors while add to your broken repository then run this command to add the keys.
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <key here>
```[Read this too...]("https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu")

What version of Ubuntu are you running? Run this command to find out, unless you already know.
```
cat /etc/issue
```

I am running Ubuntu 10.10 but I ran that last bit in Terminal just to see what it says and it has a little after 10.10 so here you go! Ubuntu 10.10 \n \l

This is the source list produced by the first line of code...

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

---

### Post by SexySara on 2011-03-23
> **gardy0701 said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Run this...

```
sudo dpkg --configure -a
```There is a package that is not fully installed and causing errors.

---

### Post by gardy0701 on 2011-03-23
> **SexySara said:**
> Run this...

```
sudo dpkg --configure -a
```There is a package that is not fully installed and causing errors.

That seems to have worked, now I feel stupid... I tried that earlier today and nothing happened and I was still getting errors... Must have been the reboot!

---

### Post by gardy0701 on 2011-03-23
Thanks for all of the help here everyone.:o

---

### Post by Krytarik on 2011-03-23
> **gardy0701 said:**
> ```

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) [COLOR=Red]**hardy**[/COLOR] main

deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) [COLOR=Red]**jaunty**[/COLOR] main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) [COLOR=Red]**jaunty**[/COLOR] main
```
Although you are already happy, I would take care of those.

Greetings.

---

### Post by maghoxfr on 2011-03-23
> **Krytarik said:**
> Although you are already happy, I would take care of those.

Greetings.

Nice avatar, Iron Tux?

---

### Post by Krytarik on 2011-03-23
> **maghoxfr said:**
> Nice avatar, Iron Tux?
Exactly! :D

---

### Post by gardy0701 on 2011-03-23
> **Krytarik said:**
> Although you are already happy, I would take care of those.

Greetings.

What exactly do you mean take care of those? Get into the list again and delete them?

---

### Post by maghoxfr on 2011-03-23
> **gardy0701 said:**
> What exactly do you mean take care of those? Get into the list again and delete them?

Look the right ones for your distro and replace them.

---

### Post by gardy0701 on 2011-03-23
> **maghoxfr said:**
> Look the right ones for your distro and replace them.

I had been looking at a way to install something yesterday or the day before and I was supposed to use those I think. But I moved on from that and I didn't complete the install, those are probably what caused all of this. I deleted them and I am working fine. Thanks again everyone.

:rolleyes:

---

### Post by maghoxfr on 2011-03-23
> **gardy0701 said:**
> I had been looking at a way to install something yesterday or the day before and I was supposed to use those I think. But I moved on from that and I didn't complete the install, those are probably what caused all of this. I deleted them and I am working fine. Thanks again everyone.

:rolleyes:

But if you want to have Copiz updated and bisigi, you'll have to get the right PPA's, the ones for Ubuntu 10.10 that is.

---

### Post by gardy0701 on 2011-03-23
> **maghoxfr said:**
> But if you want to have Copiz updated and bisigi, you'll have to get the right PPA's, the ones for Ubuntu 10.10 that is.

OK, I will look into it.

---

### Post by maghoxfr on 2011-03-23
cheers

---

### Post by v6rg on 2011-04-24
> **SexySara said:**
> Run this...

```
sudo dpkg --configure -a
```There is a package that is not fully installed and causing errors.


Hey! I have sameproblem. Please help me.


#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by maghoxfr on 2011-04-24
> **v6rg said:**
> Hey! I have sameproblem. Please help me.


#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

You have to check your current distro version and check for the repositories to be coherent. So if you're running 10.10, check that all your repositories are intended for 10.10. Then, delete the ones that are wrong and look for them on the correct version.

---

### Post by v6rg on 2011-04-24
I solved my problem by this topic notes:

[http://ubuntuforums.org/showthread.php?t=1649534](http://ubuntuforums.org/showthread.php?t=1649534)

> 
go to System > Administration > Synaptic. Search for  ttf-mscorefonts-installer. Is the box green? If not, mark it for  installation and click on 'Apply'. If the box is green, right-click on  it and select 'Reinstallation' and then 'Apply'. See if that helps.

---

### Post by abbasdjinn on 2011-04-24
when i tried to update ubuntu using update manager i got the following message.
"The package indexes are currently changed by apt-get."
since i am a novice..please help..:(

---

