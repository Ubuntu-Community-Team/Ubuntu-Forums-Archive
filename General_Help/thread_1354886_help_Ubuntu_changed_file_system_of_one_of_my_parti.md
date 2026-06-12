---
title: "help: Ubuntu changed file system of one of my partitions"
date: 2009-12-14
forum: General Help
---

### Post by AFG34 on 2009-12-14
ok so first i had two partitions, one for windows7 and the other for media files

so i wanted to try ubuntu, therefore i created another partition of 20gb

burned ubuntu img and installed it: during the installation process i couldn't get it to install on the 20gb partition so i chose the "side by side" with Windows7.

Now, i can't access the partition that had all my media files from W7. Im assuming ubuntu changed it to a different file system. [last night i was listening to some music that was stored in that partition with rythmbox]


What i want to do is revert it(the partition with all my media files) back to NTFS. I am not gonna write to that partition from ubuntu. I need to be able to access it and write to it from WIN7.


btw, this is all one hard drive.

thanks

---

### Post by lisati on 2009-12-14
One way of checking if your assumption about the disk format being changed is true is through this command from Ubuntu's command line (Applications->Accessories->Terminal):
[quote]sudo fdisk -l[/code]
Note: (1) That's a little "ell", not a number one. (2) You will be asked for your password. It won't show as you type: just type it as usual

---

### Post by dumblebee100 on 2009-12-14
the OP said correct ..the fdisk command will do the trick and then you have to mount the partitions and then know which partition is your multimedia partition ....then after you can automate it through the FSTAB thing ..

if you are not sure about mounting the NFTS manually or through FTSAB then hit the search in this forum you will get many links

---

### Post by AFG34 on 2009-12-14
ok i attached the screenshot, don't know how to read that so help me

---

### Post by philinux on 2009-12-14
> **AFG34 said:**
> ok i attached the screenshot, don't know how to read that so help me

Have a look under Places. Do you partitions show up?

---

### Post by AFG34 on 2009-12-14
> **philinux said:**
> Have a look under Places. Do you partitions show up?

ya i can see my W7 partition, the media partition..




so is the filesystem changed?
and if so, how do i change it to NTFS?

---

### Post by AFG34 on 2009-12-14
any help

---

### Post by oldfred on 2009-12-14
You have 3 NTFS partitions and one Linux partition plus swap. So what is the question?

---

### Post by dumblebee100 on 2010-01-11
> **AFG34 said:**
> ok i attached the screenshot, don't know how to read that so help me

just try to mount the sda5 and sda6 partitions either by graphical interface or command line ..

I hope you know the mounting procedure or otherwise hit the search and find about ntfs mount ...before that u need to have ntfs-3g package installed

---

