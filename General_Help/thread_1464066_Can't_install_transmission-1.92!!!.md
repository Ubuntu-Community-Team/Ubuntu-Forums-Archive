---
title: "Can't install transmission-1.92!!!"
date: 2010-04-27
forum: General Help
---

### Post by ub_ on 2010-04-27
Hello All,

                                 I want to start off by saying I'm very new to Ubuntu. I have been using Ubuntu for about a week now and have not looked back!! Now on to my issue. I have been tying to update Transmission 1.75(9117) to the lasted version (transmission-1.92) but i can't seem to get the Synaptic Package Manager to find it. I have downloaded transmission-1.92 and extracted it on to the desktop but Synaptic Package Manager still can't find it.  Any help would be great thanks!!

---

### Post by oldos2er on 2010-04-27
Which version of Ubuntu did you install?

If you downloaded a *.deb file, double-click it to install. Synaptic won't see it, which is normal.

---

### Post by ub_ on 2010-04-27
> **oldos2er said:**
> Which version of Ubuntu did you install?

If you downloaded a *.deb file, double-click it to install. Synaptic won't see it, which is normal.


When i go to About Ubuntu

Ubuntu 9.10 - the Karmic Koala - released in October 2009 and supported until April 2011.

I'm guessing *.deb is in the transmission-1.92 folder?

---

### Post by oldos2er on 2010-04-28
No, *.deb is a file, not a folder. Can you give a link to what you downloaded? Wondering if it's a tarball.

---

### Post by ub_ on 2010-04-28
> **oldos2er said:**
> No, *.deb is a file, not a folder. Can you give a link to what you downloaded? Wondering if it's a tarball.
 
 
Ok..Sorry if i sound ignorant it's just that I'm still really new to ubuntu...:confused:
 
Here's the link...
 
[http://linux.softpedia.com/get/Communications/Filesharing/Transmission-4856.shtml](http://linux.softpedia.com/get/Communications/Filesharing/Transmission-4856.shtml)

---

### Post by oldos2er on 2010-04-28
That is source code that needs to be compiled, and here are instructions to do so: [http://trac.transmissionbt.com/wiki/Building](http://trac.transmissionbt.com/wiki/Building)

There is a *.deb file for Transmission 1.92, but it's for Lucid Lynx (10.04), I'm not sure it would install on 9.10. Links to the *debs are here: [http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all)

---

### Post by wojox on 2010-04-28
[Howto: Build the BitTorrent client Transmission under Karmic Koala]("http://ubuntuforums.org/showthread.php?t=1391718&highlight=transmission")

---

### Post by ub_ on 2010-04-28
> **oldos2er said:**
> That is source code that needs to be compiled, and here are instructions to do so: [http://trac.transmissionbt.com/wiki/Building](http://trac.transmissionbt.com/wiki/Building)

There is a *.deb file for Transmission 1.92, but it's for Lucid Lynx (10.04), I'm not sure it would install on 9.10. Links to the *debs are here: [http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=transmission&searchon=names&suite=all&section=all)




I did the following

> sudo apt-get install build-essential automake autoconf libtool pkg-config libcurl4-openssl-dev intltool libxml2-dev libgtk2.0-dev libnotify-dev libglib2.0-devOk sweet!! It ran, but when i follow the rest on the steps i get > tar: transmission-1.92.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

**Building from a tarball[ ¶]("http://trac.transmissionbt.com/wiki/Building#Buildingfromatarball")**

 $ tar xvjf transmission-1.76.tar.bz2
$ cd transmission-1.76
$ ./configure -q && make -s
$ su (if necessary for the next line)
$ make install

---

### Post by Vaphell on 2010-04-28
if you want to automatically update software you can use PPA repos - these are the private repositories that can be added to the package source list and synaptic will see them. They allow to install newer versions than the locked one in official repos.

[https://launchpad.net/~transmissionbt/+archive/ppa](https://launchpad.net/~transmissionbt/+archive/ppa)

instructions are there

---

### Post by ub_ on 2010-04-28
Thanks for the help everyone!! 

[wojox]("http://ubuntuforums.org/member.php?u=802919") that link is what did the trick... you rock!!!:guitar:

---

