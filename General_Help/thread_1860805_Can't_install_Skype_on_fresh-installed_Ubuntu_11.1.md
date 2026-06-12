---
title: "Can't install Skype on fresh-installed Ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by JesusM on 2011-10-15
Hi!

I'm running a freshly installed Ubuntu 11.10. 

I try to install Skype but I get this message:

```
The following packages have unmet dependencies:

skype: Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed
       Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
       Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed
       Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed
       Depends: libqtcore4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed
       Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed
       Depends: libstdc++6 (>= 4.2.1) but 4.6.1-9ubuntu3 is to be installed
       Depends: libxss1 but it is not going to be installed
```Any idea? Am I doing anything bad?

Thanks

(I'm having similar trouble with other software as wine an others)

---

### Post by DeMus on 2011-10-15
How did you install it? From the Skype website, or using Synaptic or one of the other methods in Ubuntu?
Using Synaptic should take care of the dependencies automatically.

---

### Post by sikander3786 on 2011-10-15
> **JesusM said:**
> Hi!

I'm running a freshly installed Ubuntu 11.10. 

I try to install Skype but I get this message:
[...]
(I'm having similar trouble with other software as wine an others)
Seems like this problem isn't limited to a single package but all across the package manager. From Terminal, we need to see the outputs of these commands please:

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
sudo apt-get install -f
sudo dpkg --configure -a
```

While posting the outputs, separately wrap each output in [code] tags by pressing the # icon in post menu.

---

### Post by JesusM on 2011-10-15
the ouputs:

```
jesusm@stilgar:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
jesusm@stilgar:~$ 
``````
jesusm@stilgar:~$ ls -l /etc/apt/sources.list.d
total 16
-rw-r--r-- 1 root root  82 2011-10-15 11:03 oneiric-partner.list
-rw-r--r-- 1 root root  82 2011-10-15 10:05 oneiric-partner.list.save
-rw-r--r-- 1 root root 134 2011-10-15 11:03 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root 134 2011-10-15 10:05 ubuntu-wine-ppa-oneiric.list.save
jesusm@stilgar:~$ 
``````
jesusm@stilgar:~$ sudo apt-get install -f
[sudo] password for jesusm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jesusm@stilgar:~$ 
``````
jesusm@stilgar:~$ sudo dpkg --configure -a
jesusm@stilgar:~$ 

```

And yes, I think I have a general issue. Also with other software (7zip, dropbox, GIMP, etc) I found them in the Software Center but I have not the 'install' button, just one saying 'use this source'. Maybe is it the same problem?

Thanks a lot for your help!

---

### Post by sriramoman on 2011-10-15
It seems to be more like a problem to **apt-get** tool, itself. It is actually detecting dependencies well, but not resolving it and marking them for installation.
Solution:
[LIST]
[*]Install Synaptic package manager via the Ubuntu software center.
[*]Open the terminal. Run the command
[FONT="Courier New"]$ sudo dpkg -i skype-ubuntu_2.2.0.35-1_amd64.deb[/FONT]
It will list the required dependencies. Note them all. The installation will fail this time, never mind.
[*]Copy, paste each of the noted dependencies in the search field of synaptic package manager and install them all. Synaptic is good, it takes care of marking all the chained dependencies. Chances are there that it will remove skype that was attempted to install (broken) in the previous step. Accept it.
[*]Open the terminal again and install skype.
[FONT="Courier New"]$ sudo dpkg -i skype-ubuntu_2.2.0.35-1_amd64.deb[/FONT]
[/LIST]
This time, it will succeed well.
Good luck. I noticed this problem with Google chrome (**deb package** downloaded from google website) as well. I needed to take this step. Latest **apt-get** kind of sucks because it is not automatic as before. 
The biggest problem is that Ubuntu Software presents it as some "Unknown error". This may scare away new users from Ubuntu.

---

### Post by lovinglinux on 2011-10-15
I just downloaded the 2.2 deb file from Skype web site, right-clicked on the downloaded file and selected the option to open with Software Center. It installed pretty fast, without any errors. Tested and working.

Try that: [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/)

---

### Post by sikander3786 on 2011-10-16
There isn't anything wrong with the outputs you posted above so it is not the issue I was thinking about. Did you try what is mentioned in the above two posts?

---

### Post by manohareaga on 2012-04-14
> **sriramoman said:**
> It seems to be more like a problem to **apt-get** tool, itself. It is actually detecting dependencies well, but not resolving it and marking them for installation.
Solution:
[LIST]
[*]Install Synaptic package manager via the Ubuntu software center.
[*]Open the terminal. Run the command
[FONT=Courier New]$ sudo dpkg -i skype-ubuntu_2.2.0.35-1_amd64.deb[/FONT]
It will list the required dependencies. Note them all. The installation will fail this time, never mind.
[*]Copy, paste each of the noted dependencies in the search field of synaptic package manager and install them all. Synaptic is good, it takes care of marking all the chained dependencies. Chances are there that it will remove skype that was attempted to install (broken) in the previous step. Accept it.
[*]Open the terminal again and install skype.
[FONT=Courier New]$ sudo dpkg -i skype-ubuntu_2.2.0.35-1_amd64.deb[/FONT]
[/LIST]
This time, it will succeed well.
Good luck. I noticed this problem with Google chrome (**deb package** downloaded from google website) as well. I needed to take this step. Latest **apt-get** kind of sucks because it is not automatic as before. 
The biggest problem is that Ubuntu Software presents it as some "Unknown error". This may scare away new users from Ubuntu.



I have tried with your post but I did not get any dependencies that required instead of that I has given me the following error...
dpkg: error processing skype-ubuntu_2.2.0.35-1_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubuntu_2.2.0.35-1_amd64.deb

please check it once.....
Thank you!!!!!

---

