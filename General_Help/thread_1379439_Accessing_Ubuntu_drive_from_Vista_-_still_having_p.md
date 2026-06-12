---
title: "Accessing Ubuntu drive from Vista - still having problems!"
date: 2010-01-12
forum: General Help
---

### Post by Gareth973 on 2010-01-12
I know this is a common issue, but I’ve searched existing threads on this and other forums and can’t find any answers to my particular problems.
 
I’m new to Linux and have just installed Ubuntu Netbook Remix 9.10 on my laptop, on a separate partition to Vista (32bit, Home Premium, Service Pack 1).  I’m looking for a way of reading my Ubuntu files from within Vista, for the odd time that I’ve forgotten to store the document I need to my USB stick.  I only need read access (as I can always copy them back to Ubuntu from within Ubuntu, which works fine).
 
I’ve tried several different programs/drivers for this:  Explore2FS, Ext2FSD 1.11a (and v1.11), Ext2IFS and DiskInternals Linux Reader.  I’ve tried installing them normally, in Windows XP SP2 compatibility mode, and as administrator, but none of them will work properly (details below).  I’ve tried installing them all separately (so they shouldn’t be interfering with each other).  Am I missing something really obvious here???!!! 
 
DiskInternals Linux Reader:
Shows the Linux partition (and swap partition), but won’t open it.  No error messages – it just doesn’t seem to do anything.  Tried manually typing in a known good file path in the address bar, but still does nothing.  (Gives an error when trying to open the Vista drive too, but not sure if that’s normal).
 
Explore2FS:
When loaded in XP mode it shows just one partition (which I assume is Linux) in the left-hand tree window, but when opening it, it appears to be empty.  In normal installation mode, there’s nothing there at all.
 
Ext2FSD and Ext2IFS:
Both of these allow me to assign a drive letter to the Linux partition and mount it.  The drive appears in “My Computer” and shows the first level of files and folders on the Linux drive.  However, whenever I open a sub folder (eg /home to get at my documents), it just tells me the folder is empty.  I tried re-installing, but then it told me I would need to format the Linux drive before I could open it.  Tried running the “mountdiag” programme suggested on the Ext2IFS website, but that didn’t seem to do anything.
 
Any help would be appreciated!
Thanks,
Gareth

---

### Post by Puck7 on 2010-01-12
If you installed the latest 9.10 Ubuntu Netbook Remix then you're running on ext4. Currently there is no software for Windows to read ext4 partitions.

It would be probably smart to create a partition that would be read by Ubuntu and by Windows also (FAT32 type). Or you could mount your Windows partition in Ubuntu and save files there.

---

### Post by Gareth973 on 2010-01-12
Puck7,
Aha - that explains it!

I tend to save most of my work to a removable USB stick (which is FAT formatted), and should save anything Vista-specific directly to the Vista drive anyway.  It's just sod's law that the one file I will need when in Vista is the one I saved to the Ubuntu documents by mistake, so just wanted an easy way of getting to it.  Guess I'll just have to wait until someone more talented than me releases a an ext4 driver!

Very many thanks for your help in putting me straight!
Gareth

---

### Post by Puck7 on 2010-01-12
My pleasure of helping (:

About the waiting.. would be better to setup your system with a drive that can be read by both, as I said before, you'd find it much more convenient and wouldn't matter where you are, you'd have your files. With symlinks you can use the same folder for Pictures, Documents, Music and Videos.

---

