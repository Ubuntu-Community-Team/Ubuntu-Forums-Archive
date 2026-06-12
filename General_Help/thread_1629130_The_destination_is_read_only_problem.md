---
title: "The destination is read only problem"
date: 2010-11-23
forum: General Help
---

### Post by Crazy K on 2010-11-23
OK, I was going to put some music on my 500GB external HD, but for some reason it wont allow it. Everytime I try to put music in my music folder on my ex hd, it says "The destination is read only". 

I try to change it in the properties, but it gives me the same problem. 

How do I fix this? I use Ubuntu 10.04.

---

### Post by sikander3786 on 2010-11-23
You can either gain temporary access to that by running

```
gksudo nautilus
```

Or if you want to own that permanently,

```
sudo chown username:username /place/to/mount
```

Where username is your username and /place/to/mount is its mount point.

Good Luck!

---

### Post by Crazy K on 2010-11-23
How will it work when my ex hd is named "My Book"?

I keep getting errors like "can't access, no such file or directory.

---

### Post by Swagman on 2010-11-23
press left alt + F2 and enter gksudo nautilus

You will be able to gui to your destination.

or cd /path/"My Book"

---

### Post by Crazy K on 2010-11-23
Ok, I think I got it, I put "" around My Book and it seemed to work. 

Nope, it's still a read-only area.

---

### Post by Swagman on 2010-11-23
but is your dos prompt now pointing at the right place ?

That's all the command did that I gave you.

You will then need to sudo chmod 755 ( read, write, execute for owner)


**Warning.. Long time since I changed permissions in the cli.. do so at own risk or do some research on permissions**

---

### Post by WorMzy on 2010-11-23
How have you mounted it? What filesystem does it use? What is the output of "mount"?

---

### Post by Crazy K on 2010-11-23
This is what I got after putting that sudo chown in: 

changing ownership of `/media/My Book': Read-only file system

I go to my folder and nothing. 

I tried the gksudo nautalis and that didn't work either.

---

### Post by Crazy K on 2010-11-23
> **WorMzy said:**
> How have you mounted it? What filesystem does it use? What is the output of "mount"?

idk, It was originally used with Windows XP like 2 years ago, and has been used on Ubuntu ever since with no problems. Anyways it's Fat32 and is under the /dev/sdb1 partition or so it says on Gparted.

---

### Post by WorMzy on 2010-11-23
Unmount it, and run this command in the terminal:

```
sudo mount -t vfat -o rw,uid=1000,gid=1000,umask=000 /dev/sdb1 /mnt
```

You should then be able to access it from the /mnt directory, it should be owned by user 1000 (the first user you created), but everyone should have read, write and execute permissions.

If that works, then you can create an entry in fstab to have it use those mount options in the future.

---

### Post by Swagman on 2010-11-23
> **WorMzy said:**
> How have you mounted it? What filesystem does it use? What is the output of "mount"?

That's a good point. I assumed he had already mounted the drive.

Can you dir the drive 

```

paul@pauls-desktop:~$ cd ~
paul@pauls-desktop:~$ cd /media/Capture
paul@pauls-desktop:/media/Capture$ dir **<----**
AutumnPretty.jpg       jasmine\ on\ jack.vob  $RECYCLE.BIN
Blackin.jpeg	       kelly\ horse.osp       RECYCLER
CaptureDir	       kelly\ horse.vob       Share1Music
ffastun0.ffx	       Lucidshot.png	      System\ Volume\ Information
ffastun.ffa	       MSP7\ Preview\ Files   thumbnail
ffastun.ffl	       MspTEMP		      Ubuntu
ffastun.ffo	       MyWorks		      Ubuntu\ Stuff
Home-Folder	       Photos		      Videos
jasmine\ hw	       Photoshop	      Wayne
jasmine\ on\ jack.osp  pspbrwse.jbf	      Win7
paul@pauls-desktop:/media/Capture$

