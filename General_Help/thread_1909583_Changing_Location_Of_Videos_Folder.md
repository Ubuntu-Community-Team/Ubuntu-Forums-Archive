---
title: "Changing Location Of Videos Folder"
date: 2012-01-15
forum: General Help
---

### Post by Kreeyon on 2012-01-15
I have a second hard drive installed in my desktop that I use purely for Music And Movies, the drive that Ubuntu is installed onto isn't a big enough drive to store media on and also like to keep media stuff separate anyway.

My question is:  Is it possible to have the Videos folders that is part of the Ubuntu file-system be replaced with the videos folder from a second drive instead as it's easier to store and access the videos folder from the Ubuntu file-system but obviously would like to make use of the extra space available on the second drive.

I hope this makes sense?

---

### Post by toyoracer on 2012-01-15
Yes just went through this. Make a link from /home/Videos 

Works great. Follow oldfred's post
[http://ubuntuforums.org/showpost.php?p=11081384&postcount=4](http://ubuntuforums.org/showpost.php?p=11081384&postcount=4)

---

### Post by Kreeyon on 2012-01-16
Thanks for the reply.

I managed to sort it out after by changing the mount point of my second hard drive to mount inside the home/videos folder.

The only problem I have now; which is the same problem I experience with all additional hard drives or external USB drives, is that all drives have their own trash folder.  Coming from a Windows background this I'm finding a little annoying as I'm used to pressing delete on an item and it would automatically delete the item from the drive and place it into the main system trash folder, but on Ubuntu I seem to have a dedicated trash folder on the secondary hard drive itself occupying space.

Is there a way to have this trash folder on my second drive deleted so that all files deleted on this drive will be sent to the main system trash folder instead?

---

### Post by Wayne_V on 2012-01-16
Are you sure you want to do that?   Any video you then delete will be copied to your main drive - it will take a long time to delete *and* take up space on your main drive.   Maybe you just want to bypass the trash?

> Permanently delete a file
You can immediately delete a file permanently, without having to send it to the trash first.
Select the item you want to delete.
Press and hold the Shift key, then press the Delete key on your keyboard.
Because you cannot undo this, you will be asked to confirm that you want to delete the file or folder.
If you frequently need to delete files without using the trash (for example, if you often work with sensitive data), you can add a Delete entry to the right-click menu for files and folders. Click Edit &#9656; Preferences and select the Behavior tab. Select Include a Delete command that bypasses Trash.

---

### Post by Kreeyon on 2012-01-16
> **Wayne_V said:**
> Are you sure you want to do that?   Any video you then delete will be copied to your main drive - it will take a long time to delete *and* take up space on your main drive.   Maybe you just want to bypass the trash?

That's a good point.  Keep forgetting about the shift key for a permanent delete. Will have to break the windows habit of deleting things.

thanks

---

