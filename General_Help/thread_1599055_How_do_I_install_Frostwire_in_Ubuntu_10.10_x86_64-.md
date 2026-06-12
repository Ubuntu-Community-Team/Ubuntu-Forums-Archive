---
title: "How do I install Frostwire in Ubuntu 10.10 x86 64-bit"
date: 2010-10-17
forum: General Help
---

### Post by cisforcojo on 2010-10-17
I know I've had this working in 64-bit Ubuntu before but now when I try to install it, I get an error saying that I have the wrong architecture (which is true). 

Has anyone gotten Frostwire to install?

---

### Post by Frogs Hair on 2010-10-17
Never mind

---

### Post by sikander3786 on 2010-10-17
> I get an error saying that I have the wrong architecture (**which is true**). 

If you know that, why are you asking?

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

### Post by DougieFresh4U on 2010-10-17
> **cisforcojo said:**
> I know I've had this working in 64-bit Ubuntu before but now when I try to install it, I get an error saying that I have the wrong architecture (which is true). 

Has anyone gotten Frostwire to install?

Ok, so how did you get Frostwire installed as I am having the same issue?

---

### Post by marl30 on 2010-10-17
> **DougieFresh4U said:**
> Ok, so how did you get Frostwire installed as I am having the same issue?

I want to know too, as it use to install easily. Now all of a sudden it appears that they no longer have a deb package for 64bit.

---

### Post by oberonking on 2010-10-18
[Getdeb.net]("http://getdeb.net/") is the better option..... but, it's down right now... 

Or... 

```
$ sudo apt-get install default-jre default-jre-headless 
$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb
```

I' installed it following this codes and install ok.

---

### Post by RiffRaff06078 on 2010-10-19
> **oberonking said:**
> [Getdeb.net]("http://getdeb.net/") is the better option..... but, it's down right now... 

Or... 

```
$ sudo apt-get install default-jre default-jre-headless 
$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb
```

I' installed it following this codes and install ok.

This worked flawlessly for me as well.  Thanks!

---

### Post by pr0ph37 on 2010-10-19
> **oberonking said:**
> [Getdeb.net]("http://getdeb.net/") is the better option..... but, it's down right now... 

Or... 

```
$ sudo apt-get install default-jre default-jre-headless 
$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb
```I' installed it following this codes and install ok.


i am having the same problem.... tried both codes, first one installed, but the second one i am getting this code...

pr0ph37@mini-ho:~$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb
dpkg: error processing frostwire-4.21.1.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.21.1.i586.deb

---

### Post by oberonking on 2010-10-19
> **pr0ph37 said:**
> i am having the same problem.... tried both codes, first one installed, but the second one i am getting this code...

pr0ph37@mini-ho:~$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb
dpkg: error processing frostwire-4.21.1.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.21.1.i586.deb

You must be on the folder where download frostwire-4.21.1.i586.deb...
So, first do:
cd .../file path/...
And now try it again.

---

### Post by ivarn on 2010-10-19
I prefer limwire. it includes more p2p networks to search from.
[http://thepiratebay.org/search/limewire%20pro%20.deb/0/99/0](http://thepiratebay.org/search/limewire%20pro%20.deb/0/99/0)
This is the pro version (faster search and no ads).

---

### Post by Soul-Sing on 2010-10-19
why not use the noarch tar package of frostwire? untar/pack it and run it.
=runFrostwire.sh=

---

### Post by Coozy12 on 2010-10-20
dpkg: error processing frostwire-4.21.1.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 frostwire-4.21.1.i586.deb


I get this message everytime how do I fix it........and please explain this cause i am very new

---

### Post by oberonking on 2010-10-20
> **oberonking said:**
> You must be on the folder where download frostwire-4.21.1.i586.deb...
So, first do:
cd .../file path/...
And now try it again.

you tried this???

---

### Post by cisforcojo on 2010-10-22
Thank you!! I didn't know about the noarch package and --force-architecture is exactly what I needed to know.

For everyone that is new and still having trouble, this is most likely the command that you're missing (but again as they have said, this will depend on where you downloaded the file):

```

$ sudo apt-get install default-jre default-jre-headless 
**$ cd ~/Downloads**
$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb

```

---

### Post by DougieFresh4U on 2010-10-26
> **cisforcojo said:**
> Thank you!! I didn't know about the noarch package and --force-architecture is exactly what I needed to know.

For everyone that is new and still having trouble, this is most likely the command that you're missing (but again as they have said, this will depend on where you downloaded the file):

```

$ sudo apt-get install default-jre default-jre-headless 
**$ cd ~/Downloads**
$ sudo dpkg -i --force-architecture frostwire-4.21.1.i586.deb

```

Thank you:)

---

