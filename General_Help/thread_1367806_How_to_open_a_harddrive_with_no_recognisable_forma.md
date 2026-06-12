---
title: "How to open a harddrive with no recognisable format"
date: 2009-12-29
forum: General Help
---

### Post by gosalia on 2009-12-29
I want to open my harddrive which is an NTFS, however the computer does not recognise it. It was previously holding Windows Vista, however after a fresh install of Vista I have tried again and again to open it in Ubuntu and Vista. (well not hard enough in Ubuntu, but I need your help still)
 
I would like to know of any application that can just open it so I can retrieve my files and then later format it. Thank you in advance...

---

### Post by taurus on 2009-12-29
Did you shut down windows cleanly the last time you used it?  Otherwise, you can always use ntfsfix to fix it.

> 
Name
ntfsfix - fix common errors and force Windows to check NTFS
Synopsis
ntfsfix [options] device
Description
ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows.

You may run ntfsfix on an NTFS volume if you think it was damaged by Windows or some other way and it cannot be mounted.
Options
Below is a summary of all the options that ntfsfix accepts. Nearly all options have two equivalent names. The short name is preceded by - and the long name is preceded by --. Any single letter options, that don&#8217;t take an argument, can be combined into a single command, e.g. -fv is equivalent to -f -v. Long named options can be abbreviated to any unique prefix of their name.

-h, --help
    Show a list of options with a brief description of each one. 
-V, --version
    Show the version number, copyright and license 


---

