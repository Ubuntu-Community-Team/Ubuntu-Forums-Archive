---
title: "ubuntu's commands are different???"
date: 2012-02-29
forum: General Help
---

### Post by MeriMeri on 2012-02-29
i have two questions!
as we all know, canonical release a new version of ubuntu every six months. 

are the commands (which we type in terminal) the same in all versions??
for example i saw a tutorial about installing firefox 10 in ubuntu 11.10.
does that tutorial works for me in 10.04?


and the next question is about Xubuntu
im running xubuntu 10.04 (due to my old hardware)
can i run those commands under xubuntu 10.04???


Thank you all in advance

---

### Post by oldos2er on 2012-02-29
What commands? Can you provide a link to this tutorial?

---

### Post by MeriMeri on 2012-02-29
that was an example.
you can check this link: [http://www.liberiangeek.net/2011/10/how-to-install-google-earth-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/how-to-install-google-earth-in-ubuntu-11-10-oneiric-ocelot/)


its a tutorial for ubuntu 11.10. but im running Xubuntu 10.04

---

### Post by idoitprone on 2012-02-29
> **MeriMeri said:**
> that was an example.
you can check this link: [http://www.liberiangeek.net/2011/10/how-to-install-google-earth-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/how-to-install-google-earth-in-ubuntu-11-10-oneiric-ocelot/)


its a tutorial for ubuntu 11.10. but im running Xubuntu 10.04

those command should be the same. If it wasn't there will be hordes of people running away from Ubuntu. dpkg and apt-get front-end are package management commands which vary between distro. The only other major distro that uses it on the top of my head is debian

---

### Post by QIII on 2012-02-29
There is a "common core" of commands across Linux.  Many of them are identical to what I used back in my old Unix days.

Some differences are found in things like package management depending on the system used.

For instance yum is used in Fedora and CentOS, zypper in openSUSE.

Direct Unix descendants like the BSDs and OpenIndiana use other commands.

---

### Post by MeriMeri on 2012-02-29
so as i understand, with xubuntu 10.04 i can run ubuntu's commands
thank you all. i asked that because of this: [http://news.softpedia.com/news/How-to-Install-VLC-2-0-on-Ubuntu-11-10-253805.shtml](http://news.softpedia.com/news/How-to-Install-VLC-2-0-on-Ubuntu-11-10-253805.shtml)

wanted to have the latest version of VLC on my xubuntu 10.04:p


thank you all:p

---

### Post by WorMzy on 2012-02-29
There may be some differences between the parameters that commands accept. For example, ```
sort -h
``` won't work on Ubuntu versions 10.04 and prior, but will on versions 10.10 and upwards.

Unmaintained or buggy applications may be dropped from the repos over time, so some commands may not work across versions. Generally speaking though, the core utilities won't change too much over time.

---

### Post by oldos2er on 2012-02-29
> **MeriMeri said:**
> that was an example.
you can check this link: [http://www.liberiangeek.net/2011/10/how-to-install-google-earth-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/how-to-install-google-earth-in-ubuntu-11-10-oneiric-ocelot/)


its a tutorial for ubuntu 11.10. but im running Xubuntu 10.04

To install Google Earth on 10.04, I would use the Medibuntu repository, medibuntu.org. But you can also do it using the method you linked to.

---

