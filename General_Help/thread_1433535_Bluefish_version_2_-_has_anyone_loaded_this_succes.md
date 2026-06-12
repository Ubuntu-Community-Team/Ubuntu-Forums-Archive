---
title: "Bluefish version 2 - has anyone loaded this successfully?"
date: 2010-03-19
forum: General Help
---

### Post by frank4360 on 2010-03-19
Bluefish version 1.0.7 is in the repositories - but I want to try version 2, which seems much better according to the website.

Has anyone succeeded in loading this? I have tried following the instructions in bluefish.openoffice.nl and I get errors in the "make".

---

### Post by eriqjaffe on 2010-03-19
There are .deb packages available for 8.04 and up:

[http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_8.04](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_8.04)

---

### Post by frank4360 on 2010-03-19
Thanks - I have now succeeded in loading version 2.

 "Installing 2.0.0 (current stable) on Ubuntu 9.04 or newer" is available on [http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer](http://bfwiki.tellefsen.net/index.php/Installing_Bluefish#Installing_2.0.0_.28current_stable.29_on_Ubuntu_9.04_or_newer)


and works perfectly.

Thanks again!!

---

### Post by acid303 on 2010-03-19
add the following line to  /etc/apt/sources.list 
 deb [http://debian.wgdd.de/ubuntu]("http://debian.wgdd.de/debian") jaunty main restricted universe multiverse

Then install the repository cryptographic key and Bluefish: 


apt-get update

apt-get install wgdd-archive-keyring

apt-get install bluefish

---

### Post by andrew.46 on 2010-03-20
Another option is to build the software yourself, for which I have written a small guide:

Howto: Build the newest version of Bluefish under Ubuntu 
[http://ubuntuforums.org/showthread.php?t=1426958](http://ubuntuforums.org/showthread.php?t=1426958)

Andrew

---

### Post by tg3793 on 2012-03-13
> **andrew.46 said:**
> Another option is to build the software yourself, for which I have written a small guide:

Howto: Build the newest version of Bluefish under Ubuntu 
[http://ubuntuforums.org/showthread.php?t=1426958](http://ubuntuforums.org/showthread.php?t=1426958)

Andrew

And I'll confirm that that building yourself looked scary (because of that long list of commands to copy and paste) but worked flawlessly on Ubuntu 10.04 Lucid. I just did it about half an hour ago :-)

---

