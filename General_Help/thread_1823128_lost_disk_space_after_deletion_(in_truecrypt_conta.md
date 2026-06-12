---
title: "lost disk space after deletion (in truecrypt container)"
date: 2011-08-11
forum: General Help
---

### Post by HLS69 on 2011-08-11
First of all:

I ve read [this page]("https://help.ubuntu.com/community/RecoverLostDiskSpace") and tried some methodes such as opening nautilus with

"gksudo nautilus" and then checking (the now root?) trash bin.

Ive got a ext4 formated truecrypt container which has a size of 400GB. After I have deleted all the files in it nautilus tells me that I now have only about 100gb free space but I cant see any files in the container anymore.

Heres a picture of the situation:

[IMG]http://img17.imageshack.us/img17/4519/screenshotzud.png[/IMG]

Can you please give me a hint where the deleted files are still located?

---

### Post by gordintoronto on 2011-08-11
It has its own Trash bin, which you can only see if you Edit/Preferences in Nautilus, and tell it to display hidden files.

If it's empty, you should be able to delete and re-create it.

---

### Post by 11.04 on 2011-08-11
Since you're deleting all the files anyway, why not just do a format of the container to ensure its filesystem becomes clean and empty again.

---

### Post by westie457 on 2011-08-11
Unless you used Shift+Del to remove the files they are definitely hidden so no one can find them and they take up space on the hard drive. The safe way to reclaim the space is with a LiveCD/USB and using Gparted to check the file system for that partition for errors. Make sure it is not mounted otherwise there is a big chance of damaging your system.

I once had a partition that was supposed to be about 30% full and Nautilus I think was telling me I had something like 18MB of free space. The file system check worked for me, hopefully it will for you.

---

### Post by HLS69 on 2011-08-11
thank you very much!

after I checked "Show hidden and backup files" in Edit - Preferences

a new folder showed up and after I deleted that folder (with just "del") the files were gone.

Strange thing is that there are still 20.2 GB used.. I didn t check how the graph in the "Properties" windows looked when I created the encrypted container - mybee this is due to the calculation sheme from GB to GiB or something. Can anybody confirm that this is normal behavior?


> **11.04 said:**
> Since you're deleting all the files anyway, why not just do a format of the container to ensure its filesystem becomes clean and empty again.

I suppose that this would work but its not what I want. Lets say that I am facing this problem again in 2 mounts... what should I do then?

Anyways: what way would you suggest to format the drive and what settings should I avoid (is there anything special to take care because its a encrypted container?)

---

