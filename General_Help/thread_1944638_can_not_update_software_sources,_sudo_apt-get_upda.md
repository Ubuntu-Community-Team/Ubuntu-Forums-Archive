---
title: "can not update software sources, sudo apt-get update not working, help!"
date: 2012-03-21
forum: General Help
---

### Post by razaz03 on 2012-03-21
Hi all, 

I'm using 11.04 with Gnome 2.x on my old netbook as [[COLOR="Blue"]_nobody can help here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=11775568#post11775568") and there's a giant exclamation mark in my panel indicating my update info is out of date.

Sudo apt-get update returns the same error as the update manager with all normal sources selected: 

```
Failed to fetch.../ubuntu/dists/natty/main/binary-i386/Packages 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```Of course, it's not offering me the new distros etc I know are available, the exclamation mark won't disappear, and I can't update my ubuntu (even though I despise the unity interface), any advice would be appreciated.

---

### Post by PhantomTurtle on 2012-03-21
Try changing the mirror. (By that I mean just change the mirror from the one in your country to the main one.)

---

### Post by razaz03 on 2012-03-21
> **PhantomTurtle said:**
> Try changing the mirror. (By that I mean just change the mirror from the one in your country to the main one.)

That's the first thing I done, doesn't help!

---

### Post by wojox on 2012-03-21
hmm, what do your sources.list look like?
```
cat /etc/apt/sources.list
```

---

### Post by razaz03 on 2012-03-21
> **wojox said:**
> hmm, what do your sources.list look like?
```
cat /etc/apt/sources.list
```


```
# newer versions of the distribution.
  deb http://archive.ubuntu.com/ubuntu natty main restricted
  deb-src http://archive.ubuntu.com/ubuntu natty main restricted
   
  ## Major bug fix updates produced after the final release of the
  ## distribution.
  deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
  deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted
   
  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
  ## team. Also, please note that software in universe WILL NOT receive any
  ## review or updates from the Ubuntu security team.
  deb http://archive.ubuntu.com/ubuntu natty universe
  deb-src http://archive.ubuntu.com/ubuntu natty universe
  deb http://archive.ubuntu.com/ubuntu natty-updates universe
  deb-src http://archive.ubuntu.com/ubuntu natty-updates universe
   
  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
  ## team, and may not be under a free licence. Please satisfy yourself as to 
  ## your rights to use the software. Also, please note that software in 
  ## multiverse WILL NOT receive any review or updates from the Ubuntu
  ## security team.
  deb http://archive.ubuntu.com/ubuntu natty multiverse
  deb-src http://archive.ubuntu.com/ubuntu natty multiverse
  deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
  deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse
   
  ## Uncomment the following two lines to add software from the 'backports'
  ## repository.
  ## N.B. software from this repository may not have been tested as
  ## extensively as that contained in the main release, although it includes
  ## newer versions of some applications which may provide useful features.
  ## Also, please note that software in backports WILL NOT receive any review
  ## or updates from the Ubuntu security team.
  # deb http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
  # deb-src http://gb.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
   
  deb http://archive.ubuntu.com/ubuntu natty-security main restricted
  deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
  deb http://archive.ubuntu.com/ubuntu natty-security universe
  deb-src http://archive.ubuntu.com/ubuntu natty-security universe
  deb http://archive.ubuntu.com/ubuntu natty-security multiverse
  deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse
   
  ## Uncomment the following two lines to add software from Canonical's
  ## 'partner' repository.
  ## This software is not part of Ubuntu, but is offered by Canonical and the
  ## respective vendors as a service to Ubuntu users.
  deb http://archive.canonical.com/ubuntu natty partner
  # deb-src http://archive.canonical.com/ubuntu natty partner
   
  ## This software is not part of Ubuntu, but is offered by third-party
  ## developers who want to ship their latest software.
  deb http://extras.ubuntu.com/ubuntu natty main
  deb-src http://extras.ubuntu.com/ubuntu natty main

```

---

### Post by razaz03 on 2012-03-23
Anyone?

---

### Post by plucky on 2012-03-23
I would edit the sources.list file and put a # in front of all the lines that start with **deb-src** as you probably don't need the sources files.

Then, can you post the complete output for ```
sudo apt-get update
```

Is it just the **main** repository that is giving the problem?

Or all the repositories?

---

