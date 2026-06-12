---
title: "Unable to compile bbcp"
date: 2011-01-12
forum: General Help
---

### Post by uchighlander on 2011-01-12
I am trying to build bbcp from source on Ubuntu 10.04.1 LTS available here:
 
[http://www.slac.stanford.edu/~abh/bbcp/](http://www.slac.stanford.edu/~abh/bbcp/)
 
Source:
 
[http://www.slac.stanford.edu/~abh/bbcp/bbcp.tgz](http://www.slac.stanford.edu/~abh/bbcp/bbcp.tgz)
 
I keep running error when running make:
 
make[2]: *** No rule to make target `makeLinuxunknown'.  Stop.
 
Any ideas how to fix this? If not, can somebody port this app to Ubuntu?

---

### Post by Rubi1200 on 2011-01-13
Hi and welcome to the forums :)

Did you install the build-essential package?

```
sudo apt-get build-essential
```

You may also need other packages; see here for more:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by uchighlander on 2011-01-13
build-essential was already installed

---

### Post by uchighlander on 2011-01-14
Still having problems getting this installed. I've emailed the author of the app but if anybody else can shed some light on the issue I would appreciate it.

---

### Post by dltwyman67 on 2012-06-07
I know this is old but here is a possible answer that worked for me 12.04 LTS server:

resolve dependencies: 

sudo apt-get install curl libcurl4-openssl-dev libexpat1-dev gettext zlib1g-dev git-core libboost1.40-dev

checkout git clone [http://www.slac.stanford.edu/~abh/bbcp2/bbcp.git](http://www.slac.stanford.edu/~abh/bbcp2/bbcp.git)

cd bbcp/src

under the src directory , edit Makefile 

find "Linux" around line 184. change the line  @make makeLinux`/bin/uname -i` to  @make makeLinux`/bin/uname -m`

sudo make all
sudo make Darwin

this creted a binary under bbcp/bin/amd64_linux26

---

### Post by Jt00 on 2012-06-07
Not sure how much this helps, but the compiling from source how-to it says to be sure "checkinstall" is installed with build-essential. You may want to reinstall these if you're still stuck.

---

### Post by TechZilla on 2012-08-01
> **Jt00 said:**
> Not sure how much this helps, but the compiling from source how-to it says to be sure "checkinstall" is installed with build-essential. You may want to reinstall these if you're still stuck.

The purpose of checkinstall is to manage your manually compile applications, as you would a regular package.  It basically makes binary deb packages, from the make installation procedure.  It's not a dependency, and will not assist in this OPs problem.


As for the OP, I compiled the source without any problem.
here is my commands, not sure if you need them.
```

wget http://www.slac.stanford.edu/~abh/bbcp/bbcp.tgz
tar -xzf bbcp.tgz
cd bbcp/src
make
sudo cp bin/amd64_linux/bbcp /usr/local/bin

```

---

