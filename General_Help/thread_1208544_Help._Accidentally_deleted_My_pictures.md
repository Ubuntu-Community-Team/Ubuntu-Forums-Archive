---
title: "Help. Accidentally deleted My pictures"
date: 2009-07-09
forum: General Help
---

### Post by Hexagon on 2009-07-09
My workstation-computer recently got unstable, and I wanted to make a backup of the /home folder. I booted the source computer with Ubuntu 9.04 LiveCD (as the original 8.10 install was not stable) and connected it to a laptop running windows (I'm sorry). I shared the /home folder in ubuntu, and then installed 2 samba files.

I wanted to backup the "My pictures" drawer first, as it was the most important drawer. The connection was interrupted at about 75% (maybe due to wireless). I wanted to delete the incomplete "My pictures" drawer, as I would re-try with a new transfer on direct cable. However, I accidentally deleted the source "My pictures" folder instead of destination :(

I was not worried at first, as I did **not** do a shift-delete, and I did not get any warning when the folder was deleted. I imagined the folder was moved to trash. I was however not able to find the folder in trash??

Neither by the trash-icon, or in /home/.local/shared/trash/files ??

Maybe it's because I'm running from LiveCD?
Where is the files, or are they permanently deleted without any pop-up "are you sure" or warning box?

Please help me to recover my pictures. I do have the incomplete directory, and I did stop the delete process, but 1.1GB of personal pictures is still lost...

---

### Post by lsemmens on 2009-07-09
An Ultimate Boot CD (google UBCD)should give you some utilities for recovering deleted files. Just don't try and do anything else on that drive in the meantime.

---

### Post by Hexagon on 2009-07-09
I have not booted from the harddrive since I deleted the folder, only been running from LiveCD. I suppose this is a good thing.

I suppose the folder with pictures have been moved to trash somewhere, or does somebody know that it gets deleted permanently when running LiveCD??

Regarding the recovery tools on the Boot-CD, I will only get all pictures in one directory, and all picture names are lost...

---

### Post by niteshifter on 2009-07-09
Hi,

I'm pretty sure the Live CD put in a trash folder, the question is where on the hard drive you had mounted it is. 

While running the live cd open Terminal and try this:
```
find /media/disk -name Trash -type d
```
Change /media/disk to what you've the hard drive mounted as. If the above gets you nothing try .Trash for the name.

---

### Post by Hexagon on 2009-07-09
Thanks for your replies!!

find "/media/disk-1 -name Trash -type d" gave 2 results;
/media/disk-1/root/.local/share/Trash
/media/disk-1/home/hexagon/.local/share/Trash

None of those 2 directories contain any pictures or folders. Only some old deleted programs.

Searching for .Trash gave 0 results.

---

### Post by Hexagon on 2009-07-09
I tried to search for *.jpg on the harddrive as well. Did not find any of the missing pictures.

I suppose I can conlude that a simple delete within the "File Browser" or Nautilus is a permanent delete, atleast running Ubuntu 9.04 LiveCD. No warnings given either. I know It's my fault, but I am a bit dissapointed.

Running default Ext3 gives no recovery options either, which saves folders and filenames :(

---

### Post by niteshifter on 2009-07-09
Hi,

One last idea, then I give up. Look for /media/disk-1/.Trash-Ubuntu

---

### Post by az on 2009-07-09
You can use file carving to recover deleted files.  Start with photorec.  You can tell photorec to only use the unallocated space, which should narrow down the rescued files to those which have been deleted.


You can then rename them according to their exif data:

jhead -n%Y%m%d-%H%M%S *.jpg

---

### Post by bear24rw on 2009-07-09
im suprised no one has mentioned photorec yet, it is the best tool ive found for recovering files you can find it in the repositories

[edit] install the package testdisk to get photorec

---

### Post by Hexagon on 2009-07-09
> **niteshifter said:**
> Hi,

One last idea, then I give up. Look for /media/disk-1/.Trash-Ubuntu

I did a search for *rash* as well, and only the previous two directories showed. No .Trash-Ubuntu.

I did another quick test on a different partition. I deleted a file while running LiveCD. The directory .Trash-0 was created in root of that disk, with the deleted file inside. In other words, when I stopped the delete process, I also "stopped" the files from being "pasted" in any Trash-directory.

---

### Post by Hexagon on 2009-07-09
> **az said:**
> You can use file carving to recover deleted files.  Start with photorec.  You can tell photorec to only use the unallocated space, which should narrow down the rescued files to those which have been deleted.


You can then rename them according to their exif data:

jhead -n%Y%m%d-%H%M%S *.jpg

I tried foremost and got alot of pictures without any names, only numbers. Would take quite a bit of time sorting them out. If I can narrow these down to only the deleted ones, It would help alot. I will try photorec.

I'm sorry, but what is exif data?

---

### Post by Hexagon on 2009-07-09
> **bear24rw said:**
> im suprised no one has mentioned photorec yet, it is the best tool ive found for recovering files you can find it in the repositories

[edit] install the package testdisk to get photorec

I'm installing testdisk now, thanks!

---

### Post by az on 2009-07-10
> **Hexagon said:**
> I tried foremost and got alot of pictures without any names, only numbers. Would take quite a bit of time sorting them out. If I can narrow these down to only the deleted ones, It would help alot. I will try photorec.

I'm sorry, but what is exif data?

A jpeg file contains information about the the jpeg withing itself.  Jhead will be able to read each file and rename it according to the date in the exif data, for example.  So that means you can have all your jpegs renamed by the date they were taken.

---

