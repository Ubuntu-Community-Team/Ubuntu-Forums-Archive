---
title: "OS drive is full - help needed"
date: 2009-10-18
forum: General Help
---

### Post by frazerr on 2009-10-18
Hi.  I have Jaunty installed on a 4GB drive, and my home folder on another 16GB drive.

My 4GB drive is now full.
What will happen if I try to add new software?
What is the best solution?
Can I move some folders over to the other drive? Do I need to repartion it and mount, or can I just make sym links?

I did not expect the  OS to be bigger than 4gb and I wanted to keep it all on a separate drive to my personal data. 

Any suggestions?

---

### Post by SuperSonic4 on 2009-10-18
A. Buy more space
B. Delete some files

A is obvious

B - Look in and possibly clear /var/cache or wherever ubuntu keeps it's packages. You can use ls -sh to see what's taking up room.

You can move some folders over and create symlinks but I've never tried it myself - I wouldn't try it before fstab is actioned on boot

---

### Post by diablo75 on 2009-10-18
You should have no problems resizing your partitions using a gparted Live CD.  You can download it from here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by PorkyPie on 2009-10-18
> **frazerr said:**
> Hi.  I have Jaunty installed on a 4GB drive, and my home folder on another 16GB drive.

My 4GB drive is now full.
What will happen if I try to add new software?
What is the best solution?
Can I move some folders over to the other drive? Do I need to repartion it and mount, or can I just make sym links?

I did not expect the  OS to be bigger than 4gb and I wanted to keep it all on a separate drive to my personal data. 

Any suggestions?

I suggest you go to System -> Administration -> Computer Janitor. It will help free space.

---

### Post by frazerr on 2009-10-18
thanks everyone, but...

super sonic - I have more space - its just on the wrong drive
and thanks for the var/cache/apt/archives that freed 2MB - doesnt really solve my problem though 

diablo - thanks I will use this if I need to repartition

proky pie - the computer janitor is not there

any other answers out there?

---

### Post by cariboo on 2009-10-18
Check /var/log for large log files, there is a thread in ABT where the poster has a problem with oversized log files. Have a look [here]("http://ubuntuforums.org/showthread.php?t=1284691").

---

### Post by frazerr on 2009-10-18
here is a run down of the sizes of different folders

usr:  2.7 GB
proc: 900MB
sys:  540MB
var:  280MB
lib:  200MB

everything else is less than 10mb

I dont know how that all fits on a 4GB drive, but oh well

so I go back to my first question about moving some of it to my second drive

---

### Post by PorkyPie on 2009-10-18
> **frazerr said:**
> thanks everyone, but...

super sonic - I have more space - its just on the wrong drive
and thanks for the var/cache/apt/archives that freed 2MB - doesnt really solve my problem though 

diablo - thanks I will use this if I need to repartition

proky pie - the computer janitor is not there

any other answers out there?

Sorry, try ALT+F2 then run

```
computer-janitor
```

---

### Post by jward3010 on 2009-10-18
Well, my answer is temporary as well.

**1.**```
sudo apt-get autoremove
```
**2.**```
sudo apt-get autoclean
```
It may remove a lot, it may not. Quickest solution is a resizing of your partitions, and you can actually use your Ubuntu live disk / USB to do it. GParted is on it when in Live mode. Make your root larger and your home smaller.

If you're thinking about spanning volumes then you need to look into LVM and possibly using the alternate disk (but it's also possible from the command). I've NO experience with LVM and regardless, you shouldn't really span your root directory. It should be big enough. I go for 5GB usually and keep the system pretty clean. Mostly my installs never go beyond 2.9GB, have you a lot of apps installed? Apps can come with a lot of barely used libraries so getting rid of something that you think is even small might result in a few hundered meg being saved.

---

### Post by ajgreeny on 2009-10-18
For speed next time use ```
sudo apt-get clean
``` to remove all your downloaded packages.

Are you sure there were only 2Mb of packages in there?  It seems such a small amount, I can only imagine you have not updated at all since installing.
> here is a run down of the sizes of different folders

usr:  2.7 GB
proc: 900MB
sys:  540MB
var:  280MB
lib:  200MB

everything else is less than 10mb

