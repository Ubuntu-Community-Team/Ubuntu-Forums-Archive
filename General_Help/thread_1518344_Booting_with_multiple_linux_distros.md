---
title: "Booting with multiple linux distros"
date: 2010-06-26
forum: General Help
---

### Post by Tikhon03 on 2010-06-26
This is a general question for people familiar with multiple linux distros.  My first distro was Ubuntu.  I have been trying to branch out and learn more about linux.  So I created several other partitions and installed Fedora, with / set to one of the new partitions and /home set to the same partition where ubuntu currently has /home set.  Now of course within home there are folders for different users.  Is there a way to synchronize them between different distros?  For example if I have /home/usr1 in Ubuntu, can I have usr1 in Fedora reference the same folder rather than say /home/Usr1, which is currently an empty folder.  Is this even a good idea?

---

### Post by dabl on 2010-06-26
There are potential problems with a shared /home folder -- if you're not totally committed to it, you might want to reconsider that approach.

PROBLEMS:  Desktop environments (Gnome, KDE, Xfce) write their own hidden "settings" folders in you user's home directory.  Moreover, so do application packages and some drivers, such as the proprietary Nvidia driver.  Use your file manager and click "View" > "Show Hidden" to see these.

So, the problems begin when your second (or third) OS provides a different version of a DE or package, and that one writes into the same hidden folder, and the settings info is inconsistent.  Over time, you'll have no end of fits trying to sort why applications are throwing goofy errors, crashing, and otherwise not behaving.

A better approach is to let each OS have its own /home directory within the root filesystem, and then save your data in separate disk partition(s) -- you can label them "MUSIC", "IMAGES", "VIDEOS", or whatever.  You make one directory on each such partition, named the same as the partition, and give it your user's permissions.  Then, you symlink those directories into the /home/user folder on each OS.  Doing it this way, there's no interference, and there's never a risk of loss of data should you decide to install your next distro over your last distro.   :p

---

### Post by malspa on 2010-06-26
I use separate /home partitions for each distro.

---

### Post by irv on 2010-06-26
Correct me if I am wrong, but can a person have a separate partition where you can store documents, photos, videos, etc. and just create a link to it from each home directory in each OS, and leave the home directory for individual OS's in tack? This way you will not have the problem with over-writing setting that are stored in the home directory. I do this with Ubuntu and Linux right now, and I do not have any problems.
No matter what OS I am in and I can access my files and can edit or create files without having to worry about the problems you mentioned.

---

### Post by malspa on 2010-06-26
> **irv said:**
> can a person have a separate partition where you can store documents, photos, videos, etc. and just create a link to it from each home directory in each OS, and leave the home directory for individual OS's in tack?

Yes, I do much the same thing, except I don't create a link to it.  I do have the directories bookmarked in Krusader and in Konqueror, in each distro, so I guess that amounts to the same thing.

---

### Post by Tikhon03 on 2010-06-26
Thank you for the very helpful comments.  Now I am wondering how much space each /home partition needs for the configuration files.

---

### Post by dabl on 2010-06-26
Unless you plan to put huge downloads into the user's home folder, 15GB should be plenty big for the complete filesystem of any Linux OS, including /home. Most distros initially install at 4 or 5GB, but grow with package additions and updates.

Also, a single swap partition on your system will be found and used by each OS.  So one swap partition is all you need (you can find many claims that it is unnecessary, but "choices have consequences" -- better to put one in and not have to write a forum post about how suspend to disk isn't working ...).

---

### Post by Tikhon03 on 2010-06-26
It sounds like you are suggesting that / and /home should be on the same partition. Currently I have them on separate partitions. Do you think I should change that?  Is there any real benefit one way or the other?

---

### Post by oldfred on 2010-06-26
When I converted to Lucid I created a new /home and then a new /data. After I moved all the data out of /home my home is only about 1GB and it has 3 years of hidden settings not housecleaned. But I do move anything data related like the hidden thunderbird and firefox settings out of /home to keep it small and have all data not in root or home.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Because I moved all the data folders from /home to /data, I now delete all the folders in my new install and link them all at once with one command.
for i in `echo /usr/local/fred/data/*`;do ln -s $i; done

I first did each but it took too much time.
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
etc

---

### Post by dabl on 2010-06-27
> **Tikhon03 said:**
> It sounds like you are suggesting that / and /home should be on the same partition. 


Yep.  Just as oldfred says.  :p

---

### Post by Tikhon03 on 2010-08-03
Thanks to all of you, for your helpful suggestions.  As I mentioned before, I previously had / and /home on different partitions.  So the first step was to backup my file system using tar, and repartition.  I then installed each operating system, with kubuntu installed last so that grub2 would pick up on all of the operating systems.  Using tar to recover my original file system saved me the trouble of having to totally reinstall all my programs (in kubuntu at least). To set up common access to a single data patition, I followed the method described in the blog post, [http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html), mentioned by oldfred.  I edited the fstab file using a gui editor, and the instructions to launch the editor depended on the OS.  In kubuntu I used
```

kdesudo kate /etc/fstab

```(in ubuntu kdesudo kate needs to be replaced by gksudo gedit). In most other distros the command was
```

dbus-launch kwrite /etc/fstab

```Now I have several operating systems running side by side.  As far as installation goes, Kubuntu and Fedora were by far the friendliest.  Open Suse struck me as just plain weird!  Even the commands were weird!  On the whole I would say this was a very good learning experience.

---

