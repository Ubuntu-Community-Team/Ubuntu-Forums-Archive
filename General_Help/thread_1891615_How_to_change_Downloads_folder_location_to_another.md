---
title: "How to change Downloads folder location to another partition"
date: 2011-12-06
forum: General Help
---

### Post by andrey_ on 2011-12-06
Hi, 

I need to keep my data on a partition other than the system's one, so that I'll be able to restore my system easily and quickly (with the help of Clonezilla). 

So, how to change the location of the "Downloads" folder to another partition? also /home/andrey/.local/share/TpLogger/logs , /home/andrey/.purple/logs which are the  Piding and Skype's logs folders.

Ubuntu 11.04.

Thanks in advance

---

### Post by DapperMe17 on 2011-12-06
Create a "Downloads" folder on the alternative partition, then make sure you change your browser's perferences, in order to point to the new folder.

---

### Post by papibe on 2011-12-06
In general you want to move all your user files (/home) to a different partition or disk. Check this [tutorial]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

Regards.

---

### Post by grvsaxena419 on 2011-12-06
Hello andrey_ , you can use linux symbolic link to  do that. 
just create a directory in your other partition where you want to keep them and create a symbolic link using 
```
ln -s  <target> <link-name>
```
see man ln for more details, target would be the name of directory you created above and link-name would be the directory where your logs are currently stored.

Also for Downloads you can use the edit bookmark option from nautilus Bookmarks menu and then edit location of downloads folder.

---

### Post by andrey_ on 2011-12-06
How fast ! Thanks for your reply

---

### Post by andrey_ on 2011-12-06
> **papibe said:**
> In general you want to move all your user files (/home) to a different partition or disk. Check this [tutorial]("https://help.ubuntu.com/community/Partitioning/Home/Moving").

Regards.

Thanks, but I need to move only those folders which I mentioned above :(

---

### Post by andrey_ on 2011-12-06
> **DapperMe17 said:**
> Create a "Downloads" folder on the alternative partition, then make sure you change your browser's perferences, in order to point to the new folder.

Thank you, this will solve only the Download folders issue, any idea about the rest?

---

### Post by andrey_ on 2011-12-06
> **grvsaxena419 said:**
> Hello andrey_ , you can use linux symbolic link to  do that. 
just create a directory in your other partition where you want to keep them and create a symbolic link using 
```
ln -s  <target> <link-name>
```see man ln for more details, target would be the name of directory you created above and link-name would be the directory where your logs are currently stored.

Also for Downloads you can use the edit bookmark option from nautilus Bookmarks menu and then edit location of downloads folder.

Thanks for your replay grvsaxena419, 

Symbolic link will great a shortcut inside the folder only and that doesn't help, with regards to Nautilus Bookmark that changes the shortcut only but not the target location. 

any suggestions?

---

### Post by WorBlux on 2011-12-06
> **andrey_ said:**
> Thanks for your replay grvsaxena419, 

Symbolic link will great a shortcut inside the folder only and that doesn't help, with regards to Nautilus Bookmark that changes the shortcut only but not the target location. 

any suggestions?

Move the folder first, and then name the soft link the same as what the folder.

cd ~
mv Downloads /mnt/new-place/Downloads
ln -s /mnt/new-place/Downloads Downloads

---

### Post by andrey_ on 2011-12-06
> **WorBlux said:**
> Move the folder first, and then name the soft link the same as what the folder.

cd ~
mv Downloads /mnt/new-place/Downloads
ln -s /mnt/new-place/Downloads Downloads

Great, thank you, it's clear now :)

---

