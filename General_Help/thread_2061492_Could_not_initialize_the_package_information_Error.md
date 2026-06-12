---
title: "Could not initialize the package information Error"
date: 2012-09-22
forum: General Help
---

### Post by Bryanjpg on 2012-09-22
I am pretty new to Ubuntu. I just recently started receiving this error message and it is now not letting do any updates.


```
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
```

---

### Post by Bashing-om on 2012-09-22
Bryanjpg; Hi ! Welcome to the forum.

 Let us look at what might be the root cause... what is in your sources list ?
Please post the output of:
```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/

```Do you recall why the tualatrix ppa was enabled ?

The tualatrix ppa only is for natty and earlier. [https://launchpad.net/~team-xbmc/+archive/ppa]("https://launchpad.net/%7Eteam-xbmc/+archive/ppa")
[http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/)

[INDENT]warm regards <==BDQ

[/INDENT]

---

### Post by jerrrys on 2012-09-22
You can try this

[http://ubuntuforums.org/showthread.php?t=1946302](http://ubuntuforums.org/showthread.php?t=1946302)

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

And welcome to the forums :)

---

### Post by Bryanjpg on 2012-09-27
I am happy to be part of the community thanks!

Ok I put that into the terminal this was what it brought up

> bryan@bryan-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository
bryan@bryan-desktop:~$ cat /etc/apt/sources.list.d/
cat: /etc/apt/sources.list.d/: Is a directory
bryan@bryan-desktop:~$ 


---

### Post by Bryanjpg on 2012-09-27
I do not know why I have Tualatrix ppa. I'm honestly not sure what it is. When I first got Ubuntu I started with 10.04 or something around that, because I had to use torrent to download it with my slow internet connection. This was only about 6 months ago. When I did that there was no driver for my Wifi card, so I had to bring my computer to the internet and research it. I ended up having to download some third party driver to make it work. I'm guessing that might be when the Tualatrix came into play, but like I said I don't know what tualatrix does.

---

### Post by Bryanjpg on 2012-09-27
JERRRYS That worked! Thank you!!

I wish I knew what it did, but I'm just glad it worked.

---

### Post by jerrrys on 2012-09-27
sudo rm /var/lib/apt/lists/*

sudo give you administrator (root) access  

rm stands for remove and you removed everything in apt/list by putting an * at the end

apt-get update rebuilt that list

apt-get commands are very useful, check them out

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

and lastly

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bashing-om on 2012-09-27
Glad ya got it resolved. Looking good !

The removed files -some corruption from unknown source -These files guide-config the package manager (apt) ..new ones brought in . It is amazing how smart the package manager is.

Please mark this thread as solved, aids others in seeking solutions.

[INDENT]Happy ubuntu'n <==BDQ

[/INDENT]

---

### Post by Rytron on 2012-10-14
This fix worked but doesnt that mean that a whole load of updates need to be re-downloaded?
```

sudo rm /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by wildmanne39 on 2012-10-14
Hi, no you do not need to download a lot of new updates.
Thanks

---

### Post by Rytron on 2012-10-14
> **Wild Man said:**
> Hi, no you do not need to download a lot of new updates.
Thanks

Hey Wild Man. Thanks for clarifying that. ):P

---

### Post by wildmanne39 on 2012-10-14
Your welcome!

---

