---
title: "Advice"
date: 2010-10-14
forum: General Help
---

### Post by worthamtx on 2010-10-14
Presently have only windows on 149GB ntfs. Planning on installing ubuntu using wubi but would like to resize that 149GB to give me partition for saving files etc.
I know this is a gparted question but my past experience here was answers were quick. So here goes and thanks for helping.
When I put the gparted disk in it says size is 152625 Mib and upper and lower box on that screen is -0- What must I do to reduce that ntfs to about half. Those up and down arrows and space before and after confusing as all get out. Hey I am 80 not as sharp once was](*,)](*,)

---

### Post by sanderd17 on 2010-10-14
*If you use Win7, don't follow this and ask someone else. I don't know anything about win7.*


You want to divide your 150GB partition in half?
click on the green resize arrow. Then, you drag one side of the partition to the middle and click to accept the size change.

Look at the partition table and check if you see the same partition as there was, only taking half the space, and the other half "unallocated".

Check in the actions window (the most downside panel) that there is only one shrink action, not a delete action or so.

If that's all right, click on the green "V". If that isn't all right, close GParted without changing anything and try it again.

You now have one unformatted partition without data and one with windows.



Now your second problem: you want to use the new partition for data storage with wubi. I don't know if that is so easy. Since you're already repartitioning, you should better install a normal ubuntu intallation.

Please say what you want to do with windows and/or ubuntu before you continue with the partitioning. That way we can advise you other things, like a full dual boot with separate (semi) home partition.

---

### Post by Quackers on 2010-10-14
First thing defrag the Windows disk - twice is better.
Windows defrag is way too slow so use a free one like Auslogics Disk Defrag.
If you are using Windows Vista or Windows 7 go to Start and right-click on Computer > select Manage. In the screen that shows select Disk Management. This will give you a screen giving details of your disk layout.
Right-click on your Windows disk and select Shrink. A pop-up will appear giving details. The maximum available shrinkage will be written in that window. Just hit ok and it will take about 15 seconds to run. Voila! :-)

---

### Post by ssulaco on 2010-10-14
> **worthamtx said:**
> Presently have only windows on 149GB ntfs. Planning on installing ubuntu using wubi but would like to resize that 149GB to give me partition for saving files etc.

During the Wubi install,you  allocate the installation size....

---

### Post by pricetech on 2010-10-14
Whichever way you resize your windows partition, let windows run chkdisk.

---

