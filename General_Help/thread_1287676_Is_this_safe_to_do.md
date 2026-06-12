---
title: "Is this safe to do ?"
date: 2009-10-10
forum: General Help
---

### Post by M!SF!TS on 2009-10-10
I found a site that helps install the screen saver ElectricSheep I was wondering if these commands were safe to do...

Here it is:
-------------------------------------------
# If you don't have subversion installed:
sudo apt-get install subversion

-------------------------------------------
sudo apt-get install libavutil49
sudo apt-get install libavcodec-dev
sudo apt-get install libavformat-dev
wget [http://electricsheep.org/makesheep.sh](http://electricsheep.org/makesheep.sh)
chmod 755 makesheep.sh
./makesheep.sh

-------------------------------------------


It just seems like alot of crap to install just for 1 thing to work...

here is the website
[http://prawnuk.blogspot.com/2009/09/electric-sheep-on-ubuntu-904.html](http://prawnuk.blogspot.com/2009/09/electric-sheep-on-ubuntu-904.html)

---

### Post by CharlesA on 2009-10-10
I've used electric sheep before, it's safe.

EDIT: There is a deb package listed here: [http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51)

---

### Post by delcypher on 2009-10-10
Everything looks safe apart from the line
./makesheep.sh

If you're really not sure about the authenticity of your source you should check the contents of the makesheep.sh shell script before executing it.

---

