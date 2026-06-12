---
title: "I lost OpenOffice while upgrading to 3.1 (Jaunty)"
date: 2009-12-29
forum: General Help
---

### Post by Rackstar on 2009-12-29
Hi,

First of all, thanks for reading this post!

I tried upgrading my OpenOffice to 3.1 using this tutorial:

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

It involves a partial upgrade and uses ppa 
```
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```

Now what I read is:
> It appears that the PPA repositories are empty right now, so these instructions won't work.

e.g. for
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main

Web-browsing to
[http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/hardy/main/binary-i386/Packages)
shows that the file exists, but it is empty.

In the meantime, it's necessary to install openoffice the command-line way. 

But I read this too late. I did the partial upgrade. Only removed OpenOffice. 

I removed the ppa from my sources, but I still can't install through synaptic. I also tried the .deb from openoffice.org but it also didn't work.

When I try to install it by apt-get, I get this:
```
ruben@ruben-laptop:~$ sudo apt-get install openoffice.org
[sudo] password for ruben: 
apt-get: install openoffice.org
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Sommige pakketten konden niet geïnstalleerd worden. Dit kan betekenen dat u
een onmogelijke situatie gevraagd hebt of dat u de 'unstable'-distributie 
gebruikt en sommige benodigde pakketten nog vastzitten in 'incoming'.
De volgende informatie helpt u mogelijk verder:

De volgende pakketten hebben niet-voldane vereisten:
  openoffice.org: Vereisten: openoffice.org-core (= 1:3.0.1-9ubuntu3.1) maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-writer maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-calc maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-impress maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-draw maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-math maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-base maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-report-builder-bin maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-officebean maar het zal niet geïnstalleerd worden
                  Vereisten: openoffice.org-writer2latex maar het zal niet geïnstalleerd worden
                  Aanbevelingen: openoffice.org-filter-binfilter maar het zal niet geïnstalleerd worden
E: Niet-werkende pakketten:

```
Vereisten = Requires 
Aanbevelingen = recommended
geïnstalleerd = installed
maar het zal niet geïnstalleerd worden = but it won't be installed

Any ideas what to do?

Thanks in advance!

Ruben

---

### Post by Rackstar on 2009-12-29
Sorry, to do this, but it's quite urgent.. BUMP

---

### Post by tom66 on 2009-12-29
EDIT: I didn't correctly read your post. I was going to recommend you installed a deb but you said you already did so. What was the error message or problem?

---

### Post by Rackstar on 2009-12-29
I don't exactly recall it. But it kept giving me errors, something in the line of:
$ soffice
Unable to locate(open?) /path/openoffice.bin
Unable to locate(open?) /path/someotherfile
Same if I tried $ openoffice.org

---

### Post by eveningsky339 on 2009-12-29
Completely remove every ounce of Open Office that may be left behind.  I believe this can be done with the "autoremove" command.

> sudo apt-get autoremove xxx

That should clean things up.  Then try to grab a .deb or use apt-get.  Post back and tell us how it goes.

---

### Post by Hagar Delest on 2009-12-29
See here perhaps: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