```

Capture is an 200gb NTFS drive on my system

---

### Post by Crazy K on 2010-11-23
Seems to be working now. Went through gksudo nautilus and went to unmount. Then left that, clicked on my book, decided to click on safely remove drive (but gave me some error that I can't do that) and then I noticed I could delete files and such again, so it's working. But I don't know for how long. We'll see. Unless I just had to wait a while for the sudo chown script to work.

I'll keep this thread active just in case it happens again. Cause I have a feeling it might do it again.

---

### Post by SeijiSensei on 2010-11-23
If you have a Windows machine available, I'd run chkdsk or whatever Windows uses these days to check the drive for errors.  Usually when a device is mounted read-only it's because mount has detected errors in the filesystem.

You can try checking it from Ubuntu if it's a DOS or FAT32 drive.  I prefer letting Windows deal with NTFS, but maybe I'm just being paranoid.  Plus, according to "man ntfsfix," the ntfsfix utility in Linux is not as thorough as the equivalent utility in Windows itself.

If it is FAT32, try running "sudo fsck -t vfat /dev/sdb1" if that's the partition that you're mounting.

---

### Post by Crazy K on 2010-11-23
> **Swagman said:**
> That's a good point. I assumed he had already mounted the drive.

Can you dir the drive 

```

paul@pauls-desktop:~$ cd ~
paul@pauls-desktop:~$ cd /media/Capture
paul@pauls-desktop:/media/Capture$ dir **<----**
AutumnPretty.jpg       jasmine\ on\ jack.vob  $RECYCLE.BIN
Blackin.jpeg	       kelly\ horse.osp       RECYCLER
CaptureDir	       kelly\ horse.vob       Share1Music
ffastun0.ffx	       Lucidshot.png	      System\ Volume\ Information
ffastun.ffa	       MSP7\ Preview\ Files   thumbnail
ffastun.ffl	       MspTEMP		      Ubuntu
ffastun.ffo	       MyWorks		      Ubuntu\ Stuff
Home-Folder	       Photos		      Videos
jasmine\ hw	       Photoshop	      Wayne
jasmine\ on\ jack.osp  pspbrwse.jbf	      Win7
paul@pauls-desktop:/media/Capture$

```

Capture is an 200gb NTFS drive on my system

Here you go: 

```
crazyk@crazyk-desktop:~$ cd ~
crazyk@crazyk-desktop:~$ cd /media/"My Book"
crazyk@crazyk-desktop:/media/My Book$ dir <----
bash: ----: No such file or directory
crazyk@crazyk-desktop:/media/My Book$ dir
autorun		      Fam\ pics\ and\ ****	   ppop.odt
autorun.inf	      Fotc\ Stuff		   Recycled
bookmarkschrome.html  Hellraiser\ Hellblazer.flac  Setup.exe
bookmarks.html	      My\ Music			   System\ Volume\ Information
Controller_files      My\ Videos		   wd_mac_tools
Controller.html       Photos1			   wd_windows_tools
Documents	      porrr.txt
crazyk@crazyk-desktop:/media/My Book$ my music

```

---

### Post by Crazy K on 2010-11-23
> **SeijiSensei said:**
> If you have a Windows machine available, I'd run chkdsk or whatever Windows uses these days to check the drive for errors.  Usually when a device is mounted read-only it's because mount has detected errors in the filesystem.

You can try checking it from Ubuntu if it's a DOS or FAT32 drive.  I prefer letting Windows deal with NTFS, but maybe I'm just being paranoid.  Plus, according to "man ntfsfix," the ntfsfix utility in Linux is not as thorough as the equivalent utility in Windows itself.

If it is FAT32, try running "sudo fsck -t vfat /dev/sdb1" if that's the partition that you're mounting.

So what do I do when I type in sudo fsck and so on?

---

### Post by Crazy K on 2010-12-19
Hi again. My External HD keeps doing this. I have to keep safely removing the drive and then plugging it back in. I need help guys.

---

### Post by dinesh2n on 2011-11-29
> **WorMzy said:**
> Unmount it, and run this command in the terminal:

```
sudo mount -t vfat -o rw,uid=1000,gid=1000,umask=000 /dev/sdb1 /mnt
```



Thanks that  works ...
After mounting it /mnt , I can copy it and then format the pen drive again and then pen drive works as usual....

---

### Post by Crazy K on 2012-10-08
Hi again guys, I'd like to come back to this. I recently upgraded to Xubuntu 12.04 from Ubuntu 10.04 and I'm having similar problems to this. I have to manually mount the EX HDD. 

I checked out some sites and saw some tutorials, but it didn't work for me. I need step-by-step help on this. I would follow the previous steps, but I'd like to start from the beginning.

---

