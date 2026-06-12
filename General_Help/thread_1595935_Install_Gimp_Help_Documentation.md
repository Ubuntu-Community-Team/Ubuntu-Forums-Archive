---
title: "Install Gimp Help Documentation"
date: 2010-10-13
forum: General Help
---

### Post by Tony_Harrison on 2010-10-13
My goal is to install the Gimp Help Documentation locally (as opposed to using the Web-based help). I am having difficulty accomplishing this.
The seemingly obvious solution was to apt-get the gimp-help-common package, but this did not enable the help function in the program itself. I found no such packages in the standard repositories.
Does anyone know where I can get this or how I can enable this?

Thanks in advance!

---

### Post by mikewhatever on 2010-10-13
Gimp documentation should be located in /usr/share/doc/. For example, if you have gimp-help-en installed, open Firefox and paste the following into the address bar:

file:///usr/share/doc/gimp-help-en/html/en/index.html

---

### Post by Tony_Harrison on 2010-10-13
That did it! I guess I just needed to install the gimp-help-en package (which installs gimp-help-common too) and it worked within Gimp!
Thanks, Mike!

---

### Post by XEtedBear on 2010-12-31
> **mikewhatever said:**
> Gimp documentation should be located in /usr/share/doc/. For example, if you have gimp-help-en installed, open Firefox and paste the following into the address bar:

file:///usr/share/doc/gimp-help-en/html/en/index.html


Sorry, on my system this doesn't work at all. Firstly the GIMP help documentation contains installation instructions in an INSTALL file. These instructions state where the help files (html files) should be installed  - and those instruction do not agree with what you have stated.

The INSTALL file with version 2.6.1 of the Help documentation implies the  installation folder by the following command:

```

$ cp -R html/en $prefix/share/gimp/2.0/help/

```

where '$prefix' is shown (in the included makefile file) to be '/usr'

Unfortunately neither the explicit copy command nor use of the special makefile installs the help files into a location that GIMP itself knows about - it still says the help files are not installed.

So, where should they go and why are the INSTALL instructions inconsistent with the application?

---

