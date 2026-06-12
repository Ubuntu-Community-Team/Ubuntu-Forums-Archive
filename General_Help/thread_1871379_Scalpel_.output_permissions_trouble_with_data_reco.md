---
title: "Scalpel ./output permissions trouble with data recovery"
date: 2011-10-28
forum: General Help
---

### Post by jnuak on 2011-10-28
My brother-in-law did a fresh install of 11.04 recently.  He has the following partitions:

16GB ext4 /
4GB swap
480GB ext4 /home

When he installed, he left the home partition be, but chose a new username.  He tried to add a new user with the old username, so he could log in and gain access to all his saved preferences.  

At that point, he gets fuzzy on what happened.  He clicked something, and when the dust settled, he could log in with his old username, but his files were gone.  He turned off the computer, and the HD has not been mounted since.  

I wasn't sure how to handle this, so I ran scalpel, looking only for .doc and .pdf files.  The output file created on my HD did not allow me access.  I used chown to make myself the owner, and ran chmod a-rwx.  

When I run sudo ls -l ./output/ I can see that my user is the owner, and the permissions should be there, but if I try to open the .doc files, I get permission denied.  

Also, inside the /output folder are numerous directories that appear as files, ex: ./output/doc-0-0/.  I can list files in the ./output/doc-0-0/ directory with sudo and see numerous, in this case, .doc files inside.  

Probably more than one way to skin this cat, but I just want to get back docs and pdfs.  All other files were backed up prior to making any changes.  

Any ideas?  Thanks in advance for your help.

---

