---
title: "debootstrap and schroot"
date: 2010-11-18
forum: General Help
---

### Post by c2tarun on 2010-11-18
can anyone please tell me the difference between debootstrap and schroot.

---

### Post by sisco311 on 2010-11-18
[debootstrap]("http://wiki.debian.org/Debootstrap") is a tool which will install a Debian base system into a subdirectory of another, already installed system.

schroot allows the user to run a command or a login shell in a [chroot]("http://en.wikipedia.org/wiki/Chroot") environment.

[http://manpages.ubuntu.com/manpages/maverick/en/man8/debootstrap.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/debootstrap.8.html)
[http://manpages.ubuntu.com/manpages/maverick/en/man1/schroot.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/schroot.1.html)
[http://manpages.ubuntu.com/manpages/maverick/en/man8/chroot.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/chroot.8.html)

---

### Post by c2tarun on 2010-11-18
i googled on debootstrap and found that it can be used to install a fresh copy of debian GNU/Linux into a directory. it is very good for experimentation.

i have a system currently ubuntu lucid installed in it. if i want to perform some experimentation on maverick do i have to install maverick in any particular directory???

how can i roll back( means uninstall maverick from that folder)??
one more thing... can this debootstrap is used only to install whole OS, what if i want to perform my experimentation on ubuntu Lucid only, cant we just install an application in a particular folder, copy the files needed by it into that folder. lock on that folder and perform our experiments.

---

### Post by sisco311 on 2010-11-18
> **c2tarun said:**
> 
i have a system currently ubuntu lucid installed in it. if i want to perform some experimentation on maverick do i have to install maverick in any particular directory???


You can use any empty directory on a native Linux filesystem (i.e. ext3). If you are planning to upgrade your chroot environment to a fully functional bootable Ubuntu installation then use a separate partition.

> **c2tarun said:**
> 
how can i roll back( means uninstall maverick from that folder)??


Simply delete the directory.

> **c2tarun said:**
> 
one more thing... can this debootstrap is used only to install whole OS, what if i want to perform my experimentation on ubuntu Lucid only, cant we just install an application in a particular folder, copy the files needed by it into that folder. lock on that folder and perform our experiments.

By default, debootstrap installs the minimal list of packages you need to be able to chroot to. Once you chrooted into the new environment you can install any other packages.

---

### Post by c2tarun on 2010-11-18
> **sisco311 said:**
> You can use any empty directory on a native Linux filesystem (i.e. ext3). If you are planning to upgrade your chroot environment to a fully functional bootable Ubuntu installation then use a separate partition.



i read the wiki page on debootstrap setup. they didn't tell me how to boot to the target installation.
i established the chroot environment of hardy in my /var/chroot/hardy as per the instructions on the wiki page.
can you please tell me how can i boot into that chroot environment???

---

### Post by c2tarun on 2010-11-19
i installed xnest and opened emacs into it by my chroot environment of hardy.
i want gnome to be installed in hardy.. how can i do that???

---

### Post by sisco311 on 2010-11-19
> **c2tarun said:**
> i installed xnest and opened emacs into it by my chroot environment of hardy.
i want gnome to be installed in hardy.. how can i do that???

First you need to add some repositories. Edit the file /etc/apt/sources.list to look like this:
```
deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted universe multiverse
```

I would recommend you to install ubuntu-minimal and ubuntu-standard:
```

apt-get update
apt-get install ubuntu-minimal ubuntu-standard
```

Create a new user with sudo privileges. Log in as the new user. Install the package gnome-core or gnome or ubuntu-desktop.

After that you can start any application in the nested X server even a gnome-session, assuming that Xnest is using display :2.0:
```
DISPLAY=:2.0
gnome-session
```

---

### Post by c2tarun on 2010-11-19
> **sisco311 said:**
> First you need to add some repositories. Edit the file /etc/apt/sources.list to look like this:

actually i copied the source list from my ubuntu lucid and updated it for hardy. do i still need to make any changes???

---

### Post by sisco311 on 2010-11-19
> **c2tarun said:**
> do i still need to make any changes???

Nope, that should work.

---

### Post by c2tarun on 2010-11-19
just curious to know, what are we exactly installing with ubuntu-minimal and ubuntu-standard??

and also sorry to ask this, but i created a new account. can u please tell me how to log into that account??
i just wrote there login <username> and it asked for the password, i entered that then everything root@ubuntu-laptop:/# changed to $ with nothing written there...

ok then i tried to install using sudo and got the error <username> not in sudoers list. i created a new account using admin added the line
```

%admin ALL=(ALL)  ALL

```
to the /etc/sudoers file.
then i tried again and now getting 

```

sudo: unable to resolve host ubuntu-laptop
sudo: /etc/sudoers is mode 0640, should be 0440
sudo: no valid sudoers sources found, quitting

```

---

### Post by c2tarun on 2010-11-19
sorry i forgot to change sudoer file priviledges. i changed them back and it worked.
but i m still getting the error
cannot resolve ubuntu-laptop

---

### Post by c2tarun on 2010-11-20
hey i installed everything as told.
plus i installed ubuntu-desktop.
i got this error at the end

Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


now whenever i m installing any package i m getting this error.

what should i do..

---

