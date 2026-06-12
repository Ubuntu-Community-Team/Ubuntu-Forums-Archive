---
title: "Recovering Data..."
date: 2009-12-27
forum: General Help
---

### Post by Tom_T on 2009-12-27
Hi

My laptop has just died so I've removed the hard disk and placed it into a 2.5" to USB drive bay.

Connected it to my Ubuntu PC and can copy the files I need across.
(The laptop and PC both have the same Ubuntu username & password)

What I would like to know is is it possible to get my Firefox bookmarks and the saved username/password data from my laptops disk ?

The disk has XP, 7 & Ubunto 9.04 installed..  I want the firefox bits from the ubuntu partition.

I've not had any problems copying other data from any of the partitions upto know..  I just don't know where to look.

Thanks :)

---

### Post by diablo75 on 2009-12-27
In short, you'll want everything in your Home Folder.  If you're viewing this through Linux, that means it's probably not showing you the hidden folders/files.  Anything that begines with a period .likethis is a hidden file.  Just hit CTRL-H in Nautilus to show them, or use the Edit menu to reveal them.

Now for specific things like your Firefox stuff, just copy the .mozilla folder somewhere.  Once you get your system back up and running, copy the backup into your home and tell Nautilus to Merge it with the folder that's already there.  Everything involving Firefox will be restored automatically, including bookmarks, history, saves passwords, etc.

To make this easy for you in the future, you should install with manual partitioning and create 3 partitions.  One for your root partition / , one for your /home/ partition and a third for your swap.  This way if the system crashes, you can just reinstall by deleting the root, and telling the system to point to the /home/ partition for home so you don't have to restore anything manually; it'll already be restored (so long as you setup the first account to be the same username as it was previously).  In other words, the username has to match the name of your folder within /home/.  Now, you don't have to do this; it's just about as easy to backup your entire Home folder then copy it completely back into your new Home folder after a re-install.

---

### Post by chewearn on 2009-12-27
Goo:

[http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles)

---

