---
title: "Terrible, terrible mistake I made!"
date: 2009-10-31
forum: General Help
---

### Post by cooperaaaron on 2009-10-31
I created a seperate home partition called Home and I backed up my old home folder and info there.  Somehow, someway, it created a folder call lost+found.  I moved the lost+found folder to the new home folder and now I don't have access to it, and I can not restore all of my files and settings !!  I need help !!!  Thanks in advance !

---

### Post by mac666 on 2009-10-31
If you access Lost and found as root (sudo), do you find any thing if you do a ls as sudo?

sudo cd /DIR
sudo ls


where /DIR is the folder...

---

### Post by wildweathel on 2009-10-31
Every UNIX filesystem has a folder called "lost+found."  It's used by the filesystem checker: if a filesystem becomes broken, fsck will try to undelete files and put the resulting recovered data there.  Normally, it will be locked, and you can't do anything to it, so I'm a little confused how you managed to move it.

But, even if you did, it shouldn't break anything.  It will just re-appear when that filesystem is next checked.  That's why I think something else happened.  Could you write a step-by-step description of what you did, starting with describing how you set up your partitions at install?  Even if it's not exact, that would be helpful.

---

### Post by cooperaaaron on 2009-11-01
Ok, first I created a Home partition.  Then I looked online for some more info. Came to a post on a site that said to rsync the old home folder to the new Home partition. Did that (hopefully I got that right, now I am NOT so sure). Watched the progress in the terminal.  Finished to see something in the Home patition.  Then I installed 9.10, all went well. So now I got back to the site and instructions that I found earlier.  Said to move the old home files off of the Home partition that I created to the new 9.10 home folder.  Did that, then thats where I see the lost+found folder pop up.

Now, the site says I have to change permissions on that old file info so I can have access, and nothing works.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif). I know I screwed up somewhere!  I should have taken the time to look here on this site instead !

---

### Post by cooperaaaron on 2009-11-01
And I just tried to cd to that lost+found, it says cd command not found when I try to access it.

---

### Post by cooperaaaron on 2009-11-01
Oh, wait a min, now it says I do not have permission to access that file, the lost+found

---

### Post by pdi180 on 2009-11-06
I made the exact same mistake. I followed the instructions from tomshardware.com's linux install guide, only I named the /home folder /Home. Now I have two home folders, but it won't let me migrate the folders over. I just got Ubuntu up and running.... I have the lost and found folder, but there is nothing in it. So now I have a /Home partition that has 170 gb and a /home partition with 30 gb and all the handy music, video, photo folders. Is the only way to fix this to re install Ubuntu? If so.... I am willing to accept my punishment for being foolish.

Thanks!

---

### Post by cooperaaaron on 2009-11-07
Looks like it will take some time for someone to help us out!

---

### Post by Barriehie on 2009-11-07
> **cooperaaaron said:**
> I created a seperate home partition called Home and I backed up my old home folder and info there.  Somehow, someway, it created a folder call lost+found.  I moved the lost+found folder to the new home folder and now I don't have access to it, and I can not restore all of my files and settings !!  I need help !!!  Thanks in advance !

Is your new home partition being mounted in /etc/fstab???  I have my /home on a different partition and I've got this in /etc/fstab to mount it at boot.

```

#
#       Mount my new home partition.
#
/dev/sdb2 /home ext3 rw,nodev,nosuid 0 2

```

Barrie

---

### Post by cooperaaaron on 2009-11-07
Yes, it is being mounted.

---

### Post by pdi180 on 2009-11-08
I have begun learning a little about Ubuntu - thanks to the sticky on the Ubuntu pocket guide, helps greatly - but I am still a little hesitant to pull the trigger. I am in the disk utility, and I have a partition of 206 gb , linux Ext3 partition 3, /dev/sda3 mounted at /Home. I am thinking to delete this partition and create a new one, but I don't want to mess things up beyond reason. Thanks for the help!

Paul

---

### Post by girto on 2009-11-08
type in terminal:
```
gksudo nautilus
```

Feel free to move files as you wish, but make sure you right click them and select properties to change the owner and permissions to your username in case they are now owned by root.

---

### Post by pdi180 on 2009-11-11
ok... thank you for the info. It took me a little to actually figure out what terminal was (sorry, it is new to me!) I made my user name have the rights to change things. But I just want to make sure this is correct. I am going to move the contents of the /home folder (the one which is currently acting as the normal home) and move it into the /Home folder (the one I accidentally created with a partition). and then delete the old /home folder. Sorry if this is confusing, I tried!

Thanks!

---

