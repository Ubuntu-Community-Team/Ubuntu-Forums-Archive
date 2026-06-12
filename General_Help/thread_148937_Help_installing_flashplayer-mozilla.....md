---
title: "Help installing flashplayer-mozilla...."
date: 2006-03-23
forum: General Help
---

### Post by spyro on 2006-03-23
I do not see the flashplayer-mozilla in Synaptic.
I enabled all the repositories.
I have downloaded flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb.

[I] sudo apt-get install flashplayer-mozilla
 Reading package lists... Done
 Building dependency tree... Done
 E: Couldn't find package flashplayer-mozilla[/I]

 [I]sudo dpkg -i flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb
dpkg: error processing flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
 Errors were encountered while processing:
 flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb[/I]

So I am having trouble. How do I install this plugin?

---

### Post by aysiu on 2006-03-23
You don't need to download the .deb separately. Apt-get both fetches *and* installs the .deb for you.

Also, after you enable extra repositories, you need to let apt-get know you updated them: ```
sudo apt-get update
sudo apt-get install flashplayer-mozilla
```

Finally, when you say you enabled "all" the repositories, does that include Multiverse? Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by spyro on 2006-03-23
Still not luck.

 cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by aysiu on 2006-03-23
Apart from the duplicate sources at the bottom, your list (at a glance) seems okay.

Can you try following these instructions, though?
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try ```
sudo apt-get update
sudo apt-get install flashplayer-mozilla
``` and post the output (including the commands *and* any errors) here.

---

### Post by deadgobby on 2006-03-23
There may be a simple way of getting this done. Go to this link and you are going to love this. [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
Once you get Easy Ubie loaded. Then go to your Synaptic and type in Flashplayer. Easy and makes life with Ubie much better.

---

### Post by spyro on 2006-03-23
/tmp$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
...
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 4B in 1s (2B/s)
Reading package lists... Done


/tmp$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]E: Couldn't find package flashplayer-mozilla[/COLOR]

---

### Post by spyro on 2006-03-23
Thanks all,

The EasyUbuntu seemed to work.

-S

---