I dont know how that all fits on a 4GB drive, but oh well

so I go back to my first question about moving some of it to my second drive 	Not in any simple manner I'm afraid.  It is possible to do so if you set up separate partitions for some of those system folders at install time, but I doubt it's worth the hassle to do it afterwards, and I'm not even sure whether it's possible at that stage.

---

### Post by jward3010 on 2009-10-18
Oh, of course. Clear your Firefox temporary crap etc. That can hit a few 100MB's if not done in a LONG time.

---

### Post by nerdopolis on 2009-10-18
Another idea, is if you got a larger drive, you can do a union mount between the 4gb, and the new drive. (or you can do a union mount with a folder on your 10 gb device using AUFS. AUFS uses folders as the 'volume' not a device or loop file like ext3 or other 'normal' filesystems)

I'll try to describe it.

What a union mount does is take two (or more) folders, as the source fs. It merges them in a mountpoint. With a AUFS, you can specify multiple folders to union mount. Some can be read only, and some can be writable.

the way a union mount works is if you had two folders, and one was read only, and one was writeable with AUFS
if you read a file, it will refer it from the read only one, 

if you write a file, it will write it to the writable one. 

if you overwrite a file thats on the read only one, it will create the file on the writable one, and from then on that file will be read from the writeable one. not the read only one. 

if you delete a file thats on the read only one, it creates a hidden file on the writable one that tells aufs the file is deleted.

 the syntax for mounting aufs looks sort of like this (after you install aufs. its avalibe in the ubuntu packages) 
sudo mount -t aufs -o br:/rw_folder:/ro_folder none /aufs_mountpoint


However using aufs for your root partition will involve editing initrd scripts, and that means you have to make sure other partitions get mounted in the correct order, such as the home folder, and procfs after you mount the AUFS union mount.

---

### Post by Arquis on 2009-10-18
Use Bleachbit. It automates the cleaning process. [http://bleachbit.sourceforge.net](http://bleachbit.sourceforge.net)

---

### Post by frazerr on 2009-10-19
Hi every one.  thanks for all the suggestions.

quick responses:

I already had ran apt-get clean

I dont have computer-janitor because this was originally ubuntu netbook remix

my 2 partitions are 2 separate hard drives.  
I dont think LVM or union mount sound easy enough or suit my situation


can I copy some things from /usr/lib or /usr/share to my other drive and then symlink to them?
I know I copied /etc/bin/firefox  somewhere else and symlinked to it

thanks every one for all your suggestions

---

### Post by tabibito on 2009-10-19
Perhaps you would also want to try to clean up your thumbnails cache. It's in your ~/.thumbnails/ folder.

---

### Post by jward3010 on 2009-10-19
Uninstall some apps. When you run out of hd space there is no easy way about it to be honest. You've obviously got quite a few intensive ones installed, as I know, a clean updated Ubuntu with ubuntu-restricted-extras, easytag, soundconverter, a few more apps etc. etc. and a little bit of browsing down takes up around 2.9GB. You've obviously a lot installed. 

```
sudo apt-get remove program-name
```

Realistically, consider a reinstall and a giving yourself more room to breathe next time.

---

### Post by PorkyPie on 2009-10-21
> **frazerr said:**
> Hi every one.  thanks for all the suggestions.

quick responses:

I already had ran apt-get clean

I dont have computer-janitor because this was originally ubuntu netbook remix

my 2 partitions are 2 separate hard drives.  
I dont think LVM or union mount sound easy enough or suit my situation


can I copy some things from /usr/lib or /usr/share to my other drive and then symlink to them?
I know I copied /etc/bin/firefox  somewhere else and symlinked to it

thanks every one for all your suggestions

Sorry, didn't know that you had Netbook Remix :)

Do this in the terminal:
```
sudo apt-get install computer-janitor
```

It should install. Then you whould find it in Administraion -> Computer Janitor

If not, do ALT + F2 and type in computer-janitor.

Clearing Firefox's cache/browsing history (or any browser for that matter) is another way to clear a lot of rubbish.

---

### Post by jward3010 on 2009-10-21
Depending on how much space he's got left, he should install or not. Often it doesn't do a great job. I think "sudo apt-get autoremove / autoclean" basically do the same thing.

---

