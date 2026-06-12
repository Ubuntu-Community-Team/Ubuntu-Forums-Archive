---
title: "My Documents Shortcut Broken (fstab question)"
date: 2011-09-29
forum: General Help
---

### Post by trackmagic on 2011-09-29
This has been kind of an ongoing issue for me, but I have figured some stuff out so I thought I would start fresh with a new thread.

I am trying to add a "My Documents" link to my Ubuntu desktop that looks at my Windows XP partition's My Documents folder. I do this so I can access my files in both Ubuntu and Windows.

The issue I have is that every time I restart the link is broken until I click on the partition  in places and load it. (Then the link works)

Somebody dcstar suggested I load the Storage Device Manager to edit my fstab file since first I could not even get that to work.

The fstab seems to work now, but I still cant get my "My Documents" link to work at startup.

Any thoughts?
FYI: Here is the code from my fstab file:
/dev/sdb1                                  /media/windows  ntfs  defaults           0  0

---

### Post by staticd on 2011-09-29
/dev/sdb1                                  /media/windows  ntfs-3g  defaults           0  0

/media/windows will have to already exist for this to work. when you  mount using nautilus the directory is dynamically created and removed.

Unmount the windows partition.
 then do 
sudo mkdir /media/windows

---

