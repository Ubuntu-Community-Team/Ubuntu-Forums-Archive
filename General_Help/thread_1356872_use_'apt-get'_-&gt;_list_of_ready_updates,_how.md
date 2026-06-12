---
title: "use 'apt-get' -&gt; list of ready updates, how?"
date: 2009-12-16
forum: General Help
---

### Post by jerome schatten on 2009-12-16
Ubuntu 9.10 I'm trying to get a list of updates ready to install from the command line similar to what the update manager gui shows.

I tried **sudo apt-get update** and get this:

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done

So, how do I get the actual list of packages that would be ready to install?
Thanks,
jerome

---

### Post by slakkie on 2009-12-16
aptitude -s safe-upgrade

the -s is to simulate the action.

---

### Post by bodhi.zazen on 2009-12-16
You will get a list if you use apt-get:

```
sudo apt-get dist-upgrade
```

You can also use the -s flag:

```
sudo apt-get -s dist-upgrade
```

---

### Post by jerome schatten on 2009-12-16
> **bodhi.zazen said:**
> You will get a list if you use apt-get:

```
sudo apt-get dist-upgrade
```You can also use the -s flag:

```
sudo apt-get -s dist-upgrade
```

OK... thanks to you both, and both aptitude and apt work as you described.

Here's a snip from my output:

[snip]
Inst evolution-indicator [0.2.4-0ubuntu2] (0.2.4-0ubuntu3.1 Ubuntu:9.10/karmic-updates)
Inst grub-pc [1.97~beta4-1ubuntu4] (1.97~beta4-1ubuntu4.1 Ubuntu:9.10/karmic-updates) []
Inst grub-common [1.97~beta4-1ubuntu4] (1.97~beta4-1ubuntu4.1 Ubuntu:9.10/karmic-updates)
Conf x11-common (1:7.4+3ubuntu10 Ubuntu:9.10/karmic-updates)
Conf kdelibs5-data (4:4.3.2-0ubuntu7.2 Ubuntu:9.10/karmic-updates)
Conf kdelibs5 (4:4.3.2-0ubuntu7.2 Ubuntu:9.10/karmic-updates)
Conf kdelibs-bin (4:4.3.2-0ubuntu7.2 Ubuntu:9.10/karmic-updates)
[snip]

I can understand what 'Inst' is... Install
What does 'Conf' stand for exactly?

Thanks,
jerome

---

### Post by jerome schatten on 2009-12-16
And... while I think of it: Since I've captured the information of what will be installed and upgraded if I follow through with the update, can I use this information to reverse the update and put everything back the way it was before?  Or is there an easier route?

Many thanks for your time,
jerome

---

### Post by bodhi.zazen on 2009-12-16
> **jerome schatten said:**
> And... while I think of it: Since I've captured the information of what will be installed and upgraded if I follow through with the update, can I use this information to reverse the update and put everything back the way it was before?  Or is there an easier route?

Many thanks for your time,
jerome

Ins is telling you what is being installed.
conf = configuration.

reversing an update is not easy to perform.

---

### Post by jerome schatten on 2009-12-16
> **bodhi.zazen said:**
> Ins is telling you what is being installed.
conf = configuration.

reversing an update is not easy to perform.
Understand... thank you again!
jerome

---

### Post by slakkie on 2009-12-16
> **bodhi.zazen said:**
> 
reversing an update is not easy to perform.

I tend to disagree. 

If you want to install packages which would normally not be installed, you can force aptitude to install other versions:

```

# Based on version, will install regardless of preferences file (assume prio 999)
aptitude install hello=2.4-3
# Based on release, will install with prio 990
aptitude install -t stable hello
# Based on release, will install regardless of preferences file (assume prio 999) 
aptitude install hello/testing

```

From: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

Very easy to reverse it (provided the previous version is still available on the repo's).

---

### Post by jerome schatten on 2009-12-16
**Slakkie says:**

> **slakkie said:**
> I tend to disagree. 

If you want to install packages which would normally not be installed, you can force aptitude to install other versions:

```

# Based on version, will install regardless of preferences file (assume prio 999)
aptitude install hello=2.4-3
# Based on release, will install with prio 990
aptitude install -t stable hello
# Based on release, will install regardless of preferences file (assume prio 999) 
aptitude install hello/testing

```From: [http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/](http://blog.opperschaap.net/2009/12/12/using-the-preferences-file-on-debian-and-debian-based-distributions/)

Very easy to reverse it (provided the previous version is still available on the repo's).

I'm afraid your example is a bit above my head. I take it, it would be a file by file reversal, where depencies would be removed as well.  

My main reason for asking all of this is I'm trying to prepare to be able to track down a problem caused by an update. This is why I was asking about getting a copy of what was about to be installed -- in case things got screwed up by the update. I thought I could go back, file by file, until the problem went away. Is this not reasonable? How to search the repos to see if the n-1th version of a package is still available?

Seems to me, if there's no reasonalbe way to recover from a troublesome update, there should be.  Even windoze can do that.

Thanks,
jerome

---

### Post by slakkie on 2009-12-16
apt-cache policy <package> will tell you which version is available per repository.

```

$ apt-cache policy bind9
bind9:
  Installed: (none)
  Candidate: 1:9.6.1.dfsg.P2-1
  Version table:
     1:9.6.1.dfsg.P2-1 0
        800 ftp://ftp.nl.debian.org testing/main Packages
        990 ftp://ftp.nl.debian.org unstable/main Packages
        100 /var/lib/dpkg/status
     1:9.5.1.dfsg.P3-1 0
        500 ftp://ftp.nl.debian.org lenny/main Packages
        500 http://security.debian.org lenny/updates/main Packages

```

If I want the version of Lenny, i'll issue the following command:

aptitude install bind9=1:9.5.1.dfsg.P3-1

Normally all the dependencies are downgraded as well by this. So if you can identify the meta-packages, you would only need to downgrade them and the rest will be downgraded as well.

Please note that this example is from Debian, so the repositories are different, but the concept is exactly the same.

---

### Post by jerome schatten on 2009-12-16
Thank you again... I'll see what I can do. I have a virtual 9.10 machine that I can practice with now that I have some direction.
jerome

---

