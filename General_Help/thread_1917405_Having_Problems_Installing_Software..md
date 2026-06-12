---
title: "Having Problems Installing Software."
date: 2012-01-30
forum: General Help
---

### Post by Xourii on 2012-01-30
Whenever I'm trying to use sudo commands to install something, I get this in the terminal..

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Also, when trying to install WINE, PlayOnLinux, and Pidgin, I kept getting 

"Waiting for apt-get to exit."

What's going on? I'm a newbie and I don't know what to do.

---

### Post by Gremlinzzz on 2012-01-30
[http://nixtricks.wordpress.com/2009/10/02/ubuntu-unlock-varlibdpkglock-when-youre-locked-out/](http://nixtricks.wordpress.com/2009/10/02/ubuntu-unlock-varlibdpkglock-when-youre-locked-out/)
:popcorn:

---

### Post by Xourii on 2012-01-30
> **Gremlinzzz said:**
> [http://nixtricks.wordpress.com/2009/10/02/ubuntu-unlock-varlibdpkglock-when-youre-locked-out/](http://nixtricks.wordpress.com/2009/10/02/ubuntu-unlock-varlibdpkglock-when-youre-locked-out/)
:popcorn:

That helps, but how do I stop the other package from installing? I only got this error after doing a fresh install of 11.10, by the way.

EDIT: I followed the instructions and this is what I get: 

Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

---

### Post by Xourii on 2012-01-30
I'm also getting this when trying to install anything in the Ubuntu Software Center.

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

---

### Post by Gremlinzzz on 2012-01-30
Try 
sudo apt-get update
sudo apt-get -f install
:popcorn:

[http://ubuntuforums.org/archive/index.php/t-1599278.html](http://ubuntuforums.org/archive/index.php/t-1599278.html)

---

### Post by Gremlinzzz on 2012-01-30
> **Xourii said:**
> Whenever I'm trying to use sudo commands to install something, I get this in the terminal..

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Also, when trying to install WINE, PlayOnLinux, and Pidgin, I kept getting 

"Waiting for apt-get to exit."

What's going on? I'm a newbie and I don't know what to do.

If its a new installtion i would reinstall the OS:popcorn:

---

### Post by philinux on 2012-01-30
> **Gremlinzzz said:**
> If its a new installtion i would reinstall the OS:popcorn:

That's a very last resort. This **should** be easily fixable. 

Waiting for OP to post back.

---

### Post by Gremlinzzz on 2012-01-30
Tip:popcorn:
using Google to look for solutions
most of the time someone else has had the problem and solved it
its faster than forums:popcorn:
Like i thought the first link i sent you to would solve your problem
so i went to sleep:popcorn:

---

### Post by Gremlinzzz on 2012-01-30
> **philinux said:**
> That's a very last resort. This _should_ be easily fixable. 

Waiting for OP to post back.

your right:popcorn:

---

### Post by raja.genupula on 2012-01-30
Hi philinux , small problem . that link was not there . just should underlined .

Hi OP; this is i usually follow when i got things like that 
simply removing that lock .

```
sudo rm /var/lib/dpkg/lock
sudo apt-get update 

```

try it , hope it will work for you too . 
All the best.

---

### Post by philinux on 2012-01-30
> **raja.genupula said:**
> Hi philinux , small problem . that link was not there . just should underlined .



Fixed that :P. I meant it to be bold.

---

### Post by raja.genupula on 2012-01-30
> **philinux said:**
> Fixed that :P. I meant it to be bold.

yup  :D, now looking for op response .

---

