---
title: "Install program from another distribution"
date: 2011-06-21
forum: General Help
---

### Post by alsfi on 2011-06-21
My question :  Is it possible to install programs from the distribution (2.8 altemate for example) to another distro (Ubuntu 10.04)
 With an indication of the way, if possible

---

### Post by FormatSeize on 2011-06-21
Grab the package (and it's dependencies if you suspect some of them may not be satisfied). 
 
For a tar (tar.gz, tar.bzip2), see the man page for tar and then:
```

tar [options] /path/to/tarfile
cd /path/to/extracted/directory/
./configure
make
sudo make install
```
If you didn't get all the depencies, then grab the ones that make is asking for, and install them using the directions above, then try to install the program that needed the dependencies again.
 
If you find something that is not a tar, but is still a package that you want (say, .rpm or .slp), then it is time to get Alien, which will change it to the .deb package that you need.
```

sudo apt-get --install alien
alien --to-deb /path/to/package
```
Then you just double click on the icon for the newly generated package, and Synaptic will open up and install it for you.

---

### Post by jerrrys on 2011-06-21
ubuntu is built on other distros (like fedora for one), so yes you can.  what package are you looking at?

---

