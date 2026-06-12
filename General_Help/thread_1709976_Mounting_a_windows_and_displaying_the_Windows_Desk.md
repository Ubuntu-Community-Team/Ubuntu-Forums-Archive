---
title: "Mounting a windows and displaying the Windows Desktop"
date: 2011-03-19
forum: General Help
---

### Post by mahela007 on 2011-03-19
Hello everybody. 
Here's the situation: 
I have a windows PC which I would like to dual boot with Ubuntu. However, I have some very important documents scattered all over the "My Documents" folder. I don't want to move these to the linux partition manually because of the possibility of misplacing, deleting or otherwise doing something that could alter these files. 
(They happen to be notes that I make on Biology).

My plan was to mount the windows partitions on Ubuntu and then use symbolic links to navigate to the "My Docs" folder on the windows partition. 

This is the main question: 
It is possible to mount hard drives and then make an existing folder on Ubuntu (for example the /home/user/Documents folder)point to the "MY DOCUMENTS" folder on windows? 
(By "point to" I mean something like a symbolic link. So, for example, by double clicking on the /home/user/Documents folder, the "My documents folder" on windows should be opened. )

---

### Post by gandaran on 2011-03-19
> This is the main question: 
It is possible to mount hard drives and then make an existing folder on Ubuntu (for example the /home/user/Documents folder)point to the "MY DOCUMENTS" folder on windows? 
(By "point to" I mean something like a symbolic link. So, for example, by double clicking on the /home/user/Documents folder, the "My documents folder" on windows should be opened. )
yes you can do that (symbolic link) or just bookmark the drive or folder in nautilus.
for mounting the drive I recommend a system mount, you can do it while installing ubuntu specifying the mount point or do it later adding the drive to /etc/fstab but it should work just as well with the local media mount.

---

### Post by mahela007 on 2011-03-19
Thanks for the reply... at which stage in the installation do I get to choose this setting?

---

### Post by gandaran on 2011-03-19
> **mahela007 said:**
> Thanks for the reply... at which stage in the installation do I get to choose this setting?
choose the manual setup, then after you have the ubuntu installation partitions ready edit the windows ntfs partition, choose ntfs for the partition and select the mount point either /windows or /dos or make your own personal label, just be very careful you don't check-mark the format box! 
the windows partition is displayed as a directory in the ubuntu file system then for quick access bookmark it in the file browser.

---

### Post by mahela007 on 2011-03-20
Thanks.. maybe I'll give that a try..

---

