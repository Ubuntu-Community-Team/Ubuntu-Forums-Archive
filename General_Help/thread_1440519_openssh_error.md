---
title: "openssh error"
date: 2010-03-27
forum: General Help
---

### Post by missileboat on 2010-03-27
Hello, I am running 9.10 and am trying to install openssh-server but am running into issues. The first attempt gave me this response:

steven@remote:~$ sudo apt-get install openssh-server
[sudo] password for steven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate

The second attempt got me this result:

steven@remote:~$ sudo apt-get install openssh-server
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
steven@remote:~$ 

I have been trying to google the solution for awhile now but I it seems very few have this issue (or they are not speaking up if they do).

Anyone have any suggestions? Thanks!

---

### Post by wojox on 2010-03-27
```
sudo apt-get install ssh
```

Should do it. You need to close out any other Package managers as well. Synaptic or Ubuntu Software Center.

---

### Post by missileboat on 2010-03-27
Good call on Synaptic, I did have it running that second time. I close it, ran the command line, same result:

steven@remote:~$ sudo apt-get install ssh
[sudo] password for steven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate
steven@remote:~$

---

### Post by whoop on 2010-03-27
what is output:
```

sudo aptitude search ssh

```

---

### Post by missileboat on 2010-03-27
steven@remote:~$ sudo aptitude search ssh
[sudo] password for steven: 
i   openssh-client             - secure shell client, an rlogin/rsh/rcp rep
v   ssh-askpass                -                                           
i   ssh-askpass-gnome          - interactive X program to prompt users for 
v   ssh-client                 -                                           
steven@remote:~$

---

### Post by whoop on 2010-03-27
> **missileboat said:**
> steven@remote:~$ sudo aptitude search ssh
[sudo] password for steven: 
i   openssh-client             - secure shell client, an rlogin/rsh/rcp rep
v   ssh-askpass                -                                           
i   ssh-askpass-gnome          - interactive X program to prompt users for 
v   ssh-client                 -                                           
steven@remote:~$

Post contents of /etc/apt/sources.list, please.
I think you are missing repo's or something...

check if multiverse and universe are enabled (via removing the #), run aptitude update and try again...

---

### Post by missileboat on 2010-03-27
Here is the contents of sources.list:

#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

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

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by whoop on 2010-03-27
OK, strange...
Does: "sudo apt-get update" return anything problematic?

---

### Post by nothingspecial on 2010-03-27
Something is wrong.

In the meantime download it from [[COLOR="Magenta"]here[/COLOR]]("http://packages.ubuntu.com/karmic/openssh-server")

At the bottom of the page.

---

### Post by missileboat on 2010-03-27
I just ran apt-get update and it ran through without any issues. I then tried to install openssh-server again and it worked this time. It seems that apt-get update was all I needed to do (forgive me if that is a nooby mistake as my Linux knowledge is limited at best). Well, whatever the reasoning, thanks for the help!

---

### Post by whoop on 2010-03-27
> **missileboat said:**
> I just ran apt-get update and it ran through without any issues. I then tried to install openssh-server again and it worked this time. It seems that apt-get update was all I needed to do (forgive me if that is a nooby mistake as my Linux knowledge is limited at best). Well, whatever the reasoning, thanks for the help!

No problem. Now you know running update before installation or upgrade never hurts :)
Then your machine is up to date on what's available for upgrading or installation.

---

