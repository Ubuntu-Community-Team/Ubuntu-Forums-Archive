---
title: "Fresh reinstall"
date: 2012-07-01
forum: General Help
---

### Post by Robbyx on 2012-07-01
I have had to re-install Ub 12.04 using the livecd and not use the old home directory that was on another drive (I could not log in except as guest). Instead I have created the home drive as part of the root and not put it on another drive.

I have restored the apps that were previously installed, via dpkg and the package.selections list.

Is it ok to copy over the old home subfolders to the new location, for the programs that have been reinstalled? Will I have any problems because the locations of the home directories are not the same? Will there be internal instructions within the program folders within the old home that will not be compatable in the single system location?

Should I copy over the old home folders before or after I rsync the new home to the seperate drive previously used for the home directory?

Robin

---

### Post by mikewhatever on 2012-07-01
You shouldn't have any problems with programs, but I would just copy the profiles, and not everything. Program profiles are usually found in the hidden folders, .program_name.

---

