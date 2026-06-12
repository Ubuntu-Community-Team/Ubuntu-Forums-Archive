---
title: "Upgrade"
date: 2012-04-26
forum: General Help
---

### Post by jpg123 on 2012-04-26
hi, im planning to go from 11.10 to 12.04 via the upgrade function in the desktop, im currently running a 32 bit 11.10 and i want to upgrade to a 64bit 12.04, will i be able to do this?
 
cheers

---

### Post by oldfred on 2012-04-26
You cannot upgrade from 32bit to 64bit. When I did it from 9.04 to 9.10, it was just a clean install. I missed a few things back then, but found I really prefer clean installs as it housecleans a lot of built up cruft that I had not housecleaned otherwise.

If you have room, make a new / (root) partition and just install to that. If your /home is separate you can reuse that or it may be a good time to have a separate /home as with a separate /home or other data partitions your / only needs to be 10 to 25GB.

You will want to back everything up even if you have a separate /home.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by jpg123 on 2012-04-26
Im not sure what 'root' means, im not that literate on computers, what i was planning to do was burn 12.04 to a disc and boot it from there and overwrite 11.10, is that what you meant?

---

### Post by jpg123 on 2012-04-26
plus im trying to download it from ubuntu and its estimated to take more than 12 hours, so i may try it tomorrow.

---

### Post by Finalfantasykid on 2012-04-26
root is '/'
home '/home/'

When you are installing the OS, you can set up the mount points of your partitions, you will just specify what partition will be for what.

Here is a screenshot of what my partitions look like.  Notice how I have two partitions, one set up so that it will be mounted at '/', and the other so that it mounts to '/home/'.  Like oldfred said, the root partition doesn't have to be as big as your home, but for me, I decided to make them equal size.

---

