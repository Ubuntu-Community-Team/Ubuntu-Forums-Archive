---
title: "ssh X forwarding + gedit"
date: 2010-02-20
forum: General Help
---

### Post by dretep on 2010-02-20
I've been having issues trying to run gedit from my work machine on my home machine via SSH (both are running Ubuntu 9.10) for a while.

I was able to find information from others having a similar issue and receiving the error:
**X11 connection rejected because of wrong authentication.**

Solutions included changing .Xauthority permissions or even removing the file so it can be recreated.

Tonight I finally discovered that I can reproduce the bug that was found and corrected in Redhat's gedit:
[http://rhn.redhat.com/errata/RHBA-2008-0019.html](http://rhn.redhat.com/errata/RHBA-2008-0019.html)

> This update addresses the following problems:

* starting a remote X11 session when a local instance of gedit was already
running under the same user would cause the local instance to close and the
remote instance to be unable to open. This has been fixed so that gedit
will open a remote instance while also retaining the local one (i.e. not
closing it).

Running 'sudo gedit' will allow me to start gedit with the remote instance still running but files created will of course be owned by root.

If I kill the remote gedit process I can start gedit successfully but that's not ideal either. Anyone else come across this? Should this be reported as a bug?

---

