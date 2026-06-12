---
title: "Exit status 127"
date: 2010-05-07
forum: General Help
---

### Post by Greasyfingers on 2010-05-07
Your help needed:

I've just installed Studio 10.04 from scratch, and am still configuring it. But for some reason I'm getting an error message whenever I try to install or remove anything. This seemed to start after I uninstalled Knode newsreader.

From synaptic:

E: install-info: subprocess installed post-installation script returned error exit status 127

From apt-get:

dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've looked around for solutions, but none of them seem relevant to my setup.

How do I fix this, please?

---

### Post by Greasyfingers on 2010-05-07
Solved this:

I had incorrectly set up an Environment Variable in /etc/environment so that it pointed to a non-existent file system. Oops. For some reason this stopped stuff installing and uninstalling.

---

