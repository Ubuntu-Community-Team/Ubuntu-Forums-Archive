---
title: "General question about packages"
date: 2010-04-08
forum: General Help
---

### Post by jerimiahgentry on 2010-04-08
Greetings:

I figured I'd put my question at the top of my post because I usually bury it in the middle of a narrative:

* If I don't see a package I want in the main repositories, what is the next step? 

And now a little back story:

I am running Ubuntu Netbook Remix on a 900 eeepc, used primarily for nursing school work. I am considering using the application [Basket]("http://basket.kde.org"), and would like to use the new version, 1.8. While I am not a complete linux beginner (I used Slackware back in the day yo), I am rather slow with the whole process of compiling and searching for dependencies, etc. I am a busy student and so I need the installation "to just work."  

Thank you for whatever guidance you may offer.


Jerimiah

---

### Post by sisco311 on 2010-04-08
You can try the ppa repo to install 2.0 beta: [https://launchpad.net/~andreas-wenning/+archive/ppa](https://launchpad.net/~andreas-wenning/+archive/ppa)

or compile it:

download & extract the source 
```
mkdir ~/.src
cd ~/.src
wget http://basket.kde.org/downloads/basket-1.80.tar.bz2
tar xfvj basket-1.80.tar.bz2
```

install the build dependencies:
```
sudo apt-get build-dep basket
```

compile & install it:
```
cd basket-1.80
./install
```

---

### Post by nothingspecial on 2010-04-08
Any decent source package will contain a README and/or INSTALL file which will list the required dependencies.

You can search the repositories for them using 

```
apt-cache search -n whatever_you are_searching_for
```

the -n option will search only package names and not descriptions.

---

### Post by sisco311 on 2010-04-08
Oh, in general, if a package is not in the repositories, then:
[list]
[*]download the source from a _trusted_ location & compile it (most secure);
[*]find a ppa repository;
[*]find another third party repo; 
[*]find a deb file. 
[/list]

Take care when adding third party repositories and third party .deb.
See: [thread=1349801]Social engineering (trojan) via gnome-look.org[/thread] ;)

---

### Post by gadolinio on 2010-04-08
These sites have .deb packages ready to install. You might find the software you need there.
[http://linuxappfinder.com/](http://linuxappfinder.com/)
[http://www.getdeb.net/updates/ubuntu/9.04/](http://www.getdeb.net/updates/ubuntu/9.04/)

---

### Post by jerimiahgentry on 2010-04-09
Thanks everyone:

Cisco, this:

sudo apt-get build-dep basket

will only work if the version of basket I want is in the repository, correct? If I ran that command this rightr now I assume it would get all the dependencies for the old version, no?

---

### Post by sisco311 on 2010-04-09
> **jerimiahgentry said:**
> Thanks everyone:

Cisco, this:

sudo apt-get build-dep basket

will only work if the version of basket I want is in the repository, correct? If I ran that command this rightr now I assume it would get all the dependencies for the old version, no?

It will download the dependencies for the version of the _source_ package available from the repository. The version available in the karmic repository is a little outdated, so yes, it's possible that the command can't satisfy the dependencies.

I just realized that version 1.80 is 2.0 Beta 1 which is available from the ppa repository. So if you don't want to waste your time with building it from source, then install it from the ppa repo.

---

