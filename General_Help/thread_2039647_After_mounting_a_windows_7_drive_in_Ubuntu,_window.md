---
title: "After mounting a windows 7 drive in Ubuntu, windows won't start"
date: 2012-08-09
forum: General Help
---

### Post by quoitaapi on 2012-08-09
Hello,

I have a problem which I am now suspecting might have something to do with mounting a drive in Ubuntu.

My Ubuntu install is on an ESATA drive, so the system normally boots into w7 unless I choose the external drive to boot from.

Normally, I don't need to mount any other drives when using Ubuntu, but I have had three occasions where different drives have been made unreadable by windows and I am pretty sure that it occurred after I mounted the drive in Ubuntu.

What has happened recently is with the main w7 boot drive.  It starts to boot, but stalls at the point where the mouse pointer appears.  If I inspect the drive from Ubuntu, all the files seem to be present and correct.  If I try to view the drive from an external w7 boot disk, I get a read error message stating - drive not accessible. Access denied.  If I try right click drive and inspect the properties in w7, it shows a 0b disk with 0b free.

Has Ubuntu changed the security on the disk such that w7 cannot read it?  At the moment, this is the only thing I can think of.  If it has, can I reset the security beck to what it was some how?

I'd be grateful for any help as the drive has a lot of software on it.  Please treat me as a newbie on this, I have a very basic level of knowledge.

---

### Post by Kalanac on 2012-08-09
Try mounting the drive in ubuntu then unmounting it properly.  It might be that the drive has been sort of "locked open".  Mounting then unmounting should clear it if that's the case.

---

### Post by oldfred on 2012-08-09
Were you hibernated in Windows? Writing a file into Windows when it is hibernated can then corrupt the hibernation as some file was moved and it then cannot read that location.

Generally best to set Windows partition as read-only and create a shared NTFS partition for any data you want to share. Still best not to hibernate as if you have a shared file open in hibernation it can still be corrupted.

Also the Linux NTFS drive exposes all Windows files, like unhiding them in Windows. I used to always unhide everything in Windows but then clicked & moved to quickly and moved folders or files to another location corrupting things.

---

### Post by Kalanac on 2012-08-09
Urgh, hibernation is just a big bag of trouble.  I honestly don't know why people bother with it.

---

### Post by quoitaapi on 2012-08-13
Hello again,

Thanks for your suggestions.

As I had to install the NTFS driver in order to read the drive, I probably hadn't been accessing the drive before, and therefore the problem had nothing to do with Ubuntu - the solution might though.

Is there any software I can use in Ubuntu to reset the windows security of the drive?

If so, is there a better way to backup the drives contents first from Ubuntu, rather than use xcopy from a windows command prompt?

---

### Post by oldfred on 2012-08-13
Part of the reason I liked a shared NTFS data partition. But even then every Windows application did not let me change defaults to the d: drive. So I wrote a .bat file with several xcopy commands to copy anything else I wanted to backup when in Windows. Then it was a bit easier just to backup the entire NTFS data partition.

Also with the shared drive set read-write I change the Windows system partition to read-only. Then I did not have to worry so much about accidentally moving or deleting something important.

---

