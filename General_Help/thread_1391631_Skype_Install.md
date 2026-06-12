---
title: "Skype Install"
date: 2010-01-27
forum: General Help
---

### Post by Roshelle on 2010-01-27
Hi I am an absolute beginner at Ubuntu I am attempting to load skype-ubuntu-intrepid_2.1.0.81-1_i386.deb I however get the following error: Dependency is not Satisfiable: libqt4-dbus (>=4.4.3) can anyone give advice thank you

---

### Post by raktarok on 2010-01-27
Try this from a terminal, and then use that deb file:

```
sudo apt-get install libqt4-dbus
```

libqt4-dbus may already be installed though and you may be getting the error because you don't have the appropriate version of libqt4-dbus

I would suggest you to add the mediubuntu software repository and then install skype. That way, you won't have to deal with all these dependency problems manually.Look here on how to do that (just read the first part)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you don't want to read it, just do this (I copied the command from the above page):

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then search for skype in the synaptic package manager or do this:

```
sudo apt-get install skype
```

---

### Post by kostkon on 2010-01-27
> **raktarok said:**
> I would suggest you to add the mediubuntu software repository and then install skype. That way, you won't have to deal with all these dependency problems manually.Look here on how to do that (just read the first part)
Medibuntu has stopped offering Skype.

---

### Post by n0dix on 2010-01-27
Try:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install skype
```

---

### Post by Roshelle on 2010-01-27
Thank you for your help it is appreciated

---

### Post by HermanAB on 2010-01-27
Otherwise, get the 'static' version from the Skype web site and install that.  It contains all dependencies - so it is a slightly larger program, but not significantly so.

---

### Post by kaunofrantas on 2010-02-07
can anyone give step by step how to install static skype. I am able to download and extract the files, but not so sure how to install it?

---

### Post by Ginsu543 on 2010-02-07
If you've downloaded the .deb files, you can install them simply by double-clicking on the icon. It will automatically launch the GDebi Package Installer, and all you have to do is click Install. If not, you can launch GDebi yourself by going to Applications --> System Tools --> GDebi Package Manager and then opening the Skype .deb files to install.

---

### Post by manso.manu on 2010-10-24
> **$sudo apt-get install skype**

Error
skype: Depends: libqt4-dbus (>= 4:4.5.3) but it is not going to be installed
E: Broken packages
[B]
$sudo apt-get install libqt4-dbus[/B]
Error
The following packages have unmet dependencies:
  libqt4-dbus: Depends: libqt4-xml (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.1 is to be installed
               Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.1 is to be installed
E: Broken packages 			 		

Setting  "Update" option correctly in Repositories from Synaptic Package Manager will do the trick.Go to 

[B]System> Administration > Synaptic Package Manager >Settings>repositories >updates
[/B]
and check these in Ubuntu updates


[LIST]
[*]Important security updates(lucid-security)
[/LIST]

[LIST]
[*]Recommended updates(lucid-updates)
[/LIST]

[LIST]
[*]Pre-released updates(lucid-proposed)
[/LIST]
Then enter

[LIST=1]
[*] Skype in Quick Search in Synaptic Package Manager.
[*]Check the required skype package and other skype plugins like skysentilas - extra Functionalites for Linux Skype Client.
[*] Apply and wait for skype to get installed.
[*]Done.
[/LIST]
:smile:

---

