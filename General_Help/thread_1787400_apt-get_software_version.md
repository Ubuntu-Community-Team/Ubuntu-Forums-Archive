---
title: "apt-get software version???"
date: 2011-06-21
forum: General Help
---

### Post by Cool Javelin on 2011-06-21
Does apt-get always install the same version of a piece of software regardless of the Ubuntu version I am running? IE. will I get the same version if I am running Hardy or Lucid?

I would like to install Free Pascal on my Ubuntu 10.10 server.

If I use the apt-get (with the -s option) it reports version 2.4.0 will be installed, yet the latest version on the Free Pascal website is 2.4.4.

This even after I do an apt-get update.

Is my only choice to get the software from the website?

Thanks, Mark.

---

### Post by wildmanne39 on 2011-06-21
> **Cool Javelin said:**
> Does apt-get always install the same version of a piece of software regardless of the Ubuntu version I am running? IE. will I get the same version if I am running Hardy or Lucid?

I would like to install Free Pascal on my Ubuntu 10.10 server.

If I use the apt-get (with the -s option) it reports version 2.4.0 will be installed, yet the latest version on the Free Pascal website is 2.4.4.

This even after I do an apt-get update.

Is my only choice to get the software from the website?

Thanks, Mark.
Hi, to make update manager in ubuntu update a package from an outside source the ppa has to be added to update manager by you, so If you can get the ppa for the package then you can update it with update manager, if you can not then you have to install if from there site to have the latest version. Unless you just have to have the latest version it is best to stick with the one in the repository.

---

### Post by sanderd17 on 2011-06-21
When an OS is released, the versions of all software is fixed to prevent breakage.

The only thing that is updated are bugfixes and security fixes, so no new features.

---

### Post by Cool Javelin on 2011-06-21
Thank you **sanderd17** that is what I was looking for in question 1.

To rephrase, I might get version 1.6 in Hardy and version 2.4 in Lucid even if I do the install the same day.

Is there a website I can visit to see what versions of various softwares are supported in other versions of Ubuntu?

Assuming for a moment there is a newer one in Maverick or Natty, is there any work around so I can "fake it out" to make my Lucid get it?
---
And thank you **wildmanne39**, you have given me a new avenue to research so I can better use apt-get.

Of course this poses more questions...
What is ppa? How would I add it to my list of applications?

I will start researching this tonight after my day job.

Rephrasing what you say, I can get a 'ppa' from a third party vendor and tell my Ubuntu to include the application in it's list of goodies?

Thanks all
Mark.

---

### Post by snowpine on 2011-06-21
Hi Mark, you can search which package versions are available for each Ubuntu release at:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

Because Ubunu is "open source software" you are free to install newer applications if you like, and there are several ways to do this. 

The obvious is directly from the developer, for example Free Pascal is available from: [www.freepascal.org](www.freepascal.org)

Other popular options are [Personal Package Archives (PPAs)]("https://launchpad.net/ubuntu/+ppas") and the [Backports repository]("https://help.ubuntu.com/community/UbuntuBackports").

A final option is to use the stable, well-tested, bug-and-security-patched version that's the default for your Ubuntu release. A lot of times people think "newer is better" but that isn't always the case; newer software can introduce bugs and instabilities. Not knowing more about your situation I won't recommend one way or the other.

---

### Post by Cheesehead on 2011-06-21
If you have the devscripts package installed, then you can use the rmadison command:
```
emo:~$ rmadison hello
     hello |      2.2-2 |         hardy | source, amd64, i386
     hello |      2.4-3 |         lucid | source, amd64, i386
     hello |      2.5-1 |      maverick | source, amd64, i386
     hello |      2.6-1 |         natty | source, amd64, i386
     hello |      2.7-1 |       oneiric | source, amd64, i386

```

---

### Post by dFlyer on 2011-06-21
The simple answer is apt-get will only install the version of a program that is currently in it's archives for the version of ubuntu you are running. To install other verions of software you need to use ppa's usually from the web site that creates the program or use backports. If you can download a deb file you can use dpkg -i to install the package, but sometimes that creates dependency hell.

---

### Post by snowpine on 2011-06-21
Cheesehead, 'rmadison' is cool, thanks! :)

---

### Post by sanderd17 on 2011-06-22
Some of those tricks are more stable than others, but all can cause dependancy problems. If it works with 2 different versions of the software, I would not upgrade one.

---

