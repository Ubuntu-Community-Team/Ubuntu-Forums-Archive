---
title: "error with update and apt-get"
date: 2011-05-04
forum: General Help
---

### Post by U235master on 2011-05-04
i did something with the update settings (i don't remember what, i was tired at the time) and now i cant get either apt-get or the update manager to work. for the update manager, i open it and it tries to read the package lists then spits out this error
```

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'
```

also any apt-get operation spits this out:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

can anyone help me? i just upgraded to natty awhile ago, and any help is appreciated.

---

### Post by andrewthomas on 2011-05-04
comment out the partner repo in your /etc/apt/sources.list file and try to update again

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by U235master on 2011-05-04
its still giving me the above error.
if it helps, here is the contents of my sources.list:
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse
# deb http://archive.canonical.com/ lucid partner
# deb-src http://archive.canonical.com/ lucid partner
```

thanks for helping! :)

---

### Post by collisionystm on 2011-05-04
> **U235master said:**
> i did something with the update settings (i don't remember what, i was tired at the time) and now i cant get either apt-get or the update manager to work. for the update manager, i open it and it tries to read the package lists then spits out this error
```

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'
```also any apt-get operation spits this out:
```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```can anyone help me? i just upgraded to natty awhile ago, and any help is appreciated.

```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en

sudo apt-get update
```

Here are the contents of my Natty /var/lib/apt/lists/

> charles@MAWS5240:/var/lib/apt/lists$ ls
extras.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources
extras.ubuntu.com_ubuntu_dists_natty_Release
extras.ubuntu.com_ubuntu_dists_natty_Release.gpg
lock
partial
ppa.launchpad.net_lorenzo-carbonell_atareao_ubuntu_dists_natty_main_binary-amd64_Packages
ppa.launchpad.net_lorenzo-carbonell_atareao_ubuntu_dists_natty_main_source_Sources
ppa.launchpad.net_lorenzo-carbonell_atareao_ubuntu_dists_natty_Release
ppa.launchpad.net_nagiosinc_ppa_ubuntu_dists_natty_main_binary-amd64_Packages
ppa.launchpad.net_nagiosinc_ppa_ubuntu_dists_natty_main_source_Sources
ppa.launchpad.net_nagiosinc_ppa_ubuntu_dists_natty_Release
ppa.launchpad.net_nagiosinc_ppa_ubuntu_dists_natty_Release.gpg
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_natty_main_binary-amd64_Packages
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_natty_main_source_Sources
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_natty_Release
ppa.launchpad.net_nilarimogard_webupd8_ubuntu_dists_natty_Release.gpg
ppa.launchpad.net_rye_ubuntuone-extras_ubuntu_dists_natty_main_binary-amd64_Packages
ppa.launchpad.net_rye_ubuntuone-extras_ubuntu_dists_natty_main_source_Sources
ppa.launchpad.net_rye_ubuntuone-extras_ubuntu_dists_natty_Release
ppa.launchpad.net_rye_ubuntuone-extras_ubuntu_dists_natty_Release.gpg
ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_natty_main_binary-amd64_Packages
ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_natty_Release
ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_natty_Release.gpg
security.ubuntu.com_ubuntu_dists_natty-security_main_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_Release
security.ubuntu.com_ubuntu_dists_natty-security_Release.gpg
security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_natty-security_universe_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_Release
us.archive.ubuntu.com_ubuntu_dists_natty_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release
us.archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages
us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources
charles@MAWS5240:/var/lib/apt/lists$ 

I believe you will be just fine after you delete that bad file with the rm command

---

### Post by U235master on 2011-05-04
```
rm: cannot remove `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en': No such file or directory
```

i checked in /var/lib/apt/lists/ and there wasn't any file that was  similar to the one that it was supposed to delete

---

### Post by plucky on 2011-05-04
> **U235master said:**
> ```
rm: cannot remove `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en': No such file or directory
```

i checked in /var/lib/apt/lists/ and there wasn't any file that was  similar to the one that it was supposed to delete

Just try removing all the list files with ```
sudo rm /var/lib/apt/lists/*
```

It will complain about being unable to remove a "partial" directory,but just ignore it.

Then run ```
sudo apt-get update
``` to reload the list files.

Good luck

---

### Post by U235master on 2011-05-04
that worked, thanks very much!

---

### Post by kalaharigreen on 2011-05-11
> **plucky said:**
> Just try removing all the list files with ```
sudo rm /var/lib/apt/lists/*
```

It will complain about being unable to remove a "partial" directory,but just ignore it.

Then run ```
sudo apt-get update
``` to reload the list files.

Good luck

Thanks, a variation of this helped me. I did the rm command and then apt-get, but the terminal got stuck on the same file. I did rm again and found that it unblocked the update manager, so fingers crossed I am trying again with the update manager now.

---

### Post by ChaosChris2009 on 2011-05-12
> **plucky said:**
> Just try removing all the list files with ```
sudo rm /var/lib/apt/lists/*
```

It will complain about being unable to remove a "partial" directory,but just ignore it.

Then run ```
sudo apt-get update
``` to reload the list files.

Good luck

This worked for me as well.

Thank you, you are a lifesaver!

---

### Post by athena3rm on 2011-05-20
> **ChaosChris2009 said:**
> This worked for me as well.

Thank you, you are a lifesaver!

Hello! i tried and he replied

 rm: impossible to remove "/var/lib/apt/lists/partial": is a directory
 Any suggestion?

thanks a lot!

---

### Post by matt_symes on 2011-05-20
Hi

> **athena3rm said:**
> Hello! i tried and he replied

 rm: impossible to remove "/var/lib/apt/lists/partial": is a directory
 Any suggestion?

thanks a lot!

That should not be a problem. Just type.

```
sudo apt-get update
```

and it should work. If it does not post back.

Kind regards

---

### Post by jramshu on 2011-05-20
> **athena3rm said:**
> Hello! i tried and he replied

 rm: impossible to remove "/var/lib/apt/lists/partial": is a directory
 Any suggestion?

thanks a lot!

This will stop complaints: -v(tells what it's removing) -f (forces it)

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

There are a couple other threads about hiccups in the updates.

---

### Post by athena3rm on 2011-05-28
Problem solved, thanks a lot!

---

### Post by mananshah105 on 2012-09-15
Try 
sudo rm -R /var/lib/apt/lists/*

it will recursively delete all the sub folders of the lists directory...it will work.. :)

---

