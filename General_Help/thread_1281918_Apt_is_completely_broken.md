---
title: "Apt is completely broken"
date: 2009-10-03
forum: General Help
---

### Post by kerryhall on 2009-10-03
No hope of recovery, AFAIK

examples:
```

sudo apt-get install libsdl-image1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl-image1.2-dev: Depends: libtiff4-dev but it is not going to be installed
E: Broken packages

```

Ok, so lets try to install that dep package.

```

sudo apt-get install libtiff4-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libtiff4-dev: Depends: libtiff4 (= 3.8.2-11) but 3.8.2-11ubuntu0.9.04.3 is to be installed
E: Broken packages

```

Ok, so let try installing libtiff4

```

sudo apt-get install libtiff4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtiff4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

WTF?

Already tried apt-get install -f or whatever with the -f

Cheers!

---

### Post by slakkie on 2009-10-03
Could you show the output of apt-cache policy libtiff4?

Never mind, I've changed my sources.list to jaunty, what you should do is this:

```

sudo aptitude install libtiff4=3.8.2-11

```

This will install libtiff4 at the version which is needed for installing libtiff4-dev.

I'm running karmic, so this will be a good example of how it will downgrade a particular package:

```

sudo aptitude -s install libtiff4=3.8.2-11
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  libtiff4-dev
The following packages will be DOWNGRADED:
  libtiff4
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 3 not upgraded.
Need to get 126kB of archives. After unpacking 12.3kB will be freed.
The following packages have unmet dependencies:
  libtiff4-dev: Depends: libtiff4 (= 3.8.2-13) but 3.8.2-11 is to be installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
libtiff4-dev [3.8.2-13 (now) -> 3.8.2-11 (jaunty)]
libtiffxx0c2 [3.8.2-13 (now) -> 3.8.2-11 (jaunty)]

Score is -10

Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libtiff4 libtiff4-dev libtiffxx0c2
0 packages upgraded, 0 newly installed, 3 downgraded, 0 to remove and 3 not upgraded.
Need to get 365kB of archives. After unpacking 28.7kB will be freed.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

Or try the following, for me it works in theory

```

aptitude install libtiff4-dev=3.8.2-11ubuntu0.9.04.3

[snip]
Downgrade the following packages:
libtiff4 [3.8.2-13 (now) -> 3.8.2-11ubuntu0.9.04.3 (jaunty-updates)]
libtiffxx0c2 [3.8.2-13 (now) -> 3.8.2-11ubuntu0.9.04.3 (jaunty-updates)]

```

Best of luck

---

### Post by kerryhall on 2009-10-05
That seems to have done the trick! I was at my wit's end. Thank you! :)

---

