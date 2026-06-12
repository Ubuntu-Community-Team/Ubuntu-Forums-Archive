---
title: "unmount windows 7 partition permanent"
date: 2012-02-25
forum: General Help
---

### Post by matimont on 2012-02-25
Hi,

I installed ubuntu and selected to import everything, now I discovered it mounted the partition and I don't want that.

How can I unmount the partition permanently (so that next time I start up, is not there anymore)?

thank you!

Matias.

---

### Post by Gremlinzzz on 2012-02-25
Install GParted in Ubuntu
 Click the partition to edit in the main window and then click "Partition" from the top navigation bar. Click "Unmount" to unmount the partition, if mounted.

Click the "Apply" button on the top navigation bar to apply all pending changes.

---

### Post by Lars Noodén on 2012-02-25
You should be able to comment out that line in /etc/[fstab](http://manpages.ubuntu.com/manpages/oneiric/en/man5/fstab.5.html).  Do that by putting a hash (#) as the first character of the line you want "removed".  That way it is easy to undo the changes later if it is necessary.

---

### Post by matimont on 2012-02-25
> **Gremlinzzz said:**
> Install GParted in Ubuntu
 Click the partition to edit in the main window and then click "Partition" from the top navigation bar. Click "Unmount" to unmount the partition, if mounted.

Click the "Apply" button on the top navigation bar to apply all pending changes.


I tried that but after reboot, is still there. Actually if I unmount using gpart and then click on Home and the mounted drive, the files and folders it appears again.. any other suggestion?

thank you!

---

### Post by Mark Phelps on 2012-02-25
HOW did you install Ubuntu? Using Wubi? IF so, there is no way to unmount the Windows filesystem.

---

### Post by Morbius1 on 2012-02-25
I'm confused as to what is actually happening here.

Do you have an entry in fstab that mounts this partition at boot?

Or is there no entry and you want to prevent mounting it through Nautilus ( Home )?

If it's the former then put a # sign in front of the line as stated above. If it's the latter then add an entry into fstab and tell it not to automount:

[1] Create a mount point:
```
sudo mkdir /Win7
```[2] Add the following line to the end of /etc/fstab:
```
UUID=DA9056C19056A3B3 /Win7 ntfs defaults,noauto,umask=277 0 0
```[COLOR=Blue]Note[/COLOR]: To find the correct UUID number for your partition run the following command:
```
sudo blkid -c /dev/null
```[3] Run the following command to test for errors and execute the new fstab line:
```
sudo mount -a
```Edit: After reading Mark Phelps' post it never occurred to me that this is a Wubi install. I never used it so I was unaware that you could not prevent the mounting of the host partition.

---

### Post by matimont on 2012-02-26
> **Morbius1 said:**
> I'm confused as to what is actually happening here.
 
Do you have an entry in fstab that mounts this partition at boot?
 
Or is there no entry and you want to prevent mounting it through Nautilus ( Home )?
 
If it's the former then put a # sign in front of the line as stated above. If it's the latter then add an entry into fstab and tell it not to automount:
 
[1] Create a mount point:
```
sudo mkdir /Win7
```[2] Add the following line to the end of /etc/fstab:
```
UUID=DA9056C19056A3B3 /Win7 ntfs defaults,noauto,umask=277 0 0
```[COLOR=blue]Note[/COLOR]: To find the correct UUID number for your partition run the following command:
```
sudo blkid -c /dev/null
```[3] Run the following command to test for errors and execute the new fstab line:
```
sudo mount -a
```Edit: After reading Mark Phelps' post it never occurred to me that this is a Wubi install. I never used it so I was unaware that you could not prevent the mounting of the host partition.
 
 
When I installed ubuntu, I selected "import my documents from windows 7" during the installation process... I tried fstab and I can't see the mounted partition, I just see it in nautilus and there's an icon in the left bar..

---

