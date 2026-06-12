---
title: "update-manager: You have held broken packages"
date: 2010-06-04
forum: General Help
---

### Post by BlueTeam on 2010-06-04
I beg your pardon, but I only hold one package, and it's definitely not broken, LOL.

Anyway, so I just did an update on 10.04 and it blew up.  Now I get this mean message when I try to rerun the update manager:

"Could not initialize the package information"

"An unresolvable problem occurred while initializing the package information.  Please report this bug against the 'update-manager' package and include the following error message:  'E:Unable to correct problems, you have held broken packages.' "

So, I no nothing of bug reports.  

Am I screwed now, or can this be resolved by typing a few magical lines in a terminal window?

Thanks in advance.

---

### Post by lisati on 2010-06-04
You can use Synaptic Package Manager to help fix "broken" packages. On my machine (10.04) the relevant option is on the "edit" menu. Don't forget to close the update manager first.

---

### Post by BlueTeam on 2010-06-04
Thanks, unfortunately I get the same error from the "Fix Broken Packages" option in the Synaptic Package Manager.  It alerted me to 58 broken packages.  I guess it's time to format and reload.  Annoying, but oh well.

---

### Post by DougDorr on 2010-06-08
Yikes!  I get the same thing.  No way am I going to reload this junky release.  :mad:

I get a warning that some packages can't be authenticated.

W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-security_multiverse_binary-i386_Packages)


These are the packages:


abcde (version 2.4.0-1ubuntu1) will be upgraded to version 2.4.0-1ubuntu1.1
brasero-common (version 2.30.0-0ubuntu1) will be upgraded to version 2.30.1-0ubuntu2
chromium-browser (version 5.0.342.9~r43360-0ubuntu2) will be upgraded to version 5.0.375.38~r46659-0ubuntu0.10.04.1
chromium-browser-inspector (version 5.0.342.9~r43360-0ubuntu2) will be upgraded to version 5.0.375.38~r46659-0ubuntu0.10.04.1
epiphany-browser (version 2.30.2-1ubuntu1) will be upgraded to version 2.30.2-1ubuntu1.1
epiphany-browser-data (version 2.30.2-1ubuntu1) will be upgraded to version 2.30.2-1ubuntu1.1
epiphany-browser-dbg (version 2.30.2-1ubuntu1) will be upgraded to version 2.30.2-1ubuntu1.1
gnome-keyring (version 2.92.92.is.2.30.1-0ubuntu1) will be upgraded to version 2.92.92.is.2.30.1-0ubuntu2
gnome-panel (version 1:2.30.0-0ubuntu1) will be upgraded to version 1:2.30.0-0ubuntu2
gnome-panel-data (version 1:2.30.0-0ubuntu1) will be upgraded to version 1:2.30.0-0ubuntu2
gnome-panel-dbg (version 1:2.30.0-0ubuntu1) will be upgraded to version 1:2.30.0-0ubuntu2
gxine (version 0.5.904-2ubuntu3) will be upgraded to version 0.5.904-2ubuntu3.1
libbrasero-media0 (version 2.30.0-0ubuntu1) will be upgraded to version 2.30.1-0ubuntu2
libcairomm-1.0-1 (version 1.8.0-1build2) will be upgraded to version 1.8.4-0ubuntu1
libgcr0 (version 2.92.92.is.2.30.1-0ubuntu1) will be upgraded to version 2.92.92.is.2.30.1-0ubuntu2
libgp11-0 (version 2.92.92.is.2.30.1-0ubuntu1) will be upgraded to version 2.92.92.is.2.30.1-0ubuntu2
libpam-gnome-keyring (version 2.92.92.is.2.30.1-0ubuntu1) will be upgraded to version 2.92.92.is.2.30.1-0ubuntu2
libpanel-applet2-0 (version 1:2.30.0-0ubuntu1) will be upgraded to version 1:2.30.0-0ubuntu2
openoffice.org (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-base (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-base-core (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-calc (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-common (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-core (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-draw (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-emailmerge (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-evolution (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-filter-binfilter (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-filter-mobiledev (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-gnome (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-gtk (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-impress (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-java-common (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-math (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-officebean (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-report-builder-bin (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-style-galaxy (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-style-human (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
openoffice.org-writer (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
python-papyon (version 0.4.6-0ubuntu2) will be upgraded to version 0.4.8-0ubuntu1
python-uno (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
rhythmbox (version 0.12.8-0ubuntu5) will be upgraded to version 0.12.8-0ubuntu6
rhythmbox-dbg (version 0.12.8-0ubuntu5) will be upgraded to version 0.12.8-0ubuntu6
rhythmbox-plugin-cdrecorder (version 0.12.8-0ubuntu5) will be upgraded to version 0.12.8-0ubuntu6
rhythmbox-plugins (version 0.12.8-0ubuntu5) will be upgraded to version 0.12.8-0ubuntu6
telepathy-butterfly (version 0.5.8-1ubuntu1) will be upgraded to version 0.5.9-0ubuntu1
ttf-opensymbol (version 1:3.2.0-7ubuntu4) will be upgraded to version 1:3.2.0-7ubuntu4.1
tzdata (version 2010i-1) will be upgraded to version 2010j-0ubuntu0.10.04
tzdata-java (version 2010i-1) will be upgraded to version 2010j-0ubuntu0.10.04
uno-libs3 (version 1.6.0+OOo3.2.0-7ubuntu4) will be upgraded to version 1.6.0+OOo3.2.0-7ubuntu4.1
ure (version 1.6.0+OOo3.2.0-7ubuntu4) will be upgraded to version 1.6.0+OOo3.2.0-7ubuntu4.1
xsane (version 0.996-2ubuntu2) will be upgraded to version 0.996-2ubuntu3
xsane-common (version 0.996-2ubuntu2) will be upgraded to version 0.996-2ubuntu3

If this can't be fixed easily, I think I'm going to Windows 7 or to Mac OS.

---

### Post by Yellow Pasque on 2010-06-08
So why are they broken? What is the output of;
```
sudo apt-get dist-upgrade
```

---

### Post by DougDorr on 2010-06-09
I don't know about anybody else, but 24 hours with no fixes applied on my part, the update manager ran successfully.  Guess QA just isn't QA anymore.

---

