---
title: "Reformatting an external harddrive"
date: 2010-05-06
forum: General Help
---

### Post by Ron W on 2010-05-06
Hello

I have a Seagate Expansion external drive.

It won't load as it is NTFS. Am I okay to reformat it using GParted? I'm unable to get the drive up in a window, but GParted can see it.

Thanks

Ron

---

### Post by AgentZ86 on 2010-05-06
> **Ron W said:**
> Hello

I have a Seagate Expansion external drive.

It won't load as it is NTFS. Am I okay to reformat it using GParted? I'm unable to get the drive up in a window, but GParted can see it.

Thanks

Ron

It should load as NTFS unless it's corrupted or something

also you can use Gparted to reformat or to check and manage the disk and it might repair any corruptions so the disk becomes readable again.

Anyhow just make sure you unmount the USB disk so you can access it for formatting / check/managing etc. 

I hope this helps

Happy computing.
:guitar:

---

### Post by ajgreeny on 2010-05-06
Have you connected the drive to a windows computer and then pulled it out without using the *Remove safely* option in the status bar?  If you have done so, linux will not be able to mount it as it will be marked as "File system still in use".

You can overcome that by force mounting, but it is better to connect it again to windows and remove it correctly.  It should then be accessible in linux as normal.

---

