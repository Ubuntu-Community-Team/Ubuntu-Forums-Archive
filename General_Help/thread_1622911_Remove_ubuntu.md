---
title: "Remove ubuntu"
date: 2010-11-16
forum: General Help
---

### Post by Drenriza on 2010-11-16
I have a co-worker that needs to remove his ubuntu partition, that is besides a Windows 7 pro partition.

How do i delete ubuntu without damaging his windows or mbr?
Once this is done i then need to resize his windows partition with the x-tra disk space. What is a good way to do this?

Thanks on advance.
Kind regards.

---

### Post by TNT1 on 2010-11-16
Use a windows disk utility?

---

### Post by sky_ceiling on 2010-11-16
1.Download and run EasyBCD in your Windows 7 partition to restore the Windows bootloader

2.Restart and boot to a Linux LiveCD to access the Ubuntu partition. Preferably one that has GParted on it, like the official Ubuntu disk.

3. Go to system>administration>GParted partition editor

4. Select your Ubuntu partition, right click and press format. In the pop-up box, choose the file system to 'Unallocated'

 **Optional** - select your Windows partition, then select 'Move/Resize' and expand it to fill the resulting amount of free space.

5. Click apply and wait. Restart and you now have an exclusively Windows computer


Sad to see your friend go :(

---

### Post by mastablasta on 2010-11-16
@ sky_ceiling - most complicated guide for deleting a partition i ever saw....
 
simply run fixmbr in windows (or from windows CD) and then use windows disk utility and delete the ubuntu partition. the space will be aded to the windows partition.

---

### Post by karthick87 on 2010-11-16
The easiest way is Logon to your windows.Right click **My Computer**--->Choose **Manage,**Goto **Disk management**.And delete the ubuntu partition.To resize, use partition magic.

---

### Post by Gordonbp531 on 2010-11-16
> **mastablasta said:**
> 
 
simply run fixmbr in windows 

Doesn't work with the new version of Grub. The EasyBCD app is the way to go.
What the OP doesn't need to do is to then boot up using a live CD - Windows has it's own built-in partition manager.

---

### Post by Gordonbp531 on 2010-11-16
> **karthick87 said:**
> To resize, use partition magic.

Don't even need that. If the Ubuntu partition was to the right of the Windows partition then just use the Windows Disk management tool...

---

