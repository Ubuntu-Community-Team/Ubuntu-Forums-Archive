---
title: "installing libmozjs-dev will remove ... about everything?"
date: 2009-11-20
forum: General Help
---

### Post by sanderj on 2009-11-20
I want to install the development library of SpiderMonkey, which seems to be libmozjs-dev. However, when I try install that, apt-get warns it will remove firefox, ubuntu-desktop and a lot of other apps.

Am I doing something wrong?


```
sander@quirinius:~$ sudo apt-get install libmozjs-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  tcl8.3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmozjs0d libnspr4-dev
The following packages will be REMOVED:
  couchdb couchdb-bin desktopcouch evolution-couchdb evolution-documentation-en firefox firefox-3.5 firefox-3.5-branding
  firefox-3.5-gnome-support firefox-gnome-support gnome-user-guide python-desktopcouch python-desktopcouch-records ubufox
  ubuntu-desktop ubuntu-docs xulrunner-1.9.1 xulrunner-1.9.1-gnome-support yelp
The following NEW packages will be installed:
  libmozjs-dev libmozjs0d libnspr4-dev
0 upgraded, 3 newly installed, 19 to remove and 0 not upgraded.
Need to get 844kB of archives.
After this operation, 295MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
sander@quirinius:~$ 

```

---

### Post by Giblet5 on 2009-11-20
libmozjs-dev is a very jealous package. :)

I'm guessing that the package's dependencies are hosed.

You should file a bug on it. Then you have an option: either wait for the package maintainer to fix it, or build the kit from source.

---

### Post by sanderj on 2009-11-20
> **Giblet5 said:**
> libmozjs-dev is a very jealous package. :)

... more a cuckoo chick ;-) , see [http://en.wikipedia.org/wiki/Common_Cuckoo#Breeding](http://en.wikipedia.org/wiki/Common_Cuckoo#Breeding)


> **Giblet5 said:**
> 
I'm guessing that the package's dependencies are hosed.

You should file a bug on it. Then you have an option: either wait for the package maintainer to fix it, or build the kit from source.


And apt-get has no option to only install new packages, and NOT remove others? I checked the man page quickly, but couldn't find such an option...

---

### Post by Giblet5 on 2009-11-20
There are ways to force anything, but I wouldn't.

I'd build it from the source.

---

### Post by Giblet5 on 2009-11-20
Found it!

```
$ aptitude why-not libmozjs-dev
i   xulrunner-1.9.1 Conflicts libmozjs-dev
```

THAT is why it wants to remove all of those packages.

(chase the packages backwards and you get the entire list of yours)

Mark it SOLVED.

---

### Post by sanderj on 2009-11-20
Ai, I just filed a bug report: [https://bugs.launchpad.net/ubuntu/+source/xulrunner/+bug/486079](https://bugs.launchpad.net/ubuntu/+source/xulrunner/+bug/486079)

I will follow your last advice, and then remove the bug report.

---

### Post by sanderj on 2009-11-20
> **Giblet5 said:**
> Found it!

```
$ aptitude why-not libmozjs-dev
i   xulrunner-1.9.1 Conflicts libmozjs-dev
```

THAT is why it wants to remove all of those packages.




A bit more explanation please: what is the cause of the conflict? is a newer or older xulrunner needed? Of no xulrunner at all? 


> **Giblet5 said:**
> 

(chase the packages backwards and you get the entire list of yours)

Mark it SOLVED.

What does "chasing backward" mean? I tried something (below), but that's not what you mean?

Thanks.

```
sander@quirinius:~$ aptitude why-not libmozjs-dev
i   xulrunner-1.9.1 Conflicts libmozjs-dev
sander@quirinius:~$ aptitude why-not xulrunner-1.9.1
Unable to find a reason to remove xulrunner-1.9.1.
sander@quirinius:~$ 

```

---

### Post by Giblet5 on 2009-11-23
xulrunner-1.9.1 is a dependency of firefox-3.5

Install the libmozjs and you have to ubinstall a lot of stuff - because libmozjs is not compatible with xulrunner-1.9.1.

---

### Post by dave-o-dave on 2010-08-13
I am sorry, but I am also confused by what I am supposed to do about this.
I want to install something which requires libmozjs and I cant add the library because of this bug. 
How can I get round this problem and still use the software I want to - or is it not that easy?
Sorry if that is stupid.

---

