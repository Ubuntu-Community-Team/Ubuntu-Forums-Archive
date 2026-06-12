---
title: "Wireshark Install"
date: 2011-07-03
forum: General Help
---

### Post by bigwhiskie on 2011-07-03
Can anyone assist with installing Wireshark 1.6.0? Have tried from software center and PPA. Always get dependency errors.
----------------
From the terminal:
"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wireshark : Depends: libwireshark1 (>= 1.6.0-1) but it is not going to be installed
             Depends: libwiretap1 (>= 1.6.0-1) but it is not going to be installed
             Depends: libwsutil1 (>= 1.6.0-1) but it is not going to be installed
             Depends: wireshark-common (= 1.6.0-1~ppa1) but it is not going to be installed"
----------------------
Get the same results when trying to use the package manager.

---

### Post by Dangertux on 2011-07-03
What version of ubuntu are you using wireshark 1.6.0 is only in the oneiric ppas I believe. If that is the version you are using you can check that the universe repo is added. 

Additionally you can and IMO should install it with subversion. More info on that at this link. 

[http://www.wireshark.org/develop.html](http://www.wireshark.org/develop.html)

---

### Post by bigwhiskie on 2011-07-03
I'm using 11.04 (Natty). I don't know what you mean by "subversion", but I do have the universe repo checked.

---

### Post by uRock on 2011-07-03
Natty only offers Wireshark 1.4.6-1, which should be installable via Ubuntu Software Center, Synaptic Package Manager or terminal with the **sudo apt-get install wireshark** command.

Packaging info linked here [http://packages.ubuntu.com/search?keywords=wireshark](http://packages.ubuntu.com/search?keywords=wireshark)

---

### Post by Dangertux on 2011-07-03
[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=wireshark](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=wireshark)

Are you specifically trying to install 1.6.0? Or just wireshark. Because apt-get install wireshark will get you 1.4

What I mean by subversion is using subversion (apt-get install subversion) to download the source for 1.6.0. then you can compile from the source. Otherwise you may have to add the oneiric ppa to download that version from the repos. There are more details on subversion in the link in my first post.

Dang beat me to it ;)

---

### Post by elamericano on 2011-07-12
I am trying do this from a PPA as well: [https://launchpad.net/~n-muench/+archive/programs-ppa2/+build/2563503](https://launchpad.net/~n-muench/+archive/programs-ppa2/+build/2563503)

I want to stick with Lucid for this. Anyway, it almost works. The problem is that apt-get refuses to go ahead:

The following packages have unmet dependencies:
  libwiretap1: Depends: libwsutil1 (>= 1.6.0-1) but 1.6.0-1~ppa1 is to be installed

It has clearly misunderstood that 1.6.0-1~ppa1 = 1.6.0-1. Unfortunately, searching the man pages to force the install or ignore this dependency (-f or -m) has been futile. I'm used to Linux letting you do what you feel is best, but I can't get past this child-proof program.

---

