---
title: "Can no longer boot into Ubuntu!"
date: 2012-07-10
forum: General Help
---

### Post by airspoon on 2012-07-10
Hello, I have a multi-disk system with Win 7 Pro on one disk and Ubuntu on another disk and everything seemed to be working fine... That is until I added several more disks for storage. Now, I no longer get GRUB at all and when selecting the disk with Ubuntu in UEFI (which worked previously), it simply boots Windows. It would seem that my system is booting Windows regardless of which disk I choose through UEFI and GRUB has completely disappeared.

I only use Windows for gaming, so it's killing me that I can no longer boot into Ubuntu. Is there anyway to recover GRUB and more importantly, make my computer boot from my Ubuntu disk? 

Any help would be greatly appreciated. Thanks!

---

### Post by GreatDanton on 2012-07-10
Try this awesome tool:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by airspoon on 2012-07-11
Excellent! I got it back working, so I'm pretty happy. Thanks alot! However, this GRUB is completely different from the previous GRUB that I had and in fact, says Debian. Anyway, thanks for the help, it was much appreciated.

---

### Post by GreatDanton on 2012-07-11
Hmm, it's strange that you get debian grub menu. For me it worked like a charm. Well anyway I am glad you solved your problem.

Now go under thread tools and mark thread as Solved.

Regards.

---

### Post by tumutanzi.com on 2012-07-11
Are you able log in to Windows or other OS on your computer?

---

### Post by tumutanzi.com on 2012-07-11
> **airspoon said:**
> Excellent! I got it back working, so I'm pretty happy. Thanks alot! However, this GRUB is completely different from the previous GRUB that I had and in fact, says Debian. Anyway, thanks for the help, it was much appreciated.

I do not like the upgrade of GRUB! and force me to learn how to config the new version.

---

### Post by airspoon on 2012-07-11
I hadn't tried until you just brought that up, but yes -I just logged into Windows fine. Everything seems to be working fine now, though it looks like it installed Debian's GRUB. Maybe because I have Gnome Shell installed instead of Unity? I have no idea.

---

### Post by YannBuntu on 2012-07-12
Hello
Boot-Repair uses the GRUB which is in your Ubuntu repositories. So if you get a Debian GRUB, that means that you added in Ubuntu a repository containing the Debian GRUB.
To confirm, please boot into your Ubuntu, then open a terminal (Ctrl+Alt+T) and indicate the output of the following commands:
```
sudo dpkg-query -W -f='${Version}' grub-pc grub-common
```
```
cat /etc/apt/sources.list
```
```
ls /etc/apt/sources.list.d
```

---

### Post by airspoon on 2012-07-12
The first command didn't do anything other than change the prompt.
It went from 'airspoon@Zues' to '1.99-21ubuntu3airspoon@Zues'.

The 2nd command gave me the following:
```
 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

The third command gave me:
```
dropbox.list                     google-chrome.list.save
gnome3-team-gnome3-precise.list  killeroid-ppa-precise.list
google-chrome.list               killeroid-ppa-precise.list.save

```

Does this suggest why I have gotten the Debian GRUB? Thanks.

---

### Post by YannBuntu on 2012-07-13
The GRUB version still indicates 'Ubuntu', but I suppose the [Gnome-3 PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") modified some GRUB settings.

(generally-speaking, be careful when using PPAs, especially the ones which replace existing core packages)

---

