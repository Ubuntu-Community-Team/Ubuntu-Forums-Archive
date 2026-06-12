---
title: "Natty problem, unable to download anything new"
date: 2011-06-09
forum: General Help
---

### Post by Greenwick on 2011-06-09
Every time the option to download the new version of Natty Narwhale comes up, I click on it.  The computer isn't able to manage it.  This didn't seem to affect anything at first, but now I'm not able to download anything from the software center, and other errors are popping up.

Anyone else having this problem?

I haven't seen the message asking if I want to update to the new version of Natty in awhile, so I can't remember what the error message said.  I'll copy/paste it here the next time that happens.

When I last tried to download something, this was the error that popped up:

> An unhandleable error occurred.

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.
For some other things that I've tried to install, I get this message:

> To install ______, these items must be removed:

Linux kernel headers for versio...
linux.headers-2.6.35-22genericI don't know where to go to remove that, and can't click on it to get the full message.


If you need more info, I will try to find it.  I'll also try to get the message for when I try to fix Natty.  Thanks!

---

### Post by Peter09 on 2011-06-09
in a terminal try
 
```
sudo apt-get update
```
 
and then
 
```
sudo apt-get upgrade
```
 
please paste any errors that you get here so that we can see them.

---

### Post by Greenwick on 2011-06-09
Thanks, I will try that.

---

