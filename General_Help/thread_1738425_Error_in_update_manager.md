---
title: "Error in update manager"
date: 2011-04-24
forum: General Help
---

### Post by perolad on 2011-04-24
What does the below mean and how to fix it, or doesn't it matter?  Ubuntu 10.04 LTS,  Thanks...

[B]E: synaptics-dkms: subprocess installed post-installation script returned error exit status 2
[/B]

---

### Post by KegHead on 2011-04-24
Hi!

Have you tried via the terminal;

sudo apt-get update

sudo apt-get upgrade -f

Please advise.

KegHead

---

### Post by perolad on 2011-04-24
> **KegHead said:**
> Hi!

Have you tried via the terminal;

sudo apt-get update

sudo apt-get upgrade -f

Any ideas?  Thanks!   -Per

KegHead

----

Yes, just did.  Here's the result.  Looks like it doesn't exist, even  though update manager thought it was. Any further insights?  Thanks...

Error! Cannot locate /usr/src/synaptics-1.1.1.dkms.tar.gz.
File does not exist.
dpkg: error processing synaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 synaptics-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lumix on 2011-05-01
Bumpity.

---

