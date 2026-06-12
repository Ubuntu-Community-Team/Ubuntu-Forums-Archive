---
title: "problem updating system"
date: 2010-08-03
forum: General Help
---

### Post by vicariouslyhere on 2010-08-03
Ubuntu tried to update, but some problems occurred.  The triangle with an exclamation point in it showed up and I rolled my mouse over it.
This is what it says:
"The update information is outdated. This may be caused by network problems or by a repository that is no longer available.  Please update manually by clicking on this icon and then selection 'Check for updates' and check if some of the listed repositories fail."

I did what it says and this came up:
"The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

and in the white box below the message:
"Failed to fetch [http://ppa.launchpad.net/milarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/milarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

How do I manually update ubuntu 10.04?

---

### Post by DougieFresh4U on 2010-08-03
Well you could fire up the terminal and
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by snowpine on 2010-08-03
Welcome to the forums, vicariouslyhere!

[http://ppa.launchpad.net/milarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/milarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz) is not an official Ubuntu repository. You must have added this yourself for some reason. :) You should contact the person who told you to add this for assistance. Or, if you prefer, you can go to System, Administration, Software Sources and uncheck this particular repository so it is skipped in the future.

---

### Post by 23dornot23d on 2010-08-03
You also need to remove the ppa thats failing from your sources list if its no longer functioning.

Menu system - admin - software sources ..... 

Then add this one ... possibly ... check the link first.

The [Web8 link is here]("https://launchpad.net/%7Ewebupd8team/+archive/gthumb") ..... if this is the PPA that you need .....

What packages were you needing from the PPA

sudo add-apt-repository ppa:nilarimogard/webupd8

```

You also seem to have [COLOR=Red]**m**[/COLOR]ilarimogard instead of nilarimogard

```"Failed to fetch [http://ppa.launchpad.net/milarimogar...86/Packages.gz]("http://ppa.launchpad.net/milarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz")  404  Not Found

---

### Post by mocoloco on 2010-08-03
Probably what's happening is the site for that 3rd party PPA is down, that can happen from time to time, especially with smaller sites.  You can go in to software sources and disable it (uncheck it) temporarily.  Then use the update manager and install your updates.  Maybe try enabling that source in a day or two and using the update manager hit the "check now" button and see if the source is working again.

---

### Post by vicariouslyhere on 2010-08-04
the ppa is not in the software sources, and the codes did not work.

---

### Post by DougieFresh4U on 2010-08-04
> **vicariouslyhere said:**
> the ppa is not in the software sources, and the codes did not work.

Let's have a lok at your sources list:

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by vicariouslyhere on 2010-08-04
> **DougieFresh4U said:**
> Let's have a lok at your sources list:

```
gksudo gedit /etc/apt/sources.list
```

Am I supposed to find that ppa in the list because I do not see it in there. :?

---

### Post by 23dornot23d on 2010-08-04
This is the proper link that you should have ..... first letter was a "N" instead of a "M"    -   nilarimogard

[http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/lucid/main/binary-i386/Packages.gz)

This seems to be the way to set your sources back to normal after you used a PPA

It appears to purge the webupd8 things ...... 

So in your source list remove the ones with "webupd8" in there names and you
should return back to normal ..... after doing that and then do a ...... 

apt-get update

This is part of the file contents you were trying to access ..........

```

Package: ppa-purge
Source: ppa-purge
Priority: optional
Section: utils
Installed-Size: 56
Maintainer: Lorenzo De Liso <blackz@ubuntu.com>
Architecture: all
Version: 0.2.7-1~webupd8~lucid
Filename: pool/main/p/ppa-purge/ppa-purge_0.2.7-1~webupd8~lucid_all.deb
Size: 4758
MD5sum: 4f244b907b454092ce53dfef2574c78a
SHA1: 0be28a04a48145f9716b2a0c71af07d1a3bc81fe
Description: disables a PPA and reverts to official packages
 This program disables a PPA from your Software Sources and reverts your
 system back to the official Ubuntu packages. You can use this to return your
 system to normal after testing a new version from a PPA.

```or if you want someone to do it for you ....

Can you post your sources.list ........ someone may be able to help ......... 

As it looks like a typing error on the file name that caused the initial problem ......... 

or you can remove the web8upd ones manually yourself by unticking them in the Menu above.

System - Admin -  Sources ...... 

 Then reload the list afterwards ......

That should hopefully sort it out .......

---

### Post by vicariouslyhere on 2010-08-04
I think that worked.  It wasn't in the sources.list, but I double checked the software sources and I found the webupd8 things.  I unchecked them and I put in the apt-get update and there were no problems and the triangle thing disappeared after I did it.  Hopefully, that will be the end of it.
Thank you!

---

### Post by 23dornot23d on 2010-08-04
Good to hear ..... hope It all goes well for you ...... 

mark as solved in thread tools at top .....

Once that you know its all ok ty ):P

---

