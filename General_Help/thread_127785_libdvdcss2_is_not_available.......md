---
title: "libdvdcss2 is not available?......"
date: 2006-02-09
forum: General Help
---

### Post by lambertrj on 2006-02-09
robert@hellco:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
robert@hellco:~$

and when i add the recomended 

## Backports 

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

i only get new errors...... 

what can i do? :-k

---

### Post by lambertrj on 2006-02-09
bump. 


no one else having this problem?

---

### Post by rharris on 2006-02-09
I believe the mirrormax repos no longer work. Among the few other repos, I know for sure that libdvdcss2 can be found at the PLF repos.

You might try here for a neat tool to build a good sources list with the PLF repos:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Rob

---

### Post by o_fortuna on 2006-02-09
[QUOTE=lambertrj]bump. 


no one else having this problem?[/QUOTE]
Have no fear, it's [Automatix]("http://ubuntuforums.org/showthread.php?t=66563") to the rescue. Automatix has the ability to both install libdvdcss2 (which is illegal in the US because of the DMCA) and w32codecs (same deal), and it involves just a click. It also can install tons of other stuff, like Firefox 1.5. I definitely recommend it.

The other option is to enable the Ubuntu PLF repositories (if you don't want to use Automatix, which does this for you). Just edit your sources.list file:
```
sudo gedit /etc/apt/sources.list
```
and add this line at the end:
```
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
```
That's it. Just
```
sudo apt-get install libdvdcss2
```

---

### Post by kitpierce on 2006-03-08
I already have the suggested repos in my sources list but I still can't add libdvdcss2 or w32codecs to my list.  Any idea what repos Automatix uses so I can add those by hand without it completely rewriting my sources list?

---

### Post by kaamos on 2006-03-08
Have you done
```
sudo apt-get update
```
after making changes to the repos ?

---

### Post by kitpierce on 2006-03-08
Yep - results below... can post sources.list if needed

~$ sudo apt-get update
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Get:5 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Fetched 5B in 5s (1B/s)
Reading package lists... Done

---

### Post by kitpierce on 2006-03-08
OK even wierder, I just tried running Automatix again, but it didn't seem to work either.  I am running Kubuntu so I don't choose every option, but I installed the non-free audio and DVD stuff and then checked for libdvdcss2 and it still doesn't look like it's there.  Did I choose the right thing to install on Automatix?  If so why isn't libdvdcss2 showing up?  I'm confused...

---

### Post by powder on 2006-03-08
libdvdcss2:
[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/)
w32codecs:
[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/)

---

### Post by kitpierce on 2006-03-08
Powder, you quite simply...
**...ROCK!**

Thank you so much for the link, this now works like a charm....  Bless you!

---

### Post by bluemax on 2006-03-11
Sorry if I sound like a complete newb, but what do i do with the files at the FTP site to install libdvdcss2? If I just put the URL in sources.list it gives me an error because it needs additional parameters.

---

### Post by aysiu on 2006-03-11
[QUOTE=bluemax]Sorry if I sound like a complete newb, but what do i do with the files at the FTP site to install libdvdcss2? If I just put the URL in sources.list it gives me an error because it needs additional parameters.[/QUOTE] If all you want is libdvdcss2, just download [this file](http://packages.freecontrib.org/ubuntu/plf/pool/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb) to your desktop and then go to Applications > Accessories > Terminal and type ```
cd Desktop
sudo dpkg -i libdvd*.deb
```

---

### Post by bluemax on 2006-03-11
Thanks for the quick response! I got it installed.

And I will have to read up on using dpkg...

---

### Post by L34NN3 on 2007-01-14
An easier way for a nOOb (like me) is to go to [http://www.getautomatix.com/index.html](http://www.getautomatix.com/index.html) and download Automatix. It works like synaptic but it does all the hard work for you (ie the terminal stuff)... All the help has been great until you get command not recognised n cant go any further - this eliminates that!

---

### Post by ardchoille42 on 2007-01-14
> **powder said:**
> libdvdcss2:
[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/libd/libdvdcss/)
w32codecs:
[ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/)

I'm getting errors with Firefox:

Firefox can't establish a connection to the server at cipherfunk.org.

I can't seem to get Firefox to connect to [http://packages.freecontrib.org/](http://packages.freecontrib.org/) either.

I do see that libdvdcss2 is available here:

[http://www.dtek.chalmers.se/groups/dvd/deb/](http://www.dtek.chalmers.se/groups/dvd/deb/)

but the latest version is 1.2.5

---

### Post by ardchoille42 on 2007-01-14
> **aysiu said:**
> If all you want is libdvdcss2, just download [this file](http://packages.freecontrib.org/ubuntu/plf/pool/i386/free/libdvdcss2/libdvdcss2_1.2.9-1plf3_i386.deb) to your desktop and then go to Applications > Accessories > Terminal and type ```
cd Desktop
sudo dpkg -i libdvd*.deb
```

Does that link still work?

---

### Post by brikul on 2007-01-19
Hi,

I have this package (libdvdcss2) sitting in my updates manager but it won't download. I get this message:

> W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/pool/edgy-plf/free/libdvdcss2_1.2.9-1plf6.10_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/edgy-plf/free/libdvdcss2_1.2.9-1plf6.10_i386.deb)
  404 Not Found

What do I do? :confused:

---

### Post by damaged on 2007-01-21
Why would update manager point to a file that isn't there. That seems a little silly.

Does anyone know why this would be happening?

---

