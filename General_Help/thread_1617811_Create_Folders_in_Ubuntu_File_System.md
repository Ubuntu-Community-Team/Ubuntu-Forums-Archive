---
title: "Create Folders in Ubuntu File System"
date: 2010-11-09
forum: General Help
---

### Post by aplusguy on 2010-11-09
I am new to Linux, so I have much to learn.  I have set up a dual boot system with Windows XP and Ubuntu 9.10.  I have upgraded Ubuntu to the most current version available online.  

The problem I am having is I'm unable to create folders or subfolders in the Linux file system.  I have researched the manual and my Unbuntu Linux book, and see that I should be able to click on 'File' from the menu, then 'Create Folder', and then input the new folder name, but the 'Create Folder' selection is 'grayed' out which I conclude means that it is set on inactive and unable to be used.  I am able to access my Windows disk by mounting and then typing in my password, so I have Administrator privelidges.  I'm able to create a new folder in Unbuntu Linux for my Windows (NTFS) files.  When I installed Unbuntu, I did not see any options to have write access to the Ubuntu file system.  I can create new files within the existing folders.

Soon after working out my Linux problems, I will be using PHP/MySQL/Apache to do some important work, so I will need to be able to create new folders and subfolders in my Linux system.  Does anyone have any ideas that would help?  I have some urgent tasks I need to do away from my PC soon, so I will be a while before getting back to this.  In the meantime, any help will be greatly appreciated.  

Don G.

---

### Post by holiday on 2010-11-09
> **aplusguy said:**
> I am new to Linux, so I have much to learn.  I have set up a dual boot system with Windows XP and Ubuntu 9.10.  I have upgraded Ubuntu to the most current version available online.  

The problem I am having is I'm unable to create folders or subfolders in the Linux file system.  I have researched the manual and my Unbuntu Linux book, and see that I should be able to click on 'File' from the menu, then 'Create Folder', and then input the new folder name, but the 'Create Folder' selection is 'grayed' out which I conclude means that it is set on inactive and unable to be used.  I am able to access my Windows disk by mounting and then typing in my password, so I have Administrator privelidges.  I'm able to create a new folder in Unbuntu Linux for my Windows (NTFS) files.  When I installed Unbuntu, I did not see any options to have write access to the Ubuntu file system.  I can create new files within the existing folders.

Soon after working out my Linux problems, I will be using PHP/MySQL/Apache to do some important work, so I will need to be able to create new folders and subfolders in my Linux system.  Does anyone have any ideas that would help?  I have some urgent tasks I need to do away from my PC soon, so I will be a while before getting back to this.  In the meantime, any help will be greatly appreciated.  

Don G.

It depends on where you want to create the new folder. Even though your user has admin privileges, it doesn't have root access, doesn't have access to the entire file system. Some folders are owned by another user - often root - and you have to BE root to change that folder's contents. 

Try navigating to your home folder. /home/<yourusername>. Can you create a folder there?

---

