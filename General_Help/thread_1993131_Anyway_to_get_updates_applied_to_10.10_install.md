---
title: "Anyway to get updates applied to 10.10 install?"
date: 2012-06-01
forum: General Help
---

### Post by agrayray on 2012-06-01
Hello,

I am curious if there is way to apply all the updates (up to the point where it was stopped) for a 10.10 desktop client.  My girlfriend had it on her laptop and upgraded to 12 but it runs too slow now (it is an old machine)...so she wants to re-install 10.10 as 10.04 had video driver issues but 10.10 was only one that worked good before.

However we would like to take the updates up to the point where the 10.10 updates turned off...is that possible somehow?

Thanks in advance.

---

### Post by Cheesemill on 2012-06-01
Yes, it's possible. You need to edit /etc/apt/sources.list and point it to the location the repositories were moved to:

[http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)

I wouldn't recommend it though as you will be using out-dated software with security vunerabilities, making the machine an easy target for hacking. Instead you could try Xubuntu 12.04 if you want something that will run quicker than Ubuntu 12.04.

---

### Post by drs305 on 2012-06-01
Edit: The maverick repositories haven't appeared in old-releases as yet. When they do you can use the following, but not at the moment. It appears the maverick repositories are still at [http://archive.ubuntu.com](http://archive.ubuntu.com)

Repositories for unsupported Ubuntu releases are stored at [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) 

You can replace the main address of the /etc/apt/sources.list entries (for example *[http://archive.ubuntu.com/](http://archive.ubuntu.com/)*) with *[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)* to access the old repositories.

---

### Post by cortman on 2012-06-01
Just an idea- if standard 12.04 was too slow for you, did you try Lubuntu or Bodhi Linux? Those are both based on Ubuntu, are maintained and up-to-date, and will run really great on low spec hardware.

---

