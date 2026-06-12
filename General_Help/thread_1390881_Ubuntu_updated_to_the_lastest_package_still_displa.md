---
title: "Ubuntu updated to the lastest package still display 8.04.3"
date: 2010-01-26
forum: General Help
---

### Post by abcuser on 2010-01-26
Hi,
using Ubuntu 8.04 LTS. I have updated the system to the latest packages using: "sudo apt-get update && sudo apt-get -y upgrade" command and all of the packages are updated, the info is:" 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded".

But executing cat /etc/issue I still get 8.04.3, but I should get 8.04.4 is it?
Am I missing some update or is there a little bug in this issue file?
Regards

---

### Post by Brandon Williams on 2010-01-26
[release.ubuntu.com](http://releases.ubuntu.com/) indicates that 8.04.3 is the latest version of hardy.

---

### Post by BryanFRitt on 2010-01-27
According to 
[https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)
It'll be 2010-01-28

but According to
[https://launchpad.net/ubuntu/+milestone/ubuntu-8.04.4](https://launchpad.net/ubuntu/+milestone/ubuntu-8.04.4)
It'll be 2010-01-21

As of this posting my KUbuntu 8.04 still says KUbuntu 8.04.3 even though I tried updating it a few minutes ago. 

My guess is to give it two days, or so, and see if either the version number changes, or the prediction dates changed.

Some of the ways to tell what version number you have:
[FONT="Courier New"]
cat /etc/*release
cat /etc/lsb-release
cat /etc/issue
lsb_release -rd[/FONT]

p.s. latest is spelled latest.

---

### Post by BryanFRitt on 2010-01-27
Similar thread, but about 8.04.3 instead of 8.04.4
[http://ubuntuforums.org/showthread.php?t=1148695](http://ubuntuforums.org/showthread.php?t=1148695)

---

### Post by snowpine on 2010-01-27
There is no meaningful difference between an updated 8.04.3 system and a fresh install of 8.04.4. 

Try:

```
sudo apt-get dist-upgrade
```

if you want the latest kernel and libraries.

---

### Post by BryanFRitt on 2010-01-28
> **snowpine said:**
> There is no meaningful difference between an updated 8.04.3 system and a fresh install of 8.04.4. 

Try:

```
sudo apt-get dist-upgrade
```

if you want the latest kernel and libraries.

Wouldn't that upgrade to 9.10 instead of 8.04.4?

---

### Post by snowpine on 2010-01-28
> **BryanFRitt said:**
> Wouldn't that upgrade to 9.10 instead of 8.04.4?

No. There is no way to upgrade directly from 8.04 to 9.10. (I would recommend a fresh install if that is your goal, otherwise you have to go 8.04, 8.10, 9.04, 9.10.)

But my understanding is you want to stay with 8.04, is that correct?

---

### Post by BryanFRitt on 2010-01-29
> Preparing to replace base-files 4.0.1ubuntu5.8.04.7 (using .../base-files_4.0.1ubuntu5.8.04.8_amd64.deb) ...
Unpacking replacement base-files ...
Setting up base-files (4.0.1ubuntu5.8.04.8) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...

dpkg run finished!
I did one update today, and now KUbuntu says 8.04.4!

*cat /etc/lsb-release*

[FONT="Courier New"]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"[/FONT]

---

### Post by BryanFRitt on 2010-01-29
After the above upgrade, I did a
*sudo apt-get dist-upgrade*
[FONT="Courier New"][sudo] password for :
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

Guess that command is not a version upgrade after all.

---

### Post by BryanFRitt on 2010-01-31
despite the fact that [FONT="Courier New"]lsb_release -a[/FONT], etc... shows my system as 8.04.**4**, the boot menu still shows my system as 8.04.**3**. 

I can edit as root the file [FONT="Courier New"]/boot/grub/menu.lst[/FONT] so that it says 8.04.**4**. I can trust this is 8.04.**4**, right?

> [FONT="Courier New"]lsb_realese -a[/FONT]

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:        8.04
Codename:       hardy

---

### Post by BryanFRitt on 2010-01-31
> **snowpine said:**
> No. There is no way to upgrade directly from 8.04 to 9.10.

I upgraded from _K_Ubuntu 8.04 directly to _K_Ubuntu 9.10. 
(Although, I reverted back to my backup image I made before the upgrade, since I didn't feel like messing with a new OS at the time.)
(I guess that's not the same as Ubuntu 8.04 to Ubuntu 9.10 though.)
p.s.
You'd loose the KDE 3 settings, unless you back up your [FONT="Courier New"]~/.kde[/FONT] directory to [FONT="Courier New"]~/.kde3[/FONT]
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04)
[http://apt.pearsoncomputing.net/](http://apt.pearsoncomputing.net/)
[https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic](https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic)

---

### Post by Slim Odds on 2010-01-31
> **BryanFRitt said:**
> You can, I did. (however, I reverted back to the image I made before the upgrade, didn't feel like messing with a new os at the time.)

Ubuntu does not support upgrading from directly 8.04 to 9.10. There will be the ability to upgrade from 8.04 to 10.04 since both are LTS.

---

### Post by BryanFRitt on 2010-01-31
> **Slim Odds said:**
> Ubuntu does not support upgrading from directly 8.04 to 9.10. There will be the ability to upgrade from 8.04 to 10.04 since both are LTS.

Ok, I decided to get rid of the words 'you can' from my post, and maybe adjust it some.

Ubuntu may not be able to go directly from 8.04 -> 9.10, but [KUbuntu can go that way]("https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04"). But is it supported? I don't know. What counts as support anyway? I don't know. Although, I think answering that question might get too far off topic.

p.s.
I guess going Ubuntu 8.04 -> KUbuntu 8.04 -> KUbuntu 9.10 -> Ubuntu 9.10 doesn't count as a direct Ubuntu 8.04 to Ubuntu 9.10 upgrade. (not that I've tried that, or even looked it up)

---

### Post by snowpine on 2010-02-01
Cool, thanks for the link Brian... I did not know you could do that (and stand corrected)! :)

---

