---
title: "Convert ext. harddrive from Fat32 to NTFS?"
date: 2011-04-11
forum: General Help
---

### Post by mathiasdk on 2011-04-11
1. Is this possible without loosing the data on the external harddrive?
2. How is it done?
3. WIll I be able to read and write on both Ubuntu and OS X 10.6? (like I can now)

Thanks in advance!

---

### Post by bodhi.zazen on 2011-04-11
Copy all the data from the hard drive somewhere else.

Format the drive to NTFS (will destroy all the data on the drive) 

Restore data from backup.

I do not know of a non-destructive process to convert fat -> ntfs

---

### Post by coffeecat on 2011-04-11
> **bodhi.zazen said:**
> I do not know of a non-destructive process to convert fat -> ntfs

Amazingly, there is:

[http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

[http://www.ntfs.com/quest3.htm](http://www.ntfs.com/quest3.htm)

However, @mathiasdk don't go there. I did once. It was not a happy experience. The "converted" NTFS filesystem was usable in Windows but not on a non-Windows device. I agree with bodhi.zazen - backup, reformat and copy back.

But another however. OSX 10.6 will not write to NTFS out of the box. You will need to install the MacOS ntfs-3g driver if you want to write to NTFS in OSX. But it is much slower than the ntfs-3g Linux driver.

If you are not concerned about the 4GB filesize limit in FAT32, you may be better off staying with FAT32 if you want a filesystem compatible with Windows, Ubuntu and OSX.

---

### Post by mathiasdk on 2011-04-11
Thanks for the quick help. My only problem is exately that I need to transfer lager video files (over 4GB), so I'll need to convert anyway. Too bad.

What if I format the external harddrive in OS X in the "Mac OS Extended (journaled)"-format. Will my Ubuntu machine read and write on that format?

---

### Post by TeoBigusGeekus on 2011-04-11
Just a thought:
If less than half the drive is full, then create a new ntfs partition from the free space, move all your data in there, format the rest of the drive to ntfs and finally merge the two partitions...

---

### Post by coffeecat on 2011-04-11
> **mathiasdk said:**
> 
What if I format the external harddrive in OS X in the "Mac OS Extended (journaled)"-format. Will my Ubuntu machine read and write on that format?

Aha! Good thinking, but not quite. You'll need to use the non-journalled version of HFS+ (Mac OS Extended). Ubuntu can only read the journalled version but can read and write to the non-journalled version.

And there's another potential problem - permissions. MacOS uses the same system of Unix permissions as Linux and, of course, HFS+ supports those same permissions. Your OSX UID will be 501 (probably) and your Ubuntu UID 1000. You'll get all sorts of access denied errors until you address this one. My quick fix? Easy.

Format your drive with the non-journalled filesystem in MacOS. Now plug it into Ubuntu and let it be automounted. When the Nautilus window opens press ctrl-L to reveal the mount path. The breadcrumb trail will change to '/media/something'. Take a note of the 'something'.

Now open a terminal and:

```
sudo chmod 777 /media/something
```Obviously change the 'something'. That takes advantage of a little-known feature in Unix filesystems. You can own or chmod the root of the filesystem. Once you've done that, you will be able to access files in both OSs whoever the files are owned by.

And as a bonus, you can do exactly the same in MacOS instead if you want. MacOS mounts external drives in /Volumes. In a OSX terminal:

```
sudo chmod 777 /Volumes/something
```

---

### Post by bodhi.zazen on 2011-04-11
> **coffeecat said:**
> Amazingly, there is:

It was not a happy experience.

I have not tried the conversion, but that is what I have heard of the process as well.

---

### Post by CharlesA on 2011-04-11
> **bodhi.zazen said:**
> I have not tried the conversion, but that is what I have heard of the process as well.
Done the conversion with that command and didn't have any problems with it being read on Linux or Windows.

---

