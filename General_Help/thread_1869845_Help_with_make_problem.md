---
title: "Help with make problem"
date: 2011-10-26
forum: General Help
---

### Post by Avalanchis on 2011-10-26
Hello,

I am working with some hardware that is using kernel version 2.6.20.  I'm trying to set up an ubuntu desktop development environment that is as close as possible to that, so I've set up a VM with ubuntu 7.04 (feisty) on it, which uses the same kernel version as my hardware.

Now, I'm trying to install and build a driver on this VM, but when I run install.sh, I'm seeing the following error:

**make: g++: Command not found**

I've found some other posts which suggest I should install the build-essentials package, so I've tried this:

```
sudo apt-get install build-essential g++
```

but this results in the following error:

**E: Couldn't find package build-essential**

I've tried doing this:

```
sudo apt-get update
```

but then I see a lot of these error messages:

**404 Not Found [IP 91.189.92.177 80]**

What would be the best/easiest way for me to get g++ installed?

Thanks!

Alan

---

### Post by surfer on 2011-10-26
are you connected to the internet?

did you change the /etc/apt/sources.list for feisty? as it is no longer supported the mirror is now on [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) .

---

### Post by Avalanchis on 2011-10-26
Thanks for the reply!

Yes, I am connected to the internet.

No, I haven't changed sources.list.  I'm not exactly sure what I need to change.

Here is what it looks like now:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by surfer on 2011-10-26
you need to change all the
```
 http://us.archive.ubuntu.com/ubuntu/
``` to ```
http://old-releases.ubuntu.com/ubuntu/
``` that should be all there is to it.

---

### Post by donkyhotay on 2011-10-26
Do you have internet access from within the VM? Just because the computer can access the internet doesn't mean that the VM itself is connected to the internet. Try pinging from within the VM first and if that doesn't work then take a look at your sources.

---

### Post by Avalanchis on 2011-10-26
I changed /etc/apt/sources.list references from:

```
http://us.archive.ubuntu.com/ubuntu/
http://security.ubuntu.com/ubuntu

```

to this:

```
http://old-releases.ubuntu.com/ubuntu/
```

then ran

```
sudo apt-get update
```

and it succeeded.

I was then able to successfully run:

```
sudo apt-get install build-essential g++
```

and then I ran my install.sh and it worked!

**Thanks so very much for the help!**

Alan

---

