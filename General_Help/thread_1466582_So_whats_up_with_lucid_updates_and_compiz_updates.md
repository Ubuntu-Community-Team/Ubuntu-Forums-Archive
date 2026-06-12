---
title: "So whats up with lucid updates and compiz updates?"
date: 2010-04-30
forum: General Help
---

### Post by aviramof on 2010-04-30
During the last few days there were barely any updates i'm not even sure that the version i now have it qualified to be called final version.

and i'm also waiting for compiz updates to be build is there any news about that?
[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

---

### Post by POI09 on 2010-04-30
> **aviramof said:**
> During the last few days there were barely any updates i'm not even sure that the version i now have it qualified to be called final version.

and i'm also waiting for compiz updates to be build is there any news about that?
[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)


I'd like to know about the compiz situation also.it says it's installed but I can't find it anywhere.

---

### Post by sdowney717 on 2010-04-30
it is under system-preferences menu

perhaps the gui manager it is not installed

---

### Post by Uncle Spellbinder on 2010-04-30
To find out if you're running Lucid final, in terminal do the following:

```
sudo lsb_release -a
```

You should see this:

```
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid
```

---

### Post by zuerston on 2010-04-30
> **POI09 said:**
> I'd like to know about the compiz situation also.it says it's installed but I can't find it anywhere.

Try "applications" ==> "Ubuntu Software Center" type "compiz" in search and install the "compiz fusion icon" and "CompizConfig settings Manager"
after installing.....
find the "compiz Fusion icon" in Applications under system tools
find the "CompizConfig settings Manager" in System Preferences.
you can right click both and Add them to your desktop for conveinence.

After clicking the Compiz fuzion icon ,,,  in your top desktop bar see the blue icon,"right click it" see the choices ect ect etc etc blah blah blah

---

### Post by zuerston on 2010-04-30
> **Uncle Spellbinder said:**
> To find out if you're running Lucid final, in terminal do the following:

```
sudo lsb_release -a
```You should see this:

```
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
```

I ran that just to look at it ,what does No LSB modules ect mean? :P just wondering 
------
me@me's-desktop:~$ sudo lsb_release -a
[sudo] password for me: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
me@me's-desktop:~$ 
--------

---

### Post by zuerston on 2010-04-30
And further more............................. If you cant run Google Earth in Compiz,,,** run that little Compiz fuzion  icon again** ,and choose "select window manager" and use "Meta city" instead ,while Google Earthing, and back after done checking out the Earth.
ohh and by the way,, set Google Earth video to "safe mode" in its settings,works for me,using old Nvidia card.

---

### Post by Uncle Spellbinder on 2010-04-30
> **zuerston said:**
> I ran that just to look at it ,what does No LSB modules ect mean? :P just wondering 
------
me@me's-desktop:~$ sudo lsb_release -a
[sudo] password for me: 
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
me@me's-desktop:~$ 
--------

I actually get that as well (on 3 separate installs). Always have. Just didn't include it in my post above. I'm not sure what that means. :-k

---

### Post by aviramof on 2010-04-30
Well it look like i have final version maybe but there were so few updates that it's almost impossible:
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid
```as for compiz there are updates in the compiz ppa but as you can see not all are successfully build and it's been a while since they they been uploaded so what's up with that?

as for No LSB modules are available i just noticed that the package lsb is not installed at all.

---

### Post by csaket on 2010-04-30
Some info about LSB among different nixes [http://www.unixtutorial.org/2008/03/find-out-linux-version-using-lsb/](http://www.unixtutorial.org/2008/03/find-out-linux-version-using-lsb/)

---

### Post by aviramof on 2010-04-30
here are my results after installing lsb package:
```

sudo lsb_release -a
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04 LTS
Release:    10.04
Codename:    lucid

```

just something i thought you should be aware of.

---

### Post by POI09 on 2010-04-30
Fixed compiz

---

### Post by aviramof on 2010-05-01
I don't see it here:
[https://launchpad.net/~compiz/+archive/ppa](https://launchpad.net/~compiz/+archive/ppa)

---

