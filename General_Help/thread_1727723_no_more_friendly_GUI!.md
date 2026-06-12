---
title: "no more friendly GUI!"
date: 2011-04-12
forum: General Help
---

### Post by shadramon on 2011-04-12
[SIZE=2]hey guys

it goes like this 
i recently installed a lot of packages on my plat. last one virtualbox which i had a problem in installing it i remember at the time that i tried to install it the system popped up a message saying something like this index courapted..upgrad is needed anyways i did upgrad everything seemed fine and perfect but when i restarted my system later it started as if it was 1975 in a console mode          

btw am a new user *Any help would* be most welcomed ;)
[/SIZE]

---

### Post by WorMzy on 2011-04-12
Login, then run
```
startx
```

Does anything happen? Do you get any error messages?

---

### Post by shadramon on 2011-04-12
i got some info and this i could figure as the errors 


(EE) failed to load module "nvidia" (model dos not exist, 0)
(EE) no drivers available 


fatal server error: 
 no screen found 

xinit: no such file or directory (error2): unable to connect to Xserver
xinit: no such process(errno3): server error

---

### Post by IWantFroyo on 2011-04-12
echo exec ck-launch-session gnome-session >> .xinitrc

---

### Post by shadramon on 2011-04-12
please explain more 

ubuntu is like a black hole for me right now

---

### Post by WorMzy on 2011-04-13
Try the following:

```
sudo apt-get purge nvidia-current && sudo apt-get install nvidia-current
```

This will completely remove the driver for your nVidia graphics card, then reinstall it.

Afterwards, run

```
sudo modprobe nvidia
```

Which will make sure that the driver is loaded into the kernel.

Then try startx again.

---

### Post by shadramon on 2011-04-13
> **WorMzy said:**
> Try the following:

```
sudo apt-get purge nvidia-current && sudo apt-get install nvidia-current
```This will completely remove the driver for your nVidia graphics card, then reinstall it.

Afterwards, run

```
sudo modprobe nvidia
```Which will make sure that the driver is loaded into the kernel.

Then try startx again.


when i wrote the first command in the end of the lines it gave me this 

```
 E:unable to locat package nvidia-current
```

and after writing 

```
 sudo modprobe nvidia 
```

i get this: 

```
 WARRNING: All config files need .conf: /etc/modprobe .d/blacklist, it will be ignored in a future release.
FATAL: Moudl nvidia not found.
```

---

### Post by WorMzy on 2011-04-13
Are you sure that you spelt it correctly?

---

### Post by shadramon on 2011-04-13
yes am sure 
i guess ubuntu deleted the nvidia driver in the upgrade or i did by mistake 
plus i have to admit that i missed a little with blacklist file 

