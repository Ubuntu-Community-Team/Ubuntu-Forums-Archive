---
title: "Trash icon still shows full when empty"
date: 2010-07-02
forum: General Help
---

### Post by Werm on 2010-07-02
Hello! 

Well I'll start off with the recent changes I've made. I have three hard drives in my PC, two of which are formated NTFS. I recently installed Storage Device Manager and changed a few options around so they auto-mount of start up. Well when I did this, and wanted to delete files off those drives, I suddenly was being promoted that I must delete them permanently or not all at (wouldn't go into the trash)

I added the lines to FSTAB: uid=1000,gid=1000 0 1

So for example my secondary drive is: 

nls=iso8859-1,umask=000,uid=1000,gid=1000,0,1

And also added .Trash-1000 folders in each of the two NTFS drives.

When I delete items off one of the two NTFS disks they go to the trash... I don't get the "delete forever" prompt and I can actually see them in the trash bin.

But when I empty the trash the icon remains that of the "full" trash, despite when I open it there being no trash in it. 

Any ideas? Thanks!

---

### Post by SoFl W on 2010-07-02
I think the OS will create the ".Trash-1000" if it needs to.  Perhaps the trash is confused because it didn't create them?  Try deleting them and see what happens. 
Of course I know just enough to get us both in trouble, try at your own risk.

---

### Post by 4Orbs on 2010-07-02
Or, if you don't mind using a rather crude, barbaric solution... Install the Thunar File Manager and use it when you need to delete files or empty trash from those other hard drives. Thunar manages trash the way trash should be managed.

---

