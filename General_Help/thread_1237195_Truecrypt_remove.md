---
title: "Truecrypt remove"
date: 2009-08-11
forum: General Help
---

### Post by Anybloodyid on 2009-08-11
Hi
I tried using truecrypt which worked fine with no problems.
Having tried it I now want to remove the container that I created, below are the instructions for doing this.
But I'm stuck at the start>  Right-click the 'Computer' (or 'My Computer') where is Computer?

> **How to Remove Encryption**

       Please note that TrueCrypt can in-place decrypt only system partitions and system drives (select System > Permanently Decrypt System Partition/Drive). If you need to remove encryption (e.g., if you no longer need encryption) from a non-system volume, please follow these steps:
       
[LIST=1]
[*]Mount your TrueCrypt volume.
[*] Move all files from the TrueCrypt volume to any location outside the TrueCrypt volume (note that the files will be decrypted on the fly).
[*]Dismount the TrueCrypt volume.
[*]If the TrueCrypt volume is file-hosted,    delete it (the container) just like you delete any other  file.
          
          If the volume is partition-hosted (applies also to USB flash drives),  in addition to the steps 1-3, do the following:
[LIST=1]
[*] Right-click the 'Computer' (or 'My Computer') icon on your desktop, or in the Start Menu, and select Manage. The 'Computer Management' window should appear.
[*]In the Computer Management window, from the list on the left, select 'Disk Management' (within the Storage sub-tree).
[*]Right-click the partition you want to decrypt and select 'Change Drive Letter and Paths'.
[*]The  'Change Drive Letter and Paths' window should appear. If no drive letter is displayed in the window, click Add. Otherwise, click Cancel. 
          If you clicked Add, then in the 'Add Drive Letter or Path' (which should have appeared), select a drive letter you want to assign to the partition  and click OK.
[*]In the Computer Management window, right-click the partition you want to decrypt  again and select Format. The Format window should appear.
[*]In the Format window, click OK. After the partition is formatted, it will no longer be required to mount it with TrueCrypt to be able to save or load files to/from the partition.
[/LIST]
         
[/LIST]


---

### Post by Soul-Sing on 2009-08-11
In dutch "locatie" = locations ===> computer?

---

### Post by Anybloodyid on 2009-09-23
Anybody got a better answer than the one given?

---

### Post by peculiar penguin on 2009-09-23
The instructions you quoted are for Windows (terms like "My Computer" or "Start Menu" should be dead giveaways).
If you created a file-based container then mount it, copy any data still inside to a safe location, unmount it, and delete the container file.
If you encrypted a partition, back up your data (see above), unmount it, and reformat the partition ([FONT=Courier New]sudo mkfs.ext3 <device>[/FONT] in a terminal, or install and use something like gparted if you need a GUI).

---

