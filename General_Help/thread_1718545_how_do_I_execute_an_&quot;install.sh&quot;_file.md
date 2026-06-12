---
title: "how do I execute an &quot;install.sh&quot; file"
date: 2011-03-31
forum: General Help
---

### Post by Cotopaxi on 2011-03-31
Hi,

In terminal I am in the directory, where the file is:

How do I type in terminal the instruction to install this file?

Thanks!

---

### Post by Enigmapond on 2011-03-31
Just make sure it's able to execute and then just cd to the directory and type install.sh

---

### Post by Smart Viking on 2011-03-31
```
$ chmod +x install.sh
$ ./install.sh
```

---

### Post by Cotopaxi on 2011-03-31
Smart Viking:

The part:
> chmod +x install.sh

went fine, Thanks!

Then the command:
> ./install.sh

gives the result:

> ./install.sh: no input file specified

Thanks very much indeed to both of you!

---

### Post by Smart Viking on 2011-03-31
An install.sh file can be anything, paste the output of
```
cat install.sh
```

What are you trying to accomplish?

---

### Post by marin123 on 2011-03-31
i have a clickable version of this. :)

right-click, properties, permissions,
then check "Allow executing file as program"
close that window and double-click the file and select run or run in terminal.

btw, no input file specified could mean you should have passed a file as a parameter. what exactly should that script do?

---

### Post by Cotopaxi on 2011-03-31
Marin & Smart Viking
Thanks again, for your help!

The output of "cat install.sh" is kilometric in length, so I better don't paste it here.

What I want to accomplish:

I downloaded a program called "KnowIt". The link is:

[http://knowit.sourceforge.net/download.php]("http://knowit.sourceforge.net/download.php")

The debian package is a i386 package and I do not manage to install that with the "force architecture command".

So I downloaded the tarrbal and managed to unpack it.

Then, the only install file that I found was in the subdirectory "admin".
And this file is not executable.

If anybody knows, how I can install the i386.deb package with force-architecture, that would also help me a lot.

The reason, why I need all this is that I have been working with KnwoIt but, when I upgraded to 10.10, KnowIt was removed!

Again, thanks very much indeed for your help!

---

### Post by Sealbhach on 2011-03-31
I just downloaded it to see if I could install it. It's got dependency problems, did you try to sort them out?
```

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package knowit.
(Reading database ... 117426 files and directories currently installed.)
Unpacking knowit (from knowit_0.10-1_i386.deb) ...
dpkg: dependency problems prevent configuration of knowit:
 knowit depends on kdelibs4 (>= 4:3.3.0); however:
  Package kdelibs4 is not installed.
 knowit depends on libqt3c102-mt (>= 3:3.3.3); however:
  Package libqt3c102-mt is not installed.
 knowit depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing knowit (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 knowit
```It wants kdelibs4, libqt3c102-m and  libstdc++5.

EDIT: I tried installing those dependenices but no good.

.

---

### Post by Cotopaxi on 2011-03-31
Ok, again thanks to all of you for your help! :popcorn:

I just downloaded another application, that allowed me to import the knowit file:

> Kjots

a webpage about kjots:

[http://en.wikipedia.org/wiki/KJots]("http://en.wikipedia.org/wiki/KJots")

----------------------------------------

There is a very similar application called

> gjots2

The webpage is:

[http://bhepple.freeshell.org/gjots/index.shtml]("http://bhepple.freeshell.org/gjots/index.shtml")

Anyhow, they should be in the repositories.

Again, Thanks very much for everybody's help!

---

