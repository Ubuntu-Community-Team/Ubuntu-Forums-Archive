---
title: "DCC (Distributed Checksum Clearinghouse)"
date: 2010-10-16
forum: General Help
---

### Post by aSteve on 2010-10-16
I'm using Ubuntu 10.10 (server) and I'm trying to install the client for DCC (The Distributed Checksum Clearinghouse) - but I can't find it.  It used to be called dcc-client, but I get:

# apt-get install dcc-client
Reading package lists... Done
Building depdendency tree
Reading state information... Done
E: Unable to locate package dcc=client
#

What gives, is DCC deprecated?  Do I need to use a special repository?

---

### Post by dcstar on 2010-10-16
> **aSteve said:**
> I'm using Ubuntu 10.10 (server) and I'm trying to install the client for DCC (The Distributed Checksum Clearinghouse) - but I can't find it.  It used to be called dcc-client, but I get:

# apt-get install dcc-client
Reading package lists... Done
Building depdendency tree
Reading state information... Done
E: Unable to locate package dcc=client
#

What gives, is DCC deprecated?  Do I need to use a special repository?

These have no been available since Dapper:

[http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=dcc](http://packages.ubuntu.com/search?suite=all&searchon=names&keywords=dcc)

---

### Post by aSteve on 2010-10-17
Hmmm... that squares with what I've seen.

Was there a reason that this tool was dropped? Is it available from some 3rd party repository?  Am I hideously old-fashioned in thinking DCC is useful?

---

### Post by Firefishy on 2011-03-18
This bug: [https://bugs.launchpad.net/ubuntu/+source/dcc/+bug/228206](https://bugs.launchpad.net/ubuntu/+source/dcc/+bug/228206) implies it was removed due to using a non-free license.

---

