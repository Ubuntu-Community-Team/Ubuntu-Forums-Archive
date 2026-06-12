---
title: "Cannot delete folder on NTFS partition from nautilus or terminal"
date: 2010-08-12
forum: General Help
---

### Post by jrop on 2010-08-12
So on my NTFS partition, I have a folder I want to delete.  In nautilus, I right click and select "Move to Trash."  It says "Cannot move file to trash, do you want to delete immediately?" and I click "Delete" and get this message: "Error while deleting. Could not remove the folder [a sub-folder of the directory I want to delete]. Error removing file: Directory not empty."  I then open a terminal, and try the following command: "rm -rf /path/to/dir" and get "rm: cannot remove directory `[dir]/[sub-dir]': Directory not empty."  I even tried sudo'ing the command in still no worky. :confused:

What in the world should I do to get this to work (besides doing the recursive delete myself)?

---

### Post by Mark Phelps on 2010-08-12
If this NTFS partition is an MS Windows OS partition, you're most likely wasting your time trying to remove these folders using Linux because of protections that MS Windows has put in place.

And yeah, I know the Linux "NTFS experts" will claim this is NOT possible -- but I KNOW it IS because I experienced it myself recently on my own system.  Had to boot into Windows, take ownership of the folder and its files -- and only THEN could I do anything to the files.

---

### Post by jrop on 2010-08-13
Well, I can delete files, just not non-empty directories it seems.

---

### Post by LBraiden on 2010-11-25
The above answers are misleading.  When you do a recursive delete and get a message that the directory is not empty, it usually means that something is USING the directory.  You might have a nautilus window open at that directory, for instance, or you might have a shell cd'd to that directory, or just some other program using it for any given reason.

The fuser command will help to find out what's causing the problem.  For example, to find all processes using /home:

fuser -m /home

which will list matching process IDs.

---

