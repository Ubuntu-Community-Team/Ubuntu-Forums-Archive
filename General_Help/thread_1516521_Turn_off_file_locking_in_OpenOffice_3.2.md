---
title: "Turn off file locking in OpenOffice 3.2"
date: 2010-06-23
forum: General Help
---

### Post by herteljt on 2010-06-23
Hi all,

If you are up for a challenge read on, otherwise I suggest skipping to the next post :) 

I am wondering if anyone has figured out how to turn off the file locking in openoffice 3.2. I have been searching the net for solutions, trying out the fixes, and as of right now I have not been able to find a way to stop the creation of lock files.

I have tried editing both /usr/bin/soffice and /usr/lib/openoffice/program/soffice as described in the links (below), but this has not helped.

Here are the relevant links I have found

[http://ubuntuforums.org/showthread.php?t=1171339](http://ubuntuforums.org/showthread.php?t=1171339)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=45729](http://forums.linuxmint.com/viewtopic.php?f=42&t=45729)
[http://www.openoffice.org/issues/show_bug.cgi?id=100123](http://www.openoffice.org/issues/show_bug.cgi?id=100123)
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=28769&start=0](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=28769&start=0)
[http://framework.openoffice.org/servlets/ReadMsg?listName=features&msgNo=294](http://framework.openoffice.org/servlets/ReadMsg?listName=features&msgNo=294)
[http://www.bamweb.nl/computer/linux/267-openingsaving-files-with-openoffice-in-ubuntu-on-nfs-share](http://www.bamweb.nl/computer/linux/267-openingsaving-files-with-openoffice-in-ubuntu-on-nfs-share)
[http://user.services.openoffice.org/en/forum/viewtopic.php?t=10978](http://user.services.openoffice.org/en/forum/viewtopic.php?t=10978)

Any insight you can provide is appreciated.

Edit 1:
According to this thread, the method I tried (setting SAL_ENABLE_FILE_LOCKING=0) was based on earlier versions of openoffice.org It no longer works because as of openoffice.org 3 the file locking is built into the program. :(

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=15&t=12047&start=0](http://user.services.openoffice.org/en/forum/viewtopic.php?f=15&t=12047&start=0)

---

### Post by VH-BIL on 2010-06-23
Try:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=11419](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=11419)

> First go to Tools>Options>OOo>User Data and remove any comma or similar character in the First/Last name fields.

---

### Post by herteljt on 2010-06-23
Hi VH-BL. Thanks for the suggestion, but that solution is a work around for users who cannot edit locked files. The file lock is still created when a document is opened. I am trying to figure out how to turn off the lock option so that the file is not created.

---

