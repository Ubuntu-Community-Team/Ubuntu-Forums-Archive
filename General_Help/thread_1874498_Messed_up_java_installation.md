---
title: "Messed up java installation"
date: 2011-11-03
forum: General Help
---

### Post by therog726 on 2011-11-03
Hi,

I've done some (very basic) java programming in the past with no problems (the most recent being about 5-6 months ago) and since then I have upgraded to 11.10 and openjdk-7.
I just went to run a java program today and got an error which looked something like this with a whole lot of other stuff under it:
```
Exception in thread "main" java.lang.UnsupportedClassVersionError: a 
(Unsupported major.minor version 50.0)
```

After some googling I discovered that this apparently meant that I hadn't set the PATH properly and after trying to do that in my .bashrc file and failing miserably, I tried to reinstall openjdk. I uninstalled it and reinstalled it but in the process java seems to have changed?

Now when I run "java -version" it gives me:
```
sam@ubuntu:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.6.1

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

I don't know what's going on here, but can someone please help me get openjdk-6 or 7 working properly again??
I can't replicate the original error now since it's all messed up.

Not sure if this is useful but:
```
sam@ubuntu:~$ which java
/usr/bin/java

```

Thanks in advance :)

---

### Post by Azdour on 2011-11-03
Hi,

Assuming you have openjdk installed you should be able to pick which Java to use by opening a terminal and using:

```
sudo update-alternatives --config java
```

---

### Post by therog726 on 2011-11-03
> **Azdour said:**
> Hi,

Assuming you have openjdk installed you should be able to pick which Java to use by opening a terminal and using:

```
sudo update-alternatives --config java
```

Thanks for your reply!

I definitely have openjdk installed and I've tried that but all it comes up with is this:

```
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path              Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gij-4.6   1046      auto mode
  1            /usr/bin/gij-4.5   1045      manual mode
  2            /usr/bin/gij-4.6   1046      manual mode

Press enter to keep the current choice[*], or type selection number: 
```

I've tried all 3 of these options but it doesn't make a difference.

---

### Post by Jaybyrrd on 2011-11-03
I do not believe that gij is the OpenJDK7 directory, so I would try a full reinstall of OpenJDK to see if that can fix anything (since I don't know how else to approach it).

sudo apt-get purge openjdk-7-jre
sudo apt-get install openjdk-7-jre

Then

sudo update-alternatives java --config

See if it lists properly.

---

### Post by therog726 on 2011-11-04
> **Jaybyrrd said:**
> I do not believe that gij is the OpenJDK7 directory, so I would try a full reinstall of OpenJDK to see if that can fix anything (since I don't know how else to approach it).

sudo apt-get purge openjdk-7-jre
sudo apt-get install openjdk-7-jre

Then

sudo update-alternatives java --config

See if it lists properly.

All sorted! Thank you very much for that! I did everything there before except for the purge.

That fixed the problem. Thanks again :KS

---

### Post by sudheer penubarthi on 2011-11-09
Excellent worked like a charm.

---

