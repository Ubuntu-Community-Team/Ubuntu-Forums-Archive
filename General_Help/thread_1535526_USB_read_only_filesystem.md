---
title: "USB read only filesystem"
date: 2010-07-21
forum: General Help
---

### Post by Noorani on 2010-07-21
I plugged in my USb drive into my computer yesterday and tried to delete a folder. I was unable to do so and got the following message

Cannot move file to trash, do you want to delete immediately?
The file "my file" cannot be moved to the trash.
Show Details
Unable to create trashing info file: Read-only file system

So when I click on delete I get another error message:

Error while deleting.
There was an error deleting Case Study Database.
Show Details
Error removing file: Read-only file system

At this point I can only click on Skip, Skip All, or Cancel.

I have not changed anything on the stick recently so I dont know what is causing the problem.
Could anyone please tell me what is the cause of this and how I can solve this

---

### Post by dcstar on 2010-07-21
> **Noorani said:**
> I plugged in my USb drive into my computer yesterday and tried to delete a folder. I was unable to do so and got the following message

Cannot move file to trash, do you want to delete immediately?
The file "my file" cannot be moved to the trash.
Show Details
Unable to create trashing info file: Read-only file system

So when I click on delete I get another error message:

Error while deleting.
There was an error deleting Case Study Database.
Show Details
Error removing file: Read-only file system

At this point I can only click on Skip, Skip All, or Cancel.

I have not changed anything on the stick recently so I dont know what is causing the problem.
Could anyone please tell me what is the cause of this and how I can solve this

System-Administration-Disk Utility.

**Unmount** the Volume and then do a "**Check Filesystem**" on it.

---

### Post by starleaf1 on 2010-08-05
I have similar problem, but I know what might have caused mine.
 
Some moments ago, I plugged my drive into a computer with some strange data protection software. It turned my drive's filesystem into read only and now it cannot be mounted with write option. The problem is, the computer and the software that have caused this has... lost forever. Any solution?

---

### Post by deserthowler on 2010-08-06
> **starleaf1 said:**
> I have similar problem, but I know what might have caused mine.
 
Some moments ago, I plugged my drive into a computer with some strange data protection software. It turned my drive's filesystem into read only and now it cannot be mounted with write option. The problem is, the computer and the software that have caused this has... lost forever. Any solution?

Can you copy your data to your hard drive and reformat the USB drive?

This is a quick and dirty solution that worked for me.

Earl

---

### Post by starleaf1 on 2010-08-06
> **deserthowler said:**
> Can you copy your data to your hard drive and reformat the USB drive?
 
This is a quick and dirty solution that worked for me.
 
Earl
 
I can not format the USB drive. Formatting the USB drive results in "error: the filesystem is read-only". So does [FONT=Courier New][SIZE=2]dd[/SIZE][/FONT] command.
 
FSCK reports that the filesystem is *not* clean, but since it has been made read-only, it can't be fixed.

---

### Post by inameiname on 2010-08-06
That's weird that you can't even format it. Hopefully you are remembering to unmount before formatting. Once it's unmounted, there will be no issues with it being 'read-only' or whatever.

This damn 'read-only' thing arises from time to time, and there seems to be no fix other than to copy all that you can onto the computer and put it back after you reformat the drive. 

Typically, I unmount with disk utility, and then erase the whole thing using 'shred' in the terminal, and then formatting it with gparted. Always works for me.

---

### Post by gsoundsgood on 2010-08-19
> **dcstar said:**
> System-Administration-Disk Utility.

**Unmount** the Volume and then do a "**Check Filesystem**" on it.

this worked for me. thanks!

---

### Post by shezars on 2010-09-02
> **gsoundsgood said:**
> this worked for me. thanks!

yeah, that's fix it my problem :)

---

