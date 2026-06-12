---
title: "Debilitating problem with Chromium dependencies"
date: 2010-01-06
forum: General Help
---

### Post by mcbrennan07 on 2010-01-06
**Solved: I reinstalled the program through terminal, then force-removed it, see last post. I also had a problem with keys which was solved through a certain terminal line and getting a new key (see last 2 posts).**

Hi,

I downloaded Chromium trying to get the Chrome browser to work a while back, and I soon wanted to get rid of it because of how much space it took up. Being very inexperienced, as I still am, I tried just deleting as many files related to Chromium as I could find. This turned out to be a bad idea, because I now cannot install or remove any program:

-Add/Remove doesn't work, citing that Synaptic Package Manager doesn't work.
-Synaptic Package Manager doesn't work, with the error "**The package cxchromium needs to be reinstalled, but I can't find an archive for it.**"
-Terminal commands "sudo apt-get install -f", "sudo apt-get remove chromium-browser", and "sudo apt-get purge chromium browser" all fail with the same error message (bolded above).
-I removed every reference to chromium from Software Sources.

I don't know what I deleted, exactly, because I've been dealing with this for some time now.

I have an Eee 901 netbook, running Jaunty.

Please, does anyone have any suggestions? There is no more I can do on my own. Let me know if I need to provide more information or move this to another forum.

---

### Post by manosx on 2010-01-06
Try opening a terminal and doing
sudo aptitude update
sudo aptitude upgrade
What do you get back?

---

### Post by manosx on 2010-01-06
if it doesn't work try:
sudo dpkg --configure -a

---

### Post by mcbrennan07 on 2010-01-06
Thanks for the help.

I did "sudo aptitude update", and everything seemed to go well until it got to
"Err [http://www.statux.org](http://www.statux.org) jaunty/main Packages
404 Not Found"
Then it continued for a bit with more "Hit"s, "Get"s, and so on until 2 errors beginning with "W: GPG error...", saying that the signatures couldn't be verified because the public key is not available. It suggested that I run apt-get update to correct these problems.

Apt-get update spat back that could not open "/var/lib/apt/lists/lock" because 13 permission denied.

"sudo aptitude upgrade" (and "sudo aptitude safe-upgrade") replied with the fact that "google-chrome-beta" had unmet dependencies.

"sudo dpkg --configure -a" spat back 3 different kinds of errors, all having to do with google-chrome-beta and its "dependency problems."

Thanks for any help... I must have really messed something up.

---

### Post by manosx on 2010-01-06
For the signatures the message must be:
"...following signatures couldn't be verified because the public key is not available: NO_PUBKEY key"
take the key of every entry (if you trust the repository) and:
```
gpg --keyserver keyserver.ubuntu.com --recv key
gpg --export --armor 778978B00F7992B0 | sudo apt-key add -
```
for every one.


The message istructs you to do:
```
sudo apt-get update
```
(sudo for the permissions)

if the output doesn't instruct for a solution then:

