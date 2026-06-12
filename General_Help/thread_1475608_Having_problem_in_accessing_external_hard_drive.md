---
title: "Having problem in accessing external hard drive"
date: 2010-05-07
forum: General Help
---

### Post by ronnie006 on 2010-05-07
Hi, I am totally new to ubuntu and I have no idea how to access an external hard drive. When I connect my external hard drive and go to \dev i see my drives, but when i click them it says that you are not the owner, you can't access it. They are blocked. 
They rather look like a file than a drive. Please help me out. And also I am having problems on shutting down the laptop from ubuntu, but it's only been one week I installed it in my laptop. So, please help me with this problem? Should I uninstall it again? If then how do I remove it from my laptop? Note that I have windows XP installed on my laptop as well...
Many Thanx

---

### Post by dino99 on 2010-05-07
sudo apt-get install mountmanager

then you will find it into: system admin mountmanager, open it and tweak the devices and partitions rights as you need

---

### Post by sbergman on 2010-05-07
Hi,

For USB, I usually just plug in the drive after I've logged on and a few seconds later an icon appears on the desktop allowing me to browse the drive. To remove it, just right-click on the icon and select Unmount. ie: it did it for me by default.

Strangely though this only works for me 9 out of 10 times... I've found often that I have to plug it into a different port, or the "safe to remove" message doesnt appear when I want to remove it.

---

### Post by scouser73 on 2010-05-07
**1** - Go to **Applications** > **Accessories** & select **Terminal**, copy & paste this command: > **gksudo nautilus** that will open Terminal as root

**2** - Navigate to the folder or file or drive you wish to gain permissions on, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder or file or drive.

---

### Post by ronnie006 on 2010-05-07
:p
Thanx a lot all of you. I will try that. Thanx...

---

