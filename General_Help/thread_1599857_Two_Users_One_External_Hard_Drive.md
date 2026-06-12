---
title: "Two Users One External Hard Drive"
date: 2010-10-18
forum: General Help
---

### Post by Lacho on 2010-10-18
Hi,

Just got a WD Elements 2TB External Hard Drive for my home computer (Ubuntu Lucid)in which I will load all the media files (pics, music, video), it mounted automatically to my user, no problem, but I have two questions:

1.) I can see that it has some stuff on root level, an autorun folder, a System Volume Information folder, and an autorun.inf file. Do I leave them there? Or do I delete them?

2.) **The marriage saver question**. My wife cannot access the drive, even though it does appear as a folder with an "x mark" inside her media folder of the filesystem, but she gets something like she does not have sufficient user privileges or something like that.

So how do I make it so that she can also access the drive, or certain folders of the drive, which would be an even better option as the backup stuff would be inaccessible to her.

Thanks

---

### Post by Earl_Maroon on 2010-10-18
Those files on the root of the disk are for Windows. They can be deleted, but Windows will recreate them every time the drive is used on that OS. You'd be better just to ignore them.

As for your wife being unable to access the drive, this is a permissions problem. As you can access the drive, your user account is probably recognised as the owner of the drive, therefore you should be able to set the file/folder permissions by logging in yourself. Find the drive in Nautilus and right click. In properties there should be the option to change permissions. These options should be pretty self-explanatory, but what you need to do is allow your wife's account read and write access and apply to enclosed files. If you don't want her to have full access, find the folder you do want her to have access to and change the permissions on that instead.

---

### Post by Lacho on 2010-10-18
Earl_Maroon,

Thanks for the prompt reply, I just tried your suggestion, right-clicked the Elements icon on the desktop, but the Permissions tab says "The Permissions of "Elements" Could not be determined" and there is no other option.

So, I went to the Media folder where the drive mounts and right-clicked, went to the Permissions Tab, and tried to change the drop-down menu for Folder Access under Others, and as soon as it rolls back, it changes back to None, so the change does not stick. I also tried the same for several folders inside the drive, same as before.

What am I missing?

---

