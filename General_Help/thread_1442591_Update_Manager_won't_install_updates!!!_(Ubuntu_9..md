---
title: "Update Manager won't install updates!!! (Ubuntu 9.10)"
date: 2010-03-30
forum: General Help
---

### Post by trixa_13 on 2010-03-30
After I checked for updates, I clicked, "Install Updates". But then, an error message popped up! It says,

[COLOR=Red]W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_cairo-dock-team_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)[/COLOR]

What should I do???

---

### Post by plucky on 2010-03-30
> **trixa_13 said:**
> After I checked for updates, I clicked, "Install Updates". But then, an error message pooped up! It says,

[COLOR=Red]W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages (/var/lib/apt/lists/ppa.launchpad.net_cairo-dock-team_ppa_ubuntu_dists_karmic_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)
W: Duplicate sources.list entry [http://repository.glx-dock.org](http://repository.glx-dock.org) karmic/cairo-dock Packages (/var/lib/apt/lists/repository.glx-dock.org_ubuntu_dists_karmic_cairo-dock_binary-i386_Packages)[/COLOR]

What should I do???

Remove the duplicate repository sources using **System > Applications > Software Sources**.

---

### Post by trixa_13 on 2010-03-30
> **plucky said:**
> Remove the duplicate repository sources using **System > Applications > Software Sources**.


But when I checked them, there are no duplicates.

---

### Post by plucky on 2010-03-30
> **trixa_13 said:**
> But when I checked them, there are no duplicates.
From a terminal ```
ls -l /etc/apt/sources.list.d/
```

---

### Post by 3rdalbum on 2010-03-30
They're not error messages, they are "warnings" (they begin with "W", so they're warnings). You can most likely still use those sources.

I'd just advise you to check what is in the /etc/apt/sources.list.d directory, because that's where you're likely to find both copies, or the duplicates of entries that are in /etc/apt/sources.list.

---

### Post by trixa_13 on 2010-03-30
> **plucky said:**
> From a terminal ```
ls -l /etc/apt/sources.list.d/
```

After I input that, what should I do? I'm really sorry if I'm asking too many questions. It's just that I'm really new to Ubuntu or Linux so I don't know much my way around. Please bear with me. Thanks for the help until now. ;)

---

### Post by 3rdalbum on 2010-03-30
> **trixa_13 said:**
> After I input that, what should I do? I'm really sorry if I'm asking too many questions. It's just that I'm really new to Ubuntu or Linux so I don't know much my way around. Please bear with me. Thanks for the help until now. ;)

That command tells you what repositories have files in that folder. I think the suggestion was given so that you'd post back the result of the command to us, and we can see whether you've got duplicate files in there.

If you can see the duplicates, then by all means go into that folder and delete them.

---

### Post by trixa_13 on 2010-03-31
> **3rdalbum said:**
> That command tells you what repositories have files in that folder. I think the suggestion was given so that you'd post back the result of the command to us, and we can see whether you've got duplicate files in there.

If you can see the duplicates, then by all means go into that folder and delete them.


I'm very sorry I didn't realize it. Here it is (the results):

[COLOR=Red]total 44
-rw-r--r-- 1 root root  0 2010-03-30 11:56 cdemu-ppa-karmic.list
-rw-r--r-- 1 root root 60 2010-03-30 11:56 cdemu-ppa-karmic.list.save
-rw-r--r-- 1 root root 63 2010-03-30 11:56 docky-core-ppa-karmic.list
-rw-r--r-- 1 root root 63 2010-03-30 11:56 docky-core-ppa-karmic.list.save
-rw-r--r-- 1 root root 75 2010-03-30 11:56 mozillateam-firefox-stable-karmic.list
-rw-r--r-- 1 root root 75 2010-03-30 11:56 mozillateam-firefox-stable-karmic.list.save
-rw-r--r-- 1 root root 44 2010-03-30 11:56 playonlinux.list
-rw-r--r-- 1 root root 44 2010-03-30 11:56 playonlinux.list.save
-rw-r--r-- 1 root root 64 2010-03-30 11:56 trixa-daily-ppa-karmic.list
-rw-r--r-- 1 root root 64 2010-03-30 11:56 trixa-daily-ppa-karmic.list.save
-rw-r--r-- 1 root root 73 2010-03-30 11:56 ubuntu-mozilla-daily-ppa-karmic.list
-rw-r--r-- 1 root root 73 2010-03-30 11:56 ubuntu-mozilla-daily-ppa-karmic.list.save[/COLOR]

---

### Post by plucky on 2010-03-31
Now post your sources.list.

From a terminal ```
cat /etc/apt/sources.list
```

 Cut and paste into the forums with [noparse]```

```[/noparse] brackets at the beginning and end as this makes it easier to read.

Or go into **Software Sources** and select the **Other Software** tag and un-tick all the boxes.Then **Close** and select **Reload** to reload the sources.list and see if you still have the same problem.

If the problem goes away,then you can add them back in one at a time,each time reloading to see if the error comes back.If it does,delete the line from the Software Sources Page.


Good Luck

---

### Post by trixa_13 on 2010-03-31
> **plucky said:**
> Now post your sources.list.

From a terminal ```
cat /etc/apt/sources.list
``` Cut and paste into the forums with [noparse]```

```[/noparse] brackets at the beginning and end as this makes it easier to read.

Or go into **Software Sources** and select the **Other Software** tag and un-tick all the boxes.Then **Close** and select **Reload** to reload the sources.list and see if you still have the same problem.

If the problem goes away,then you can add them back in one at a time,each time reloading to see if the error comes back.If it does,delete the line from the Software Sources Page.


Good Luck

I did what you told me to. I un-ticked all of them and reloaded and ticked them one at a time. But when I ticked this certain source, an error appeared:

```

Failed to fetch http://ppa.launchpad.net/trixa-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```And, this is my sources.lists

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ph.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu/ karmic universe
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://ph.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu karmic main ## Cairo-Dock-PPA-Weekly
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu karmic main ## Cairo-Dock-PPA-Stable
deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu karmic main ## Cairo-Dock-PPA-Stable
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable
deb http://ph.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe #Added by software-properties
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable
deb http://packages.medibuntu.org/ karmic free non-free
deb http://repository.glx-dock.org/ubuntu karmic cairo-dock ## Cairo-Dock-Stable

```Thanks! :p

---

### Post by plucky on 2010-04-01
As far as I can see,there is no trixa-daily ppa on launchpad.net.That is why you are getting the 404 not found error.

Are there any other problems?

---

### Post by trixa_13 on 2010-04-01
> **plucky said:**
> As far as I can see,there is no trixa-daily ppa on launchpad.net.That is why you are getting the 404 not found error.

Are there any other problems?


No, there are no remaining problems. So, I have to remove that in my Software Sources, right? Really, thanks for the help! :KS

---

