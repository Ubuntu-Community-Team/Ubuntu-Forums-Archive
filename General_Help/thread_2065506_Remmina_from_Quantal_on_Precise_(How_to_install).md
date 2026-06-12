---
title: "Remmina from Quantal on Precise (How to install)"
date: 2012-10-02
forum: General Help
---

### Post by moteprime on 2012-10-02
Hi.
I'm on Precise using the standard Remmina from the repoes, but it's got some annoying window placement bugs.
I tested Quantal, and discovered that the bugs have been fixed in the version shipped with Quantal.
In both version of Remmina, under "About", it's the same version number, "0.9.99.1".
Why don't they put the "fewer bugs version" in Precise, or how can I install it there

---

### Post by dcstar on 2012-10-02
> **moteprime said:**
> Hi.
I'm on Precise using the standard Remmina from the repoes, but it's got some annoying window placement bugs.
I tested Quantal, and discovered that the bugs have been fixed in the version shipped with Quantal.
In both version of Remmina, under "About", it's the same version number, "0.9.99.1".
Why don't they put the "fewer bugs version" in Precise, or how can I install it there

You go here and manually download the packages and dependencies and install them:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

The fixed version may be eventually backported to 12.04, you just have to be patient.

I had to remove the existing Remmina and Freerdp packages and then install the following 12.10 packages to get that version of Remmina working on 12.04 (not necessarily in this order):

```
freerdp-x11_1.0.1-1ubuntu7_amd64
libfreerdp1_1.0.1-1ubuntu7_amd64
libfreerdp-plugins-standard_1.0.1-1ubuntu7_amd64
libpam-freerdp_1.0.1-0ubuntu1_amd64
remmina_1.0.0-1ubuntu8_amd64
remmina-common_1.0.0-1ubuntu8_all
remmina-plugin-rdp_1.0.0-1ubuntu8_amd64
```

---

### Post by moteprime on 2012-10-02
Thanks David.
The way you put it, it sounds like i just better wait and hope for a backport. :-)
Thanks

---