It seems the problem is google chrome not chromium(?)
then
I suggest adding the repositories for chrome:
[http://www.jimmyburnett.com/2009/06/how-to-install-google-chrome-in-ubuntu.html](http://www.jimmyburnett.com/2009/06/how-to-install-google-chrome-in-ubuntu.html)
and try again
```
sudo apt-get update
```

---

### Post by mcbrennan07 on 2010-01-06
Okay:

gpg --keyserver [http://repos.eeebuntu.org](http://repos.eeebuntu.org) --recv (long string of numbers from above error)
and
gpg --keyserver [http://ppa.launchpad.net](http://ppa.launchpad.net) --recv (long string of numbers from above error)

both came back with "no key data found for (the web address)" and "no valid OpenPGP data found".


Sorry about forgetting the sudo on the apt-get update. I did "sudo apt-get update", but I got the same three errors from before: no public keys for ppa.launchpad or repos.eeebuntu, and "failed to fetch statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages 404 Not Found"


Okay, I went and added the repository as on the link. I also added the public key as on the link.

I found another forum thread that said to uncheck statux.org in the Third-Party Software repositories because it is no longer used. I then was able to download a public key for repos.eeebuntu.

Now, when I run sudo apt-get update, I only get one error: it still can't find the pubkey for ppa.launchpad.net.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B15AB91951DC1E2

---

### Post by manosx on 2010-01-06
What if you do:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6B15AB91951DC1E2
```

Is the chrom[e/ium] dependency prolem solved?

---

### Post by mcbrennan07 on 2010-01-06
I did that, and still no key data found for ppa.launchpad.net (which might have something to do with chromium).

sudo aptitude update: ppa.launchpad key problem as above

sudo apt-get update: ppa.launchpad key problem as above

sudo aptitude upgrade: "The following packages have unmet dependencies: google-chrome-beta: Depends: libnss3-1d (>= 3.12.3) but 3.12.2~rc1-0ubuntu2 is installed."

sudo apt-get upgrade: "package cxchromium needs to be reinstalled, but I can't find an archive for it"

sudo dpkg --configure --a:
"dpkg: dependency problems prevent configuration of google-chrome-beta:
google-chrome-beta depends on libnss3-1d (>= 3.12.3); however; Version of libnss3-1d on system is .12.2~rc1-0ubuntu2.
dpkg: error processing google-chrome-beta (--configure): dependency problems - leaving unconfigured
Errors were encountered while processing:
google-chrome-beta"

I hope that will tell you something.

EDIT: by the way, I put in your last suggestion as:
sudo apt-key adv --recv-keys --keyserver [http://ppa.launchpad.net](http://ppa.launchpad.net) 6B15AB91951DC1E2

---

### Post by manosx on 2010-01-07
No, you should do:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6B15AB91951DC1E2
```
which i tried and it works for me.

Try removing the packets:
```
sudo apt-get remove google-chrome-beta cxchromium
```

---

### Post by mcbrennan07 on 2010-01-07
[SIZE="1"]Okay, I tried those two things.

The first one (sudo apt-key adv...) did some stuff, and ended saying that:
gpg: key 951DC1E2: "Launchpad PPA for Blueman Development Team" not changed
which probably means that this problem doesn't have to do with the google chrome problem. I do have problems with blueman, but at least it's clear that there's two different problems.

I'll try finding a new key for blueman and putting it into Software Sources.

The second one (sudo apt-get remove...) just ended by saying that "The package cxchromium needs to be reinstalled, but I can't find an archive for it."

I'm pretty sure that link you gave me on how to install Chromium is the one I used to reinstall it. But the only remaining step left to install Chromium is #9-- go to Synaptic and install it. But of course, Synaptic won't open, citing that "The package cxchromium needs to be reinstalled..." etc. I'd be glad to reinstall it, but I wouldn't know how at this point.

I'm not tied to any significant amount of data on this computer; should I consider reinstalling Ubuntu? Or something similar?

EDIT: I installed a new key for blueman. Now, more things work:

sudo aptitude update: works

sudo apt-get update: works

sudo aptitude upgrade: "The following packages have unmet dependencies: google-chrome-beta: Depends: libnss3-1d (>= 3.12.3) but 3.12.2~rc1-0ubuntu2 is installed."

sudo apt-get upgrade: "package cxchromium needs to be reinstalled, but I can't find an archive for it"

sudo dpkg --configure --a:
"dpkg: dependency problems prevent configuration of google-chrome-beta:
google-chrome-beta depends on libnss3-1d (>= 3.12.3); however; Version of libnss3-1d on system is .12.2~rc1-0ubuntu2.
dpkg: error processing google-chrome-beta (--configure): dependency problems - leaving unconfigured
Errors were encountered while processing:
google-chrome-beta"

So I guess that solved one of my problems-- maybe that narrows down the google problem?[/size]

EDIT: Solved?

sudo aptitude update: works
sudo apt-get update: works
sudo aptitude upgrade: upgraded things
sudo apt-get upgrade: said that "chromium-browser" has been kept back
sudo dpkg --configure --a: returned nothing, no errors
Add/Remove works!
Synaptic works!

Okay, so to recap:

I had problems with upgrading, and those errors told me the keys that were the problem.

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com (insert key #)
gave me the name of the application that was causing the problem, and I was able to go to the site and download the key.

I had problems with a mis-uninstalled Chromium, and so I went to
[http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)
I followed the steps, and it successfully reinstalled, all through terminal.

Then, following
[http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it/](http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it/)
I officially uninstalled it using
dpkg --remove --force-remove-reinstreq cxchromium
and
dpkg --remove --force-remove-reinstreq google-chrome-beta
I also used --purge.

Thanks for all your help, manosx! Now maybe my bluetooth will work again, too!

---

### Post by manosx on 2010-01-07
no prob! :)

the bluetooth seems to work in this computer out of the box.. toggling it seems to be broken.. 
[http://forum.eeeuser.com/viewtopic.php?id=68445](http://forum.eeeuser.com/viewtopic.php?id=68445)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)
good luck with that

---

### Post by fragos on 2010-01-07
I've installed Ubuntu Tweak on my systems. It provides the ability to install a number of different software source repositories, Among them is the one for Chromium. With the repository added Chromium is available for install. One installed it will update under the control of the Update Manager. Chromium has daily builds.

---

### Post by manosx on 2010-01-08
I use firefox, but to check this software i have iron browser.
you can check it here:
[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

---

