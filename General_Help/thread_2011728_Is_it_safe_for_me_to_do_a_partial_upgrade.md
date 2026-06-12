---
title: "Is it safe for me to do a partial upgrade"
date: 2012-06-27
forum: General Help
---

### Post by coldjeanz on 2012-06-27
I've had the partial upgrade notification for about 2 weeks now and I've been ignoring it out of fear of breaking my system. But it's really bugging me that I can't install "Important Security Updates" (referring to 3 different kernel installs where the checkboxes are disabled and I can't install them). 

I ran this in terminal

sudo apt-get dist-upgrade

and it told me:

> The following packages will be REMOVED:
  libplank3-0
The following NEW packages will be installed:
  linux-headers-3.2.0-25 linux-headers-3.2.0-25-generic
  linux-image-3.2.0-25-generic
The following packages will be upgraded:
  libplank-common linux-generic linux-headers-generic linux-image-generic
4 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 50.6 MB of archives.
After this operation, 216 MB of additional disk space will be used.


Is something highly likely to go wrong if I go ahead with it?

---

### Post by wilee-nilee on 2012-06-27
I think you are safe to run the dist-upgrade for kernels that is a standard hold requiring this command.

---

### Post by Cheesemill on 2012-06-27
That's normal, it isn't a partial upgrade.

A partial upgrade will inform you with the words 'partial upgrade'.

---

### Post by coldjeanz on 2012-06-27
It did, every time I open up update manager it tells me it wants to do a partial upgrade.

---

### Post by wildmanne39 on 2012-06-27
Hi, a partial upgrade is normally a bad idea.
[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)
Edit: Yes this link is talking about the developmental version of ubuntu but it still remains true for normal release.

I myself have done partial upgrade and it broke apt-get.
Thanks

---

### Post by coldjeanz on 2012-06-27
I don't understand then, am I just never going be able to update my kernel again?

---

### Post by wildmanne39 on 2012-06-27
Hi, I do not know for sure usually these matters resolve themselves by allowing the packages on the server time to finish updating.

Since you have been waiting you could try another server and see what it tells you or see what packages it wants to do the partial upgrade on and put them on hold so they do not update or just go for it and see what happens.

Have a look here.
[http://www.google.com/search?q=partial+upgrade+ubuntu&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=partial+upgrade+ubuntu&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)
Thanks

---

### Post by Frogs Hair on 2012-06-27
Run the sudo apt-get update to update the package system. Partial upgrade notices appear when all the packages for an update are not available . Run check for updates or the command above. 

What type of updates are you receiving ? When opening update manager > settings > updates there is a check list. I would not recommend using pre-released updates or unsupported updates because they can result in partial upgrades . If you are not using those options it is most likely the package system needs updating.

You can also choose another download sever if the package system is not updating properly.

---

