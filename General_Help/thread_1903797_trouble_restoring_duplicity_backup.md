---
title: "trouble restoring duplicity backup"
date: 2012-01-03
forum: General Help
---

### Post by smcoll on 2012-01-03
Using Deja Dup in 11.04, i backed up my home directory to an external USB drive, and incrementally updated that backup several times, most recently Jan 1.  i made a fresh install of Unbuntu 11.10 later that day and proceeded to restore my files using Deja Dup, but when i reached the "Restore from When?" dialog, the most recent backup dates were not listed as options.

These date were listed: 10/28/2011, 09/30/2011, 09/11/2011.  i know there were several backups since then in November, December, and one for Jan 1, 2012.  There were times i used the "resume later" function during that period.  In any case, i ultimately got an indication that backup was successful each time i attempted a backup, and didn't get any error messages.

i used duplicity to restore what i had to a new directory, and it looks like it restored to the 10/28/2011 version.  i have attached the terminal output of that command (which says there are tons of "orphaned" backup files), and also a list of files in the backup directory.  Fortunately there are gpg files for the December and January backups, but i don't know how to make use of them while duplicity is ignoring them.

What can i do?

---

### Post by smcoll on 2012-01-03
Here's some more information that might help.

i noted that there is a missing manifest between 20111029 and 20111116, and that the several subsequent incrementals refer to 20111116 as the starting point. Here are the manifests in that list:

duplicity-full.20110911T222234Z.manifest.gpg
duplicity-inc.20110911T222234Z.to.20110930T225238Z.manifest.gpg
duplicity-inc.20110930T225238Z.to.20111029T040635Z.manifest.gpg
duplicity-inc.20111116T003041Z.to.20111116T033432Z.manifest.gpg
duplicity-inc.20111116T003041Z.to.20111212T172444Z.manifest.gpg
duplicity-inc.20111116T003041Z.to.20120101T171352Z.manifest.gpg
duplicity-inc.20111116T003041Z.to.20120101T192903Z.manifest.gpg

i also noted that (fortunately) there are difftars for that missing manifest:

duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol10.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol11.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol12.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol13.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol14.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol15.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol16.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol17.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol18.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol19.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol1.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol20.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol21.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol22.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol2.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol3.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol4.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol5.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol6.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol7.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol8.difftar.gpg
duplicity-inc.20111029T040635Z.to.20111116T003041Z.vol9.difftar.gpg

i'm glad that it appears all my data is present in some form, but i'm in a bad way until i can restore from it.

---

