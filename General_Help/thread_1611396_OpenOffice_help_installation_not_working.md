---
title: "OpenOffice help installation not working"
date: 2010-11-01
forum: General Help
---

### Post by PaulWhipp on 2010-11-01
I'm using Ubuntu 10.04LTS. I upgraded from 8.04 (which may be relevant to my problems) a while back.

OpenOffice was working with no Help visible. When I checked synaptic openoffice appeared as a manual install (probably because I installed version 3.0 manually on 8.04).

So I started by uninstalling it using 'remove completely' and re-installing.

I also deleted .openoffice.org (which was still left there in spite of the 'complete removal').

Sadly I still have no help coming up - the panes are blank. I installed openoffice.org-help-en-gb and the common files. Here is the full list:

```

~ $ apt-show-versions | grep openoffice
openoffice.org/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-base/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-base-core/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-calc/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-common/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-core/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-draw/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-emailmerge/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-filter-binfilter/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-filter-mobiledev/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-help-en-gb/lucid uptodate 1:3.2.0-7ubuntu1
openoffice.org-impress/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-java-common/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-l10n-common/lucid uptodate 1:3.2.0-7ubuntu1
openoffice.org-l10n-en-gb/lucid uptodate 1:3.2.0-7ubuntu1
openoffice.org-math/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-officebean/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-report-builder-bin/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-style-galaxy/lucid-security uptodate 1:3.2.0-7ubuntu4.1
openoffice.org-thesaurus-en-au/lucid uptodate 2.1-5
openoffice.org-writer/lucid-security uptodate 1:3.2.0-7ubuntu4.1

```

Everything reports as correctly configured and installed - e.g.
```

~ $ sudo dpkg --configure -a
~ $ 

```

Another minor anomaly is that Database, Presentation, Spreadsheet and Draw turned up in the Application menu as expected but Writer did not. This was easily remedied by adding the option but strange it was missing.

How can I get the OpenOffice Help facility to work?

---

### Post by vsh3r on 2010-11-01
Have you tried installing it with the Ubuntu Software Center?  Also, you should double check with a "whereis openoffice" command.

V$H.

:(

---

### Post by PaulWhipp on 2010-11-01
I haven't tried the software center but I can't see how it would make any difference.

whereis reports the expected locations:
```

~ $ whereis openoffice
openoffice: /usr/bin/openoffice.org /etc/openoffice /usr/lib/openoffice /usr/share/openoffice /usr/share/man/man1/openoffice.1.

```

Should it show anything for help?

---

### Post by vsh3r on 2010-11-01
Hi,

Someone needs to update Ubuntu to remove software similar to OSX.  In OSX when you install a package it installs everything in one directory called APPLICATION.APP and then to remove the program you ONLY REMOVE THAT DIRECTORY and thats it.

As you have shown, Linux works differently and has a lot of library dependencies and places cross linked files with shadow directories with links rather then the actual file which is getting to be a nightmare.  

This has long been a problem in Windows and Linux.

V$H.

:KS

---

### Post by hrickh on 2010-11-01
I'm also running 10.04 LTS. My help works - the differences i see between your install and mine are:

ure
uno-libs3
python-uno

Truthfully, I don't know that installing those would make a difference. I just know that I have those installed and you don't have those listed.

Oh, and I guess I also have openoffice.org-gnome and openoffice.org-gtk installed.

HTH

R.
==

---

### Post by PaulWhipp on 2010-11-01
Hi hrickh,

I have ure, uno-libs3 and python-uno installed (the openoffice grep did not show them).

I did not have have openoffice.org-gnome or gtk. I don't think they are related but...

I installed them anyway and they have indeed made no difference. Help still comes up blank. Its very irritating, particularly as I'm pushing OpenOffice to friends - its easy to workaround using online help but I am not always online and even when I am its a lot nicer going through the built in help... if only it worked.

---

### Post by PaulWhipp on 2010-11-02
For whatever reason this worked :-

I uninstalled my reinstalled help (the gb file) with synaptic. I then installed the us help file figuring that is the most likely one to work without issue.

Sure enough it worked fine. Problem solved.

---

