---
title: "Unable to save to flash"
date: 2009-08-13
forum: General Help
---

### Post by oxf on 2009-08-13
Can someone tell me why I am unable to save files to one of my flash drives when I can to the rest? The one in question is a 1GB Sandisk with plenty of empty space on it.  Theres no write-protect on it so cant be that. All the rest of my USB flash drives I can save to just fine  :confused:

Thanks

---

### Post by oxf on 2009-08-13
I'm wondering if tis is some sort of permission issue?
Also its formated FAT32 as purchased

---

### Post by oxf on 2009-08-13
Bump

---

### Post by michy99 on 2009-08-13
What is the output of this command? (With the flash plugged in)```
ls -l /media
```

---

### Post by tgeer43 on 2009-08-13
> **oxf said:**
> Can someone tell me why I am unable to save files to one of my flash drives when I can to the rest? The one in question is a 1GB Sandisk with plenty of empty space on it.  Theres no write-protect on it so cant be that. All the rest of my USB flash drives I can save to just fine  :confused:
It might help to know just what happens when you try. If you are trying to save with some sort of GUI app and there's no indication of what's going wrong, try copying a file to it from the command line and see if it spits out an error message.

tgeer

---

### Post by oxf on 2009-08-13
> **michy99 said:**
> What is the output of this command? (With the flash plugged in)```
ls -l /media
```
Thanks for replying!
Here the output:

mbdb@M2000:~$ ls -l /media
total 20
lrwxrwxrwx  1 root root     6 2009-06-27 22:05 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-06-27 22:05 cdrom0
drwx------ 16 mbdb root 16384 1970-01-01 01:00 disk
mbdb@M2000:~$

---

### Post by michy99 on 2009-08-13
Try this:```
sudo chmod 777 /media/disk
```

---

### Post by oxf on 2009-08-13
> **michy99 said:**
> Try this:```
sudo chmod 777 /media/disk
```

mbdb@M2000:~$ ls -l /media
total 20
lrwxrwxrwx  1 root root     6 2009-06-27 22:05 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-06-27 22:05 cdrom0
drwx------ 16 mbdb root 16384 1970-01-01 01:00 disk
mbdb@M2000:~$ sudo chmod 777 /media/disk
[sudo] password for mbdb: 
chmod: changing permissions of `/media/disk': Read-only file system
mbdb@M2000:~$ 

When I try and save an html file to the USB flash it says:
"could not be saved, because an unknown error occurred.
Try saving to a different location"

If I try to save by right clicking > save when I go to the flash there is no paste option available. Maybe I should try from the command line as tgeer sugested but I need you to give me the command
Thanks

---

### Post by prem1er on 2009-08-13
> **oxf said:**
> 
If I try to save by right clicking > save when I go to the flash there is no paste option available. Maybe I should try from the command line as tgeer sugested but I need you to give me the command
Thanks

```
cp /path/to/file /media/disk
```

Change '/path/to/file' to the actual location of the file you want to move.  If you are copying an entire directory you need to do


```
cp -r /path/to/file /media/disk
```

---

### Post by michy99 on 2009-08-13
For some reason, Ubuntu see the drive as read-only. Have you tried it on a different computer, or in Windows if you have it on this computer?

---

### Post by oxf on 2009-08-13
> **michy99 said:**
> For some reason, Ubuntu see the drive as read-only. Have you tried it on a different computer, or in Windows if you have it on this computer?

I'm pretty sure it works fine in Win XP. But I'll try it again and confirm and report back later
Thanks

---

### Post by oxf on 2009-08-13
> **prem1er said:**
> ```
cp /path/to/file /media/disk
```Change '/path/to/file' to the actual location of the file you want to move.  If you are copying an entire directory you need to do


```
cp -r /path/to/file /media/disk
```

Thanks premi1er!
Same result!  Will now check out it out widows.....sigh!

mbdb@M2000:~$ cp /home/mbdb/img_0977.jpg /media/disk
cp: cannot create regular file `/media/disk/img_0977.jpg': Read-only file system
mbdb@M2000:~$

---

### Post by oxf on 2009-08-13
> **michy99 said:**
> For some reason, Ubuntu see the drive as read-only. Have you tried it on a different computer, or in Windows if you have it on this computer?

OK its the same problem on another PC too. The flash is being perceived as read only.

When I boot into Windows XP I can save to the flash just fine. And I also checked other flash drives as well and they save OK. So what ever the problem is it would appear to be this particular flash. If  there was a tab on the flash to write protect it that would explain it but there isn't! :confused:

---

### Post by transmition on 2009-08-13
While this isn't the most tech savvy reply, have you tried re-formating the USB drive (after backing up the data of course :P)

This would make it just like all the other *working* flash drives, in my opinion.

---

### Post by oxf on 2009-08-13
> **transmition said:**
> While this isn't the most tech savvy reply, have you tried re-formating the USB drive (after backing up the data of course :P)

This would make it just like all the other *working* flash drives, in my opinion.

Hmmm? good point! No I haven't, only because I've never had this problem before with my other ones. I guess if no one comes up with any other whiz bang ideas I'll have to try that tomorow.

---

### Post by oxf on 2009-08-14
> **transmition said:**
> While this isn't the most tech savvy reply, have you tried re-formating the USB drive (after backing up the data of course :P)

This would make it just like all the other *working* flash drives, in my opinion.

Well Thanks! :) I re-formated it with FAT32 and now I can copy to it from Linux Why I dont know. The only clue is that there was one old file that I had previously deleted off of it and which when copying gave me an error msg that it was corrupted even though it was gone. So I have to presume that had "something" to do with it.

---

