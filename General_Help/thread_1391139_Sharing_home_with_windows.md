---
title: "Sharing home with windows"
date: 2010-01-26
forum: General Help
---

### Post by J V on 2010-01-26
**It is possible to share your home folder with windows.**
Linux shortcuts (known as symlinks) act just like folders, so if a shortcut called shorty leads to randomfolder which contains test.txt, you can also access it with shorty/test.txt

Now, while windows has difficulty (At best) with accessing the Linux file system, you can still share your documents.

By replacing standard folders like Pictures with symlinks to /media/windowsdrive/Users/<yourname>/My Pictures etc, all files saved to pictures, will actually be saved to the windows drive, meaning you can access and modify your stuff from both windows and Linux.

Settings for some programs can also be linked, Firefox settings are similar on both OSs for example, so you could link your .mozilla folder to the similar location on your windows drive.

If you are trying to share your home between two Linux OSs, it becomes much easier.
All you have to do is put your home on a separate partition, which can be used for multiple OSs, and will make fresh installs much much easier.

(But that is beyond the scope of this guide)

**So how do I do it?**
Creating a link like this is very easy!

Middle-click drag a folder from your windows drive to your home and select "Link here"

Note that windows shortcuts won't work, the "My documents" shortcuts from windows won't work in Linux, so you should usually look under the "Users" folder to actually access your documents.

Shortcuts are easily recognizable by their extension (They end with .lnk)

Once you have done this, delete the corresponding home folder, and rename the link to that. (Capital letters matter!)

There you go, now your stuff will be saved to the windows account.

If you use a shared folder a lot, and you don't want to click on your windows drive in places every time you log on, you can [edit your fstab file]("https://help.ubuntu.com/community/Fstab") to automatically mount it.

**A word of warning to those with encrypted home directories!**
On windows, unless you specifically choose to encrypt something, it won't be encrypted, so an encrypted home will do you no good if you use this technique.

You can however create an encrypted private directory to store your more sensitive data, while the rest is freely available to both operating systems.

If you have an encrypted home directory, just create another folder and it will be encrypted.

This should be considered when linking your documents and/or settings to windows.

---

