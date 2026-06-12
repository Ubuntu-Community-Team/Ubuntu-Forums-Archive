---
title: "planing new install"
date: 2010-12-16
forum: General Help
---

### Post by mxsteini on 2010-12-16
Hi there,
I'm planing a completly new install of my machine to get rid of things from version 8.04 and older.
But, is there a way to figure out which packages I've installed in addition to the CD?

---

### Post by cjhabs on 2010-12-16
sudo dpkg --get-selections

I don't know of it lists packages that were installed outside of the configured repositories.

---

### Post by mxsteini on 2010-12-17
Thanks for your answer.
How do I interpret that list?
Packages with uninstall are on my machine.
What are the others?

---

### Post by karthick87 on 2010-12-17
You can use Synaptic to save the current state  of your installed packaged. In Synaptic, select "file/save markings",  Enter the name of the file to save the state to, and make sure to check  the "Save full state, not only changes" box.The file saved from this can be loaded into a new machine using "file/read markings" in Synaptic.

---

### Post by cjhabs on 2010-12-17
> **mxsteini said:**
> Thanks for your answer.
How do I interpret that list?
Packages with uninstall are on my machine.
What are the others?

From the man page:
  PACKAGE SELECTION STATES
       install
              The package is selected for installation.

       hold   A package marked to be on hold is not handled  by  dpkg,  unless  forced  to  do  that  with  option
              --force-hold.

       deinstall
              The  package  is selected for deinstallation (i.e. we want to remove all files, except configuration
              files).

       purge  The package is selected to be purged (i.e. we want to remove everything, even configuration files).

---

