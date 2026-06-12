---
title: "problem with Synaptic"
date: 2009-09-08
forum: General Help
---

### Post by nezurian on 2009-09-08
Hello!

I am new at linux, and am trying to install some programs by synaptic. but when I search the package, the synaptic cannot find it, so I cannot install them. I know that the program is contained by synaptic. 

For instance, 

I am trying to install Jackd to use my m-audio firewire solo driver. but I cannot install it with synaptic package manager. I search for Jack in the synaptic, but all I got is a blank screen. 

What am I doing wrong ?!

---

### Post by shylent on 2009-09-08
It seems, your software sources are a bit off. Go to System->Administration->Software Sources and make sure, that in the first tab you have at least "main", "universe", "restricted" and "multiverse" checked (jackd is in "universe").

---

### Post by nezurian on 2009-09-08
With your advice, I checked my software sources. main and universe were checked, but the others were not. I checked them too, but I have faced a problem :

"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://tr.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead."


 I do face this problem when I try to use update manager. 

The matter comes from here I guess...

---

### Post by shylent on 2009-09-08
You don't need the "sources" software source.  

Wait, I can see, that the repositories you are trying to use are gutsy. Are you using ubuntu gutsy then?

---

### Post by drs305 on 2009-09-08
> **nezurian said:**
> I search for Jack in the synaptic, but all I got is a blank screen. 

Are you typing jackd in the Quick Search window? If not, try typing the first few letters.

If you are using Quick Search, sometimes it is better to make sure 'Origin' and 'ALL' are selected in the left pane and then scroll through the right pane. You can click in the pane and type the first few letters to get near what you are looking for.

---

### Post by nezurian on 2009-09-08
> **shylent said:**
> You don't need the &quot;sources&quot; software source.  Wait, I can see, that the repositories you are trying to use are gutsy. Are you using ubuntu gutsy then?


I am using 8.0x something. :) It's hardy Heron I guess.

---

### Post by nezurian on 2009-09-08
> **drs305 said:**
> Are you typing jackd in the Quick Search window? If not, try typing the first few letters.

If you are using Quick Search, sometimes it is better to make sure 'Origin' and 'ALL' are selected in the left pane and then scroll through the right pane. You can click in the pane and type the first few letters to get near what you are looking for.


I tried using the first letters, but I have failed. My synaptic does not seem to have this programs at all .

---

### Post by drs305 on 2009-09-08
> **nezurian said:**
> I am using 8.0x something. :)

Your sources.list repositories are all for Gutsy, which is why they can't be found. Which version are you running?
```

lsb_release -a

```
If you aren't using Gutsy, you need to replace your sources.list  For a start, try replacing "gutsy" references with "hardy" or whatever newer version you are using. 
```

gksudo gedit /etc/apt/sources.list

```


If you are using Gutsy, it has reached it's End of Life.
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by nezurian on 2009-09-08
> **drs305 said:**
> Your sources.list repositories are all for gutsy, which is why they can't be found. Which version are you running?
```

lsb_release -a

```If you are using Gutsy, it has reached it's End of Life.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


Wrote code, get: 

Ubuntu 8.04 
Codename Hardy

---

### Post by nezurian on 2009-09-08
If you aren't using Gutsy, you need to replace your sources.list  For a start, try replacing "gutsy" references with "hardy" or whatever newer version you are using. 
```

gksudo gedit /etc/apt/sources.list

```
The soruces.list comes with a blank page. damit. :)

---

### Post by drs305 on 2009-09-08
Normally the blank page is the result of a typo. I noticed in your post you typed [COLOR="Red"]soruces.list[/COLOR] It means the file cannot be found, so gedit makes a new file with that path/address. Make sure you entered the command correctly (cut/paste).

Here is a copy of a generic hardy sources.list genrerated from this site: [http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/"):

> 
################### OFFICIAL UBUNTU REPOS ###################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse 


Also, confirm this is a normal Hardy install correct from a LiveCD or online upgrade.

---

