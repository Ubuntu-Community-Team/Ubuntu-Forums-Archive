---
title: "Restore deleted folders and files"
date: 2011-09-21
forum: General Help
---

### Post by Trubbelgum on 2011-09-21
Hi!
I know there are many threads and programs for this, but I can't find any thread, with a good howto.

I want to restore my files and folders in /home/a/, which were deleted yeserday by a mistake.
All programs I've tried for this, could only restore separate files and not whole folders.

Can anyone guide me to the easiest way to restore my completely deleted files in my home folder?

---

### Post by Trubbelgum on 2011-09-21
I've found a program called "gddrescue", but I can't get the program to restore my home folder either (I can just restore whole partitions)

Anyone who can guide me to restore my folder /home/a/?

---

### Post by Trubbelgum on 2011-09-21
I've found a good program now that is called foremost and can be installed by *sudo apt-get install foremost*.

First I needed to open up /etc/*foremost*.conf and uncomment some lines, but then I only needed to put in this:
*sudo foremost -t all -i /home/a/ -o /media/Storage/myoutputfile/*

and now it's working with the recovering :), but it seems to take hours

---

