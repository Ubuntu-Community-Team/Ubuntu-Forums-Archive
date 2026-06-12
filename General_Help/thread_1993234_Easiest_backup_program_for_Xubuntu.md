---
title: "Easiest backup program for Xubuntu"
date: 2012-06-01
forum: General Help
---

### Post by Wuxin on 2012-06-01
I just installed the recent edition of Xubuntu and would like to know what is the best and easiest to use backup program for this distro?  I have an external hard drive which I use for the purpose of backing up.  I know there are several backup programs out there but if someone can advise me on one to use, I would appreciate it.  Thanks in advance!

---

### Post by flemur13013 on 2012-06-01
Probably "rsync" with it's GUI = "grsync".

---

### Post by ajgreeny on 2012-06-01
> **flemur13013 said:**
> Probably "rsync" with it's GUI = "grsync".
+1

Simple, effective, and after the first time of use, is quick as it only copies new and changed files.

---

### Post by Wuxin on 2012-06-01
Thanks for these...so it sounds like grsync is a good way to go.  How does this compare with SBackup, another one I've seen people talk about?

---

### Post by CrusaderAD on 2012-06-01
Not sure if it's still around, but "keep" is a great backup program.

---

### Post by Wuxin on 2012-06-02
Okay...I downloaded grsync and ran it by simply copying my hard drive onto my external drive--that took quite a long time!   What I have, in effect, is a mirror image of my computer's hard drive on the external drive.  From here, how do I qualify the backup so that it only copies those additions or changes made since the previous backup?  In other words, what do I put in the "source" box and what in the "destination" box?  I have a feeling I may have copied too much unnecessary material in doing a full disk backup.  It may be too late, but what is essential to be backed up?

---

### Post by ajgreeny on 2012-06-03
Personally I back up everything in my /home, and the only change I have made to the standard, apart from exclusions (see below) is to select to "Preserve permissions", as I backup to an ext3 partition which means linux permissions are enabled with no problems.  If you backup to a fat32 partition, permissions are lost.

By default grsync will only copy changed files and folders on subsequent runs, so you should not need to make any specific changes to the setup.  You can, however, exclude any specific folders if you wish, and I do that for all the various cache folders in my home by making a simple text file called excludecache.txt and then in the Advanced tab of grsync adding the line ```
--exclude-from=/home/*user*/excludecache.txt
``` to the box in that tab.  That saves quite a lot of time copying the many ephemeral files from caches that are probably not wanted as backups.  My excludecache file is attached for you to use if you want.

Try another run of grsync and you will probably find that it finishes very quickly this time, as most files will not be copied across.

---

### Post by Wuxin on 2012-06-04
Thanks so much--very good reply!  So it isn't necessary then to backup absolutely everything on the primary hard drive?  (I may have blown it here...I think I did that!) Is there a way I can now delete some of the extraneous stuff I transferred onto the backup
drive?  My backup drive is large, but why clutter it with useless material?  Do I need to wipe the drive clean and start over, or is there a way I can keep the essential stuff and eliminate everything else?  Thank you again!

---

### Post by ajgreeny on 2012-06-04
> **Wuxin said:**
> My backup drive is large, but why clutter it with useless material?  Do I need to wipe the drive clean and start over, or is there a way I can keep the essential stuff and eliminate everything else?  Thank you again!
I see no point in backing up everything on the drive as it is so quick to reinstall ubuntu from scratch, and my personal files in /home are most important to me.

Now you can either delete the extraneous folders from the backup and just keep your home folders, or more easily, I think delete the whole backup now and start again.

In the source box of grsync put /home/user/ and in the destination box put /media/diskname/foldername/ not forgetting the trailing /, though if I remember right there is a search facility for each of those two boxes which makes it all very simple.

---

### Post by Wuxin on 2012-06-04
Thanks so much!  Excellent replies one and all.  Appreciate the kind help.

---