the command above is not working with me :( 
i wrote them as they are

---

### Post by WorMzy on 2011-04-13
What changes did you make to the blacklist? Have you blacklisted the nvidia module? I don't know if that would stop you manually loading it into the kernel or not.

What does dpkg have to say about your installed nvidia packages?
```
dpkg -l "*nvidia*" | less
```

Which packages have "ii" at the start?

---

### Post by shadramon on 2011-04-13
```
ii   nvidia-173-modaliases    173.14.28-Oubuntu1    Modaliases for NVIDIA binary X.org driver
ii   nvidia-96-modaliases                 96.43.19-Oubuntu1               Modaliases for the NVIDIA binary X.org driver
ii   nvidia-common                            0.2.24                                             Find obsolete NVIDIA drivers 
ii   nvidia-current-modaliases             260.19.06-Oubuntu1         Modaliases for the NVIDIA binary X.org driver
ii   nvidia-glx                                    1.0.8776+2.6.15.12-57.8                          NVIDIA binary XFree86 4.x/X.org driver
ii   nvidia-kernel-common                  20051028+1                         NVIDIA binary kernel module common file
ii   nvidia-kernel-source                     1.0.8776+2.6.15.12-57.8         NVIDIA binary kernel module source
``` 


i disabled my wireless driver cuz installed madwifi

i did some research in the forums solution to such a problem and here is what i did

i made sure that ubuntu desktop is installed (gnome)
and i installed nvidia-glx hoping that it will solve my problem anyways i rebooted, got the shell screen again asking me to login and to enter my pass

should i make a fresh install?

---

### Post by WorMzy on 2011-04-13
Looks like you don't actually have the driver installed.

Can you run
```
sudo apt-get update && apt-cache search nvidia | grep "kernel module"
```

You already have the common files installed, you just need to install one of the binary drivers.
```

sudo apt-get install nvidia-current
``` should net you the most up-to-date driver, but you got an error regarding that earlier, so I'm not sure if it's available to you or not (for whatever reason).

---

### Post by shadramon on 2011-04-13
The first command result lots of line like this 

```
w: Failed to fetch http://archive.ubuntu.com/ubuntu/..... Temporary failure resolving 'archive.ubuntu.com'

#and

w: Some index files failed to download, they have been ignored, or old ones used instead.
nvidia-kernel-common - NVIDIA binary kernel module common file 
nvidia-kernel-source - NVIDIA binary kernel module source 
nvidia-lagacy-kernel-source - NVIDIA binary 'lagacy' kernel module source
```


When writing the second command i get this: 

```
Reading package lists... Done
Building dependency tree 
Reading state information... Done 
E: Unable to locate package nvidia-current
```

is there any other code i can run that could solve this?
is there any possibility that my data got corrupted or is it only the gpu driver thats cusing all this?

thanks for your effort in helping me solve this,

---

### Post by WorMzy on 2011-04-13
It looks like you have a problem with your software sources. 

```
sudo nano /etc/apt/sources.list
```

Check yours in comparison to mine:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick universe
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
```

Make changes to yours where necessary, but be aware that if you're using Lucid, you should use "lucid-security", etc, instead of "maverick-security". If you're not sure which version you're running now (considering you mentioned upgrading in your first post, you may not have the version you originally installed), run
```
lsb_release -a
``` and it should tell you.

EDIT: Almost forgot to mention; to exit nano, press Ctrl+X. It will ask you whether to save changes or not.

---

### Post by shadramon on 2011-04-14
#IGNORE THIS REPLAY, GO DOWN...

 am gonna write everything i have seen in the sources.list before i change anything 

```
## MAJOR BUG FIX UPDATES produced after the final release 
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-securitay main restricted universe multiverse
## BACKPORTS REPOSITORY (Uunsupported. May contain illegal packages. Use at own risk.)
deb http://archive.ubuntu,com/ubuntu dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 
## PLF REPOSITORY (Unsupported. My conftaqin illegal packages. Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb http://archive.ubuntu.com/ubuntu maverick universe 
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```my ubuntu version as shown 

```
 No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 10.10
Release: 10.10
Codename: maverick
```thats all beffor editing anything 

right now im restarting my system 

i notece this new lines in the shell after restarting 

```
12 packages can be updated.
12 updates are security updates.

```everything else semes to be the same and when applying

sudo apt-get install nvidia-current  i get the same old result :(

---

### Post by shadramon on 2011-04-14
wait i applied the code without connecting my laptop to the internet ._. 
-note: first time above i applied these codes my laptop was connected but after editing my source file it wasn't. btw i did change all the source file to be the same as WorMzys file!-
i just did but this time its connected 
```

sudo apt-get update && apt-cache search nvidia | grep "kernel module"
```its being updated :') 
afer i finish this i will run:
```

sudo apt-get install nvidia-current
```and waiting for the results

---

### Post by WorMzy on 2011-04-14
I think you can see what the problem is from your sources.list. You must have originally installed Dapper Drake (6.06), and have now upgraded to Maverick Meercat (10.10), but you're still trying to get updates for Dapper.

Looks like you're on track to getting it sorted now though. Let me know if you still have problems. :)

---

### Post by shadramon on 2011-04-14
> **WorMzy said:**
> I think you can see what the problem is from your sources.list. You must have originally installed Dapper Drake (6.06), and have now upgraded to Maverick Meercat (10.10), but you're still trying to get updates for Dapper.

Looks like you're on track to getting it sorted now though. Let me know if you still have problems. :)


i am writing this comment from my laptop i have my desktop back :D
and everything is working great as before the problem :D
there was no need for a fresh installation of Ubuntu or anything that will delete my data :')

Thank you from all my heart WorMzy for your time and effort helping me solve this and making me learn new stuff in Ubuntu Linux :)

---

### Post by WorMzy on 2011-04-14
No problem. :)

---

