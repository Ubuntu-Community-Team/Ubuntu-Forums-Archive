---
title: "How to install a bin file??"
date: 2010-04-17
forum: General Help
---

### Post by chris.jericho on 2010-04-17
I just downloaded Google earth and am trying to use... it can't understand/// how to install it since its a bin file... 

how do I install a bin file...?????  I am using Ubuntu 10.04 lucid beta 2

---

### Post by darolu on 2010-04-17
Open a terminal and run "./<yourbinfile>.bin":
```
$ cd /path/to/your/bin

$ ./GoogleEarthLinux.bin
```

---

### Post by 3rdalbum on 2010-04-17
> **chris.jericho said:**
> I just downloaded Google earth and am trying to use... it can't understand/// how to install it since its a bin file... 

how do I install a bin file...?????  I am using Ubuntu 10.04 lucid beta 2

Google Earth is already in the Medibuntu repository. You should use repositories instead of just downloading programs from websites, for a number of reasons: It's easier to install, it allows you to keep on top of updates, it ensures that the program isn't maliciously modified in transit, and it makes it easy to remove when you're finished with it.

A "bin file" is just a program that can be run on Linux. First you need to make it executable, then you need to run it (as root - so it can install into a system-wide location).

```
sudo chmod a+x <drag the file to the terminal>
sudo <drag the file to the terminal>
```

The installer will run.

But install Google Earth via the repository. ([www.medibuntu.org](www.medibuntu.org))

---

### Post by chris.jericho on 2010-04-17
okay...  so you mean to say that first I type in the first line i.e      sudo chmod a+x
and then drag the file in the terminal..

then later type sudo again and drag that bin file in the terminal.... is that right??

but then how do I install Google earth via the repository........

sorry I am new to linux and not much familiar with it but trying........  please reply :)

---

### Post by chris.jericho on 2010-04-17
Okay thanks for the answer mate....... I went to this page and downloaded the AMD64 version of google earth and it works perfect.... Thanks for the help... :) :)


[http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html)

---

