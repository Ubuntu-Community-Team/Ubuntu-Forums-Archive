---
title: "Dual Boot Shared Partition"
date: 2009-12-01
forum: General Help
---

### Post by lvc on 2009-12-01
I am attempting to set up a dual-boot Ubuntu/XP system on my laptop, which has a 30GB harddrive. Because of this small amount of space, I am aiming to partition it as 10GB for the operating systems and swap space, and the remaining 20GB shared between them. This is to be mounted on linux as /home, and have tweaks done to XP using, eg, powertoys so that it uses it for its equivalent user directories. 
However, the way I intend to use my home directory, I need to be able to run executable shell scripts from it, but in many cases runnig these as 'sh foo' instead of './foo' isn't an option (because they are to be run from the GUI, particularly in the context of ROX-Filer's AppDirs). This implies that I need a filesystem with support for the execute permission, but which can be read and written from both Linux and XP.
I found a page (since lost) suggesting that NTFS is capable of this, and that NTFS-3g will behave properly when chmod-ing, but this doesn't seem to be the case: it defaults to mounting with all permissions as 777, and chmod -x on a file fails.
I have also tried the ext2IFS driver for Windows, but it tells me that the partition 'is not formatted', and offers to format it for me. I have seen advice that this is a known issue with the driver being imcompatible with some of the settings that newer Ubuntus use for ext3. 
I have also considered the reiserfs driver for Windows, but I have seen advice that this fails to work, and the driver appears to be unmaintained. 

Would NTFS-3g work with an extra mount option? Could the ext2IFS be made to work by changing the relevant ext2/3 options for the filesystem (are there any major disadvantages to this?)?    
Are there any other possible solutions?

---

### Post by oldfred on 2009-12-01
/home has to be a linux file system ie ext2, ext3 or ext4 normally. It cannot be NTFS or FAT as they do not support all the linux features.

When I first mounted my NTFS partition in fstab everything was executable. I am not sure what setting I had but I changed them so now .txt is not executable.

---

### Post by blueridgedog on 2009-12-01
I recommend your 20 gig partition be mounted in a custom location as it will need to be formated ntfs.  When I had a shared drive, I mounted it as /documents.  This worked and allowed Ubuntu to have a proper /home.  You can then make links to /documents from inside your /home folder.

---

### Post by Mark Phelps on 2009-12-02
Trying to share your /home partition with MS Windows is a very bad idea.  MS Windows doesn't understand the intricacies of Linux filesystem permissions, and any changes you make inside MS Windows to files in your /home partition are risking filesystem corruption.

As to Ext2ifs, the "newer" Ubuntu's use Ext4 filesystem which, from what I last read, Ext2ifs can't handle.

Your best results will be obtained if you leave /home alone and only use it inside Ubuntu and create a separate NTFS-formatted partition for sharing data.

And if you do that, be sure to install the ntfsprogs package.

---

