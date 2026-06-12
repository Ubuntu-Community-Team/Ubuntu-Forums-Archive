---
title: "Update a program from command line to specific version"
date: 2011-05-17
forum: General Help
---

### Post by lobosqe on 2011-05-17
Hello. I would like to know if I can update only one program to an specific version from the command line.

For exmaple I would like to update transmission to a version that is supported by my tracker... instead when I updated it got updated to the 2.30. Which is not even the latest! That one went out just now is rally fresh. But still an update wont update it to 2.31 (though it fixes a packaging problem in 2.30).

Lets say I would like transmission downgraded to version 2.22. How can I do that from command line? Bear in mind it is a headless ubuntu version with no gui (like a seedbox). So I just need to downgrade transmission-daemon and everything that depends on it.

It is my first post I hope I do it alright.

---

### Post by AlphaLexman on 2011-05-17
I did a quick ppa search and could **NOT** find 2.31, but only 2.30. You may have to compile from the source code if you need the absolute latest version.

Good Luck!

---

### Post by lobosqe on 2011-05-17
Thank you for your quick reply.

Another thing that could help would be to downgrade to version 2.22

How can I downgrade to version 2.22 from command line? (or any other previous version)

Thanks!

---

### Post by snowpine on 2011-05-17
Ta-da! First hit on Google: [http://www.transmissionbt.com/download/](http://www.transmissionbt.com/download/)

---

### Post by AlphaLexman on 2011-05-17
Here is a link: [http://www.ubuntugeek.com/transmission-2-22-released-and-ppa-installation-instructions-included.html](http://www.ubuntugeek.com/transmission-2-22-released-and-ppa-installation-instructions-included.html)

---

### Post by lobosqe on 2011-05-17
Thank you all for your help.

But if I follow that guide:

```

sudo add-apt-repository ppa:transmissionbt/ppa
sudo apt-get update
sudo apt-get upgrade

```It will install the latest version, transmission 2.30. I've just done it.

Instead what I need is to downgrade to version 2.22 (the one accepted by the tracker). Is there something like:

sudo apt-get install transmission2.22

Or something similar?

---

### Post by AlphaLexman on 2011-05-17
Try searching [http://packages.ubuntu.com]("http://packages.ubuntu.com/")
I couldn't find a direct link as the site searched for my version of ubuntu.

Good Luck!

---

### Post by lobosqe on 2011-05-17
Ok, finally I had to do it the wild way. Thank all of you for your suggestions and help. Here is what I did in case someone has the same issue:

1) Removed the previous version of transmission-daemon
```
sudo apt-get remove transmission-daemon
```

2) Downloaded the packages of version 2.22
[https://launchpad.net/~transmissionbt/+archive/ppa/+build/2273483]("https://launchpad.net/%7Etransmissionbt/+archive/ppa/+build/2273483")

```

wget https://launchpad.net/~transmissionbt/+archive/ppa/+build/2273483/+files/transmission-cli_2.22-0ubuntu1.09.10.1_i386.deb
wget https://launchpad.net/~transmissionbt/+archive/ppa/+build/2273483/+files/transmission-common_2.22-0ubuntu1.09.10.1_all.deb
wget https://launchpad.net/~transmissionbt/+archive/ppa/+build/2273483/+files/transmission-daemon_2.22-0ubuntu1.09.10.1_i386.deb

```

However I couldn't find them in:
[http://archive.ubuntu.com/ubuntu/pool/main/t/transmission/](http://archive.ubuntu.com/ubuntu/pool/main/t/transmission/)

Only up to version 2.13... maybe somone knows why and can explain?

3) Installing the packages, in the proper order of course
```

sudo dpkg -i transmission-common_2.22-0ubuntu1.09.10.1_all.deb
sudo dpkg -i transmission-cli_2.22-0ubuntu1.09.10.1_i386.deb
sudo dpkg -i transmission-daemon_2.22-0ubuntu1.09.10.1_i386.deb

```

4) Restart transmission-daemon
```
/etc/init.d/transmission-daemon restart
```

Hope someone else finds it useful.

---

