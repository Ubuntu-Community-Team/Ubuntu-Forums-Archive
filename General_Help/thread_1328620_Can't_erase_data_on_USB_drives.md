---
title: "Can't erase data on USB drives"
date: 2009-11-16
forum: General Help
---

### Post by aj_the_first on 2009-11-16
I am having a problem with USB drives.  I can save data to them, but I can not erase data from them.  when I erase the data, it creates and sends the data to an invisible "trash" folder on the drive.  The "trash" folder is only invisible to Ubuntu, but not to windows, so I have to take the USB drive to a windows computer in order to truly get it cleaned.

In windows the files appear in a folder called trash(insert long meaningless extension to folder name here), so it is obviously being created by Ubuntu when I erase the files.
Even when I plug the device back into my Ubuntu computer without erasing it in windows, it still appears empty on the Ubuntu computer (9.04) and all the files appear in windows.  However, when I open the device properties in ubuntu, it shows me how much of the device is used up with files, it just shows no files or folders on the device.  

How can I completely erase things on a USB drive?  I would prefer a non-terminal solution.

It really sucks to have to keep a windows computer around for this simple stuff...  I want to be windows-free in my life, but as long as stuff like this keeps popping up, I have to keep a spare windows machine around for "convenience"

---

### Post by Junosix on 2009-11-16
Press Ctrl-H and you can see the hidden trash folder.

---

### Post by albannach1 on 2009-11-16
Or, in Nautilus:

View -> Show hidden files

Ctrl-H is the keyboard shortcut.

Also, when you empty the trash in Ubuntu, it will empty the trash folders on the USB drive as well.

---

### Post by aj_the_first on 2009-11-16
Thanks!
Is there any way to make ubuntu immediately erase the data on USB drives instead of creating a hidden trash folder and sending it there and then having to show hidden files and re-erase them?

---

### Post by MonoDeem on 2009-11-16
> **aj_the_first said:**
> Thanks!
Is there any way to make ubuntu immediately erase the data on USB drives instead of creating a hidden trash folder and sending it there and then having to show hidden files and re-erase them?

[COLOR=Blue]Shift + Delete[/COLOR]

---

### Post by audiomick on 2009-11-16
Are you de-mounting the drive properly before you take it out? I always get asked if I want to empty the trash first

---

