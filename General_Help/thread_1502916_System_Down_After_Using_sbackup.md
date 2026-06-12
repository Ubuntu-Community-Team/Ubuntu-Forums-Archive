---
title: "System Down After Using sbackup"
date: 2010-06-06
forum: General Help
---

### Post by golfnut324 on 2010-06-06
Hello All - 
 
I really messed my system up! I installed and ran sbackup. As I recall the backup file was defaulted to /var/backup but I'm not sure. I left it in the default backup location. I went to bed and returned to find message that less than 2% of (I think it said) the partition was available. After analyzing hard disk and trying unsuccesfully to find/delete backup file, I decided to re-boot. Now it looks like I have some kind of GNOME problem because I get the foillowing message:
 
Install Problem!
The configuration defaults for GNOME Power Manager have not been installed. Please contact your system administrator.
 
And I can't log in. I have only been running Linux (Ubuntu) for 2 months so I need detailed instructions.
 
Thank you all in advance for any assistance.
 
Craig

---

### Post by bobcollard on 2010-06-06
> **golfnut324 said:**
> Hello All - 
 
I really messed my system up! I installed and ran sbackup. As I recall the backup file was defaulted to /var/backup but I'm not sure. I left it in the default backup location. I went to bed and returned to find message that less than 2% of (I think it said) the partition was available. After analyzing hard disk and trying unsuccesfully to find/delete backup file, I decided to re-boot. Now it looks like I have some kind of GNOME problem because I get the foillowing message:
 
Install Problem!
The configuration defaults for GNOME Power Manager have not been installed. Please contact your system administrator.
 
And I can't log in. I have only been running Linux (Ubuntu) for 2 months so I need detailed instructions.
 
Thank you all in advance for any assistance.
 
Craig
/var/backup is in your root directory.  I'm not sure how big your original partition was or how much you had to backup, but it is possible you have filled up your partition.  The files you want to remove is in your file system.  To do that you need root access.  You need to get into Terminal and enter ```
gksu "file manager"
```  where File Manager is thunar in my computer it may have another name on yours.  Then go to /file system/var/backup and open it to delete just the contents, not the folder.

---

### Post by golfnut324 on 2010-06-06
I will try that. Can you guide me on how to open Terminal since I can't seem to boot up? Is there a way to run it from a live cd?
 
Thanks.

---

### Post by bobcollard on 2010-06-06
> **golfnut324 said:**
> I will try that. Can you guide me on how to open Terminal since I can't seem to boot up? Is there a way to run it from a live cd?
 
Thanks.
Run Live CD, find Terminal under System, I think, it's been awhile since I used gnome.  In terminal use all lower case and no quotation marks.  If you get completely stuck you could reinstall the system from the live CD, however all your user files will be removed too.

---

### Post by golfnut324 on 2010-06-08
Problem Solved! Thanks for the help.

I ran live cd, navigated to the /var/backup folder and checked the properties on the folder. Turns out, since I was running live cd it had a path of:
/media/48f83b54-34d3-4412-a20b-d0bebe900ac1/var/backup

Then from terminal and signed in as sudo -s, I moved the directory to /home. From there I could delete all files using "rm -rf *"command. Then I used "rmdir" to remove the folder.

It seems that, since the root partition was totally maxed out, I couldn't delete it from there. I don't know for sure but it worked this way and my system is back.

I removed sbackup just to be sure it wasn't set to auto run and mess me up again.

Now looking for a good solution to auto run images of my drive.

Hope this helps someone.

Thank You!

---

### Post by bobcollard on 2010-06-09
> **golfnut324 said:**
> Problem Solved! Thanks for the help.

I ran live cd, navigated to the /var/backup folder and checked the properties on the folder. Turns out, since I was running live cd it had a path of:
/media/48f83b54-34d3-4412-a20b-d0bebe900ac1/var/backup

Then from terminal and signed in as sudo -s, I moved the directory to /home. From there I could delete all files using "rm -rf *"command. Then I used "rmdir" to remove the folder.

It seems that, since the root partition was totally maxed out, I couldn't delete it from there. I don't know for sure but it worked this way and my system is back.

I removed sbackup just to be sure it wasn't set to auto run and mess me up again.

Now looking for a good solution to auto run images of my drive.

Hope this helps someone.

Thank You!
Try wallpaper-tray or drapes in Synaptic Package Manager, search wallpaper will bring both up.  Glad you got it straightened out.  Next time you want to use sbackup specify a folder in another HD or another partition so you don't fill up the one with your system.  Use Quicklinks, top right of this page, to put Solved in your title.

---

