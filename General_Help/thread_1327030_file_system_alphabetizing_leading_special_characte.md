---
title: "file system alphabetizing leading special characters"
date: 2009-11-15
forum: General Help
---

### Post by akahige on 2009-11-15
I've got a NAS that serves files via SMB/CIFS to a number of Windows and Linux machines. The convention has evolved that files or directories that are considered to have special significance or priority are named with a leading ~ . On Windows, this places them at the top of the alphabetical structure (as _ would move them to the bottom).

The problem is that Linux ignores the ~ and alphabetizes these directories in with everything else, which plays merry hell with the ability to find them (or tell people where to look for them). (Apparently, this has something to do with the ~ being a special bash character, even though the file systems are really only ever navigated from GUI file managers, and not from a shell.)

There's no problem opening, moving, manipulating these files, only finding them alphabetically.

Hoping that someone has some suggestions as to how to either fix or work around this issue.

---

