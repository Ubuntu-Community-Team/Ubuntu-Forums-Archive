---
title: "access denied on ext4 external drive - say what?"
date: 2010-05-12
forum: General Help
---

### Post by zachthejones on 2010-05-12
I had an old desktop which had Ubuntu 9.10 on it. I recently decided to do away with the old desktop, but to salvage the hard drive by putting it in an external enclosure to access via USB. I can access (from my laptop) all the files perfectly normally - except for my music files!

When I try to open a folder in my music directory I get a "Permission denied" error. Any idea why this is happening and/or a way around this? I really don't want to have rebuild the old dinosaur to backup these files...

---

### Post by koanhead on 2010-05-13
Have you tried to 'sudo chown -R' that directory?
Are the files in the directory owned by your uid? Use 'ls -n' to get the uid of the files' owner(s).
Are the files or the directory owned by a group of which you are not a member?

---

### Post by zachthejones on 2010-05-16
thanks! didn't realize I could use the "chown" command to fix the problem...guess I need to brush up on the 'ole terminal commands a bit. for the record, heres the command I used to fix stuff (after navigating to my old home folder on the drive):
```
sudo chown -R [username] Music 
```
After using that command I could access and copy all the stuff in my music folder...at least so far.

thanks again!

---

