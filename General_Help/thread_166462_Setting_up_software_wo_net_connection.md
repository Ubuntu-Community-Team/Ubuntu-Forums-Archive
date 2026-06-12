---
title: "Setting up software w/o net connection"
date: 2006-04-26
forum: General Help
---

### Post by daniel2501 on 2006-04-26
It would be really great if you folks have any ideas for this little issue of mine.
I use a computer at work to do some php development stuff. It doesn't have an internet connection, and getting one is not an option. I've installed ubuntu on it before from install CD, and gotten some extra debs you'd need for php. I recently wiped the partition and installed Dapper, but this time it's pretty apparent that downloading all the debs needed from the internet connection at home is going to be a pain when considering all the dependencies. Have you experienced a similar situation? There must be a creative way to do this aside from manually d/ling all the debs and putting them on a usb hd and creating your own deb file:/// type repo on the connectionless machine...

---

### Post by enopepsoo on 2006-04-28
Maybe you could convince the sysadmin at work to give you ssh access so you could get to your home computer.  It's not really a security risk to allow ssh.  You could shell in, wget the debs and transfer them across you secure shell.
Of course if you are saying no one at work has the internet, then I don't really think there is any way of getting the files.

Edit: of course the easier thing would be to just download them on some computer on your (assumed) network and smb them across.

---

### Post by daniel2501 on 2006-04-29
Thank you for your suggestion. I should clarify though. The computer at work is not connected to any network or to the internet, so actually having access to online or network repositories isn't an option.
So far I've come up with this not so satisfactory solution: 
Take the debs from the computer at home stored in /var/cache/apt/archives, and put them on a usb hd. Then make a repository on the work computer out of the archives/ directory, which should have all the packages installed on my home computer, however the home computer's deb archives doesn't contain many of the packages I have installed at home.  It's odd because I thought that I had apt set up to only delete debs for packages no longer available and that had been uninstalled. None the less, some of the dependencies needed for php5 are not in the archives/ directory, so I've needed to manually download them.
There must be a simpler way to just get php5 and it's dependencies onto a disk or portable hard drive, and install them or make a repository out of them...

---

### Post by bettermentflux on 2006-06-07
Maybe I'm oversimplifying the situation, but I only recently became aware of the [http://packages.ubuntu.com/dapper]("http://packages.ubuntu.com/dapper").

Search, download, burn and done.

Assuming that helps you as much as it helped me, perhaps the good people at Canonical could more prominently advertise the fact that the repos can be accessed through a standard browser.

---

