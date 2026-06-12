---
title: "Changing File Permissions for Multiple Folders"
date: 2009-12-16
forum: General Help
---

### Post by tacantara on 2009-12-16
I copied my home folder to an external HD prior to doing a fresh install of 9.10.  After the install, I copied the files back to my computer HD, only to find that many of my folders and files were changed to root access.  I can change them back, one at a time, by opening a file browser in gksudo, but that is very time consuming for the large number of folders and files I have that are "locked up."  Is there a faster way to identify those files and return them to full access?  I am the only user on my machine, so I don't have to worry about restricted access for anyone else.

---

### Post by scouser73 on 2009-12-16
Use these commands.

This makes you Root
> sudo -i

This changes to your home directory as Root, change **/yourname** to you
> cd /home/yourname

This changes all of the files back to you, so you won't need to do it one by one.
> chown -R username filename

---

### Post by tacantara on 2009-12-16
Thank you, scouser73 :)  That did the trick nicely.  I was copying music files from my music folder to my Droid the other day, and half of the files wouldn't transfer because they were locked up with root access.  Now I've got those files and a bunch more back to where they need to be for me.

---

