---
title: "Libreoffice install caused problems that no other solutions can fix"
date: 2012-02-28
forum: General Help
---

### Post by MiketheCalamity on 2012-02-28
This is going to seem like a previous post. Well I do admit it is very similar the only difference is, no solution has fixed my problem. First off I have Ubuntu 11.10 Oneiric. It all start when I stupidly tried 'sudo apt-get install libreoffice' Now there is the unmet dependencies problem in the Software Center and the terminal. Here are the things i have tried to fix this and their output:

1. sudo apt-get clean (no output)

2. sudo apt-get update (runs without error)

3. sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:3.4.4) but it is not installed
 libreoffice-java-common : Depends: libreoffice-common but it is not installed
E: Unmet dependencies. Try using -f.

4. sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango libreoffice-style-crystal libreoffice-style-oxygen
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
15 not fully installed or removed.
Need to get 0 B/16.9 MB of archives.
After this operation, 43.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 210103 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

5. sudo dpkg --configure -a

<might be more up here but the terminal cuts it off>
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-core is not configured yet.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.4.4-0ubuntu1); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libreoffice-java-common
 libreoffice-filter-mobiledev
 libreoffice-base
 libreoffice-report-builder-bin
 libreoffice-core
 libreoffice-style-human
 libreoffice-math
 libreoffice-impress
 libreoffice
 libreoffice-writer
 libreoffice-base-core
 libreoffice-emailmerge
 python-uno
 libreoffice-draw
 libreoffice-calc

6. When I sudo rm /var/cache/apt/archives/libreoffice-common_1%3a3.4.4-0ubuntu1_all.deb and then clean and update and run the USC it tries to "repair broken deps" but once it says "Finished" it says there's an error again and then when it tries to "repair broken deps" it quickly fails.

What else can I do? Is there a way to clear my last install or something?

---

### Post by ajgreeny on 2012-02-28
This may be one jump further than you wish to go, and I do not even know for certain if it is possible in 11.10, but have you considered enabling the ppa for libreoffice, which is now providing 3.5.0, and very good it is too.

I realise that 11.10 has LO as a default installation, but simply wonder if the ppa will manage to provide the missing dependency that is causing your current problem.

If you prefer not to do that, can I suggest that you try using synaptic to fix the broken package from its "Edit" menu.  You will need to install synaptic first as it is not included with the default packages, a big mistake in my opinion, as it is so much better and more flexible than USC.  It is usually very good at fixing broken packages.

---

