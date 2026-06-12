---
title: "Cannot Update UBUNTU 12.04"
date: 2012-05-11
forum: General Help
---

### Post by mukulshukla1992 on 2012-05-11
When I run the update manager, and check for updates I get:
Failed to download repository information
Check your internet Connection
 W:Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

                 [B]
[/B]

---

### Post by MG&amp;TL on 2012-05-11
That won't do anything to official updates...but you've added a PPA that either doesn't exist, or doesn't have packages for your version of *buntu.  EDIT: that package (pulse-audio equaliser?) only has packages for up to Lucid. (10.04).

If it bothers you, can we see the output of:

```
ls /etc/apt/source.list.d
```

from a terminal, then we can remove it. Thanks!

---

### Post by Enigmapond on 2012-05-11
That PPA is for the equalizer not available in 12.04...yet. Just remove it from your sources.

---

### Post by mukulshukla1992 on 2012-05-12
I have these two files in /etc/apt/source.list.d/

psyke83-ppa-precise.list
psyke83-ppa-precise.list.save

Both the files have these lines

deb [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) precise main

which one to remove?

---

### Post by zombifier25 on 2012-05-12
> **mukulshukla1992 said:**
> I have these two files in /etc/apt/source.list.d/

psyke83-ppa-precise.list
psyke83-ppa-precise.list.save

Both the files have these lines

deb [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu) precise main

which one to remove?

both.

---

### Post by mukulshukla1992 on 2012-05-12
> **zombifier25 said:**
> both.

Sorry to  bother you again.. but both the files or both the lines.?

Do I delete both the files.?

Or Do i delete both the lines and keep both files empty..?

or just delete those lines from one file.?

---

### Post by mukulshukla1992 on 2012-05-12
Thank you, I deleted both the lines from both files! :)

---

### Post by MG&amp;TL on 2012-05-12
You can delete both the files safely now, as they serve no purpose. But they're not harming anything sitting there. :)

---

### Post by hunteke on 2012-07-13
> **mukulshukla1992 said:**
> Sorry to  bother you again.. but both the files or both the lines.?

Given that it's two months later, you've probably resolved this problem one way or the other, but let me explain for any Googlers who may have this problem.

The short answer is: the lines.

Longer answer: you need to understand how the **repository system** works.  Briefly, to install a package on your system, you have two options:

[LIST=1]
[*]Exactly analogous to how one might install it in Windows or OS X, you acquire (download, USB, etc.) a **.deb** file, and double click it.
[*]You add a repository that contains the package you want, and then install the package /through the Ubuntu Software Center/.
[/LIST]

The second option is generally The Better Option (TM) because then the Ubuntu Software Center will automatically discover and install any updates.  (As opposed to the program informing you that you need to download an update, or you have having a terribly out of date version in 2 months time.)

In your case, the issue is likely that you recently updated to Ubuntu 12.04, but the repository to which you'd linked in a previous version of Ubuntu has not been updated to handle Precise.  Thus, your error.

To add a repository, you need only one thing: to add its web-accessible URL (e.g. 'http://...') into a file in [FONT="Courier New"]/etc/apt/[/FONT].  Whether you do this by hand (through the command line, gedit, etc.) or through the graphical interface that is the Ubuntu Software Center is up to you, but each repository added amounts to a single line in one of the files in [FONT="Courier New"]/etc/apt/[/FONT].

So, to fix your error, you want to remove the offending repositories, and that means removing any references (lines) to them in [FONT="Courier New"]/etc/apt/[/FONT].

---

