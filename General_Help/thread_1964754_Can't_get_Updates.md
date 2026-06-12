---
title: "Can't get Updates"
date: 2012-04-24
forum: General Help
---

### Post by reylas81 on 2012-04-24
Ok I have tried to get updates but no keep getting a message to check my connection. Under details I get:

[LIST]
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]E:Some index files failed to download. They have been ignored, or old ones used instead.
[/LIST]
I have tried the "sudo apt-cdrom" and various variations of that command but to no avail. I have tried "sudo apt-get update" no effect. I have also tried to upgrade. nada. doesn't matter if I am using the terminal or gui it will not update.

---

### Post by ptn107 on 2012-04-24
Run the following and post your results:
```
cat /etc/apt/sources.list
```

---

### Post by jonobr on 2012-04-24
Hello

I think the problem is that CD rom is defined in your sources.list

you need to go into the source.list file (if your ok using gedit, nano or vi and comment out the instances of cd rom so the updates occur on the network not on the cd rom
.(make a backup of sources.list first!!)

Once done
```
sudo apt-get update && sudo apt-get upgrade
```

You should be able to do it in the repos of synaptic.

---

### Post by techsupport on 2012-04-24
> **reylas81 said:**
> Ok I have tried to get updates but no keep getting a message to check my connection. Under details I get:

[LIST]
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[*]E:Some index files failed to download. They have been ignored, or old ones used instead.
[/LIST]
I have tried the "sudo apt-cdrom" and various variations of that command but to no avail. I have tried "sudo apt-get update" no effect. I have also tried to upgrade. nada. doesn't matter if I am using the terminal or gui it will not update.

Why is it updating from your CD ROM still? Remove the disc from the drive and reboot your system.   Open synaptic package manager (or open software center, click edit, and click software sources) and uncheckbox the CD ROM it is trying to read from.  Close out and update everything again. Don't leave the install disc in your drive after you are done installing Ubuntu.

:guitar:

---

### Post by jonobr on 2012-04-24
I think we are all ninjaing each other here ):P:p

---

### Post by reylas81 on 2012-04-24
ok here is what I got for the source list:

randall@randall-N80Vb:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by techsupport on 2012-04-24
> **jonobr said:**
> I think we are all ninjaing each other here ):P:p

Software Center >>> Edit >>>  Software Sources 

Uncheckbox the CD ROM.  

Close out. 

Update your system.

high five.. yes!

---

### Post by jonobr on 2012-04-24
> deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

This is the line cuasing your issue

Follow techcupport's advice and uncheck via the gui
or use cli to modify the file directly.

I recommend you use the gui.

I think we are done here!

---

### Post by h3ooo on 2012-06-23
Thanks for the replies in this thread as you have just helped me too!

---

