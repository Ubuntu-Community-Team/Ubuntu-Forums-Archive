---
title: "Problems with 'tomboy'......(Empty file name)"
date: 2011-04-29
forum: General Help
---

### Post by Thewhistlingwind on 2011-04-29
> installArchives() failed: Selecting previously deselected package libjline-java. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `tomboy' contains empty filename 
So, I removed tomboy notes the other day, and now I'm getting this whenever I touch apt-get. Not fun, not making me happy. Kind of annoyed. Google does not appear to know the answer, so any help would be appreciated.

Thank you in advance.:D

---

### Post by Thewhistlingwind on 2011-04-29
Forums are busy today, bump.

---

### Post by Thewhistlingwind on 2011-04-30
Solved, using the advice outlined here. ([http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-missing-final-newline-271118/](http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-missing-final-newline-271118/))

Of course, since I uninstalled tomboy, I didn't need the list file anyway.;)

EDIT: To outline in case of dead link:

The list file for applications occasionally gets trashed when playing with apt-get, the solution is to remove the list file then reinstall the application. (Unless you feel like recreating that file by hand.......)

---

