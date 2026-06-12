---
title: "Package Manager Errors after Update"
date: 2009-08-21
forum: General Help
---

### Post by jimmm33 on 2009-08-21
After a recent update, I started getting this on my server. I'm running 9.04 Server with the gnome desktop. I cant' run the package manager at all.

E: Problem parsing dependency Depends
E: Error occurred while processing openoffice.org-gnome (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

When I run 

sudo dpkg --configure -a

I get:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 3012:
 invalid package name (character ` ' not allowed (only letters, digits and characters `-+._'))

I ran this:

sudo nano +3012 status

I found dozens of files with illegal characters. Many words had a letter replaced with ! or &. I fixed many, but the file has 31000 lines and I can't check it all. The error regarding line 3012 never changes.

Is there a way to restore this file or that not my problem?

The update also killed my Nvidia drivers (again) but I think that is a different problem that would be best to solve after this package manager problem.

---

### Post by michy99 on 2009-08-21
Does it help if you replace status with status-old?```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by jimmm33 on 2009-08-21
That did it. Thank you.

---

