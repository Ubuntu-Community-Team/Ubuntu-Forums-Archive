---
title: "Can't install program from PPA"
date: 2012-02-25
forum: General Help
---

### Post by A Traveller on 2012-02-25
Hi all.

I have followed the steps as instructed at the following page but the Pinta program hasn't appeared in the Applications menu.

[https://launchpad.net/~pinta-maintainers/+archive/pinta-stable](https://launchpad.net/~pinta-maintainers/+archive/pinta-stable)

Here is what I did:-

In the terminal,

sudo add-apt-repository ppa:pinta-maintainers/pinta-stable

then

sudo apt-get update

When that didn't work, I tried:-

sudo gedit /etc/apt/sources.list

then adding these two lines at the bottom of the page and saving.

deb [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) lucid main

then

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A5A1D6B2

and then

sudo apt-get update

That also didn't work, so I also tried adding the following but it still hasn't worked:-

sudo apt-get install pinta

this gave me

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pinta

and

sudo apt-get install pinta-stable

which gave me

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pinta-stable


The following appear in Software Sources:-

[http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) main
[http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) main (Source Code)
[http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) main
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) main

If anyone could shed any light on what I'm doing wrong, I'd be grateful. Thanks.

---

### Post by josephmills on 2012-02-25
Not sure if I can be of much help but can you see it at all with a ```
apt-cache search pinta
```
like I said not sure if this will help but have a good one

---

### Post by Krytarik on 2012-02-25
> **A Traveller said:**
> sudo apt-get install pinta

this gave me

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pinta
That's because there are no packages for Lucid 10.04 in both the official repos and that PPA, for installing Pinta. But you could install version 1.0 of it from WebUpd8's PPA:

[http://www.webupd8.org/2011/01/install-pinta-06-in-ubuntu-ppa.html](http://www.webupd8.org/2011/01/install-pinta-06-in-ubuntu-ppa.html)

But I suggest disabling that PPA after the installation of Pinta, as it includes many other packages as well, to which you may not want to be upgraded.

Regards.

---

### Post by A Traveller on 2012-02-26
Thanks for the suggestion, josephmills. It brought up the following:-

W: Duplicate sources.list entry [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/) lucid/main Packages (/var/lib/apt/lists/ppa.launchpad.net_pinta-maintainers_pinta-stable_ubuntu_dists_lucid_main_binary-amd64_Packages)

Thanks Krytarik. I think I see what you mean. The list only brings up 'mono-addins' and not 'pinta' for Lucid, but does bring up pinta for the other distros. I did notice that but because I am really inexperienced, I didn't know how to interpret it. Anyhow, I followed the instructions at the link you provided and it seems to have installed the program fine. Thanks!

---

