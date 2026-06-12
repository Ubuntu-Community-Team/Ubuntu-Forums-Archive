---
title: "In urgent need of help"
date: 2010-10-30
forum: General Help
---

### Post by newperson on 2010-10-30
I put a MicroSD card in to a card reader, it's from a Nokia mobile phone, and then plugged that in to the USB port.

For some reason I can't delete certain files. I am assuming my phone has some kind of virus.

Ubuntu refuses to let me access, modify or delete the files that are in the music folder but clearly not music files.

So I tried to open the folder with Wine to try and delete it the windows way (I have no idea if that was even supposed to work) and I get an error message that says 'File not Found' in a typical windows error display box.

Now I am having the exact same problem trying to open my home folder from the places menu. The same error pops up.

How do I switch Wine off?

Please advise, this is horrible!

All I want to do is clear a MicroSD card and put new music on it.

Also, I am the only user on this computer, and I have administrator privileges, and I cannot access the root folder or the lost-found folder.

Please help!

Thanks guys.

---

### Post by Verbeck on 2010-10-30
to revert the wine issue : create an empty folder on the desktop, right click it and select open with other application. from there, select file browser and check the option 'remember this application for folder files'

as for not being able to delete the files on the card, maybe its mounted as read only. could you post the output of **mount** from a terminal?

on a side note: wine doesn't open folders, only windows executables

---

### Post by newperson on 2010-10-30
I put a empty folder on the desktop, but if I double click it it opens fine and I can access my home folder through that, but if I do it the proper way and click places then home, I still get the error message.

I just fixed that by selecting open with file browser.

Thanks. 

Also, I think they are read only, but I'm not sure of how to change the attributes, it seems to always change back.

How do I access the 'root' directory and the 'lost-found' directory also?

I think I need root access, as when I try and mount the card through the terminal it says 'only root can do that'.

I only have one user account on this computer and it is me with administrator access.

What now?

---

### Post by Verbeck on 2010-10-30
to run a command as root put **sudo** in front of it. for example, to open the file browser as root, type **sudo nautilus **
also you do not need to access the root and lost+found directory. however, you can by opening the file browser as root but its not advisable to do so

---

### Post by newperson on 2010-10-30
Is there a way of doing all this without using the terminal?

I would just like to be able to browse folders and delete everything and not be told that the only user account on this machine which has administrator privileges is not able to perform all tasks as it lacks permissions to do so.

I am now confused. 

So do I go to the terminal then type sudo mount "name of drive" and then what do I do?

Thanks.

---

### Post by newperson on 2010-10-30
I'm pretty sure there's a self executing virus on there (the MicroSD from the Nokia).

How do I format a drive? It's via USB and if I format it it would probably work better.

Sorry for not being good at this stuff.

---

### Post by newperson on 2010-10-30
Ok I did sudo Nautilus and am now in the file manager as root, however I still can't delete the files. There is no option to delete the files and there is no option to move them to trash.

---

### Post by Verbeck on 2010-10-30
if you dont want to do terminal work then the most easy way is to format it
you can format a drive using System>administration>disk utility.
if its mounted, select unmount ,then format volume. most of the time FAT is the best for memory cards

also
the 1st user (the default user)is not root
 read up [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info
 
 to mount a device the syntex is **mount /dev/sdxx /mount/point** where sdxx is the device name and /mount/point is which folder into which you want to mount the device

---

### Post by newperson on 2010-10-30
Thanks so much for that. I formatted it and it seems to be working great.

So if I ever want to run as root, I just go to the terminal and type sudo root and that is how I do it?

I really appreciate your help.

---

### Post by Verbeck on 2010-10-30
> **newperson said:**
> Thanks so much for that. I formatted it and it seems to be working great.

So if I ever want to run as root, I just go to the terminal and type sudo root and that is how I do it?

I really appreciate your help.
yep. but don't run each and every program by sudo for simple tasks, it defeats the purpose of having the root account locked by default.  if you're confused, read up [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

 and remember to mark your thread as solved if the issue is fixed. see thread tools at the top

---

### Post by newperson on 2010-10-30
No problem.

So I should just run nautilus as root if I ever need to?

What kind of reasons would I actually need to ever run as a root user for, anyway? Consider I can install and am supposed to be able to delete with Administrator privileges.

---

### Post by Swagman on 2010-10-30
No reasons to run as root at all.

That's why sudo exists. To **temporarily** elevate your privileges to **administer** your system.

Instead of opening a terminal you can always press alt +F2 and type sudo nautilus

---

### Post by Verbeck on 2010-10-30
everything outside of you /home/<usr name> is owned by root so if you're doing some system customisations then you would often need to run a program as sudo which will elevate your privileges temporarily

for example, some times you may need to edit a file owned by root (example : /etc/fstab) in which case you should run sudo gedit /etc/fstab. 

it's all explained in the documentation link posted before

---

