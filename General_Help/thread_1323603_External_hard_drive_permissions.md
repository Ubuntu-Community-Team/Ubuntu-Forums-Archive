---
title: "External hard drive permissions"
date: 2009-11-11
forum: General Help
---

### Post by ColdLunch on 2009-11-11
I'm running Karmic and I have a 320 GB Seagate External hard drive formatted as hfs+.

I can't seem to write to it, only read from it.  So I'm guessing its read-only.

How can I change its permissions?
GParted won't let me reformat it or anything.

Thanks.

---

### Post by ColdLunch on 2009-11-12
Anyone?  I'd really like to be able to use this hard drive. :D

Thanks!

---

### Post by scouser73 on 2009-11-12
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by ro2nie on 2009-11-13
1) In Mac OS X Go and select your hard drive, right click it> select get info.

2) Change its permissions, and where it says Everyone, change it to Read&Write

3) Now go and open disk utility. Select your hard disk, and press and hold the option key (alt key) whilst you click File in the menu. You will see an option that reads "Disable Journaling" Click that, and then eject your drive.

4) Now plug the hard drive into your Ubuntu machine, and try to write to it. All files will have locks on them, because they will have the wrong permissions. To fix this, I went to the terminal and did:
```
sudo chmod -R 775 /media/[name_of_your_hard_drive]
```

This procedure will let you write to the drive from both Mac OS X and Ubuntu.

---

### Post by coffeecat on 2009-11-13
If that drive is formatted with the journalled version of hfs+ you'll not be able to write to it in Ubuntu. Changing permissions in MacOS will not help you write to it in Ubuntu. Similarly, a root-owned Nautilus browser will not help. The Linux hfs+ driver does **not** support writing to the journalled version of hfs+.

If you want to share files between Ubuntu and your Mac using hfs+, and be able to write to the drive in Ubuntu, you'll have to use the Mac Disk Utility to reformat that drive to the **non-journalled** version of hfs+. Then Ubuntu will be able to write to it. Of course, you'll have the disadvantages of a non-journalled filesystem.

And, of course, you will run into permission problems sooner or later because your Mac UID will be different from your Ubuntu UID. This is when you will need to change permissions in MacOS or do some chowning or chmodding in Ubuntu.

See that dent on my forehead?  Do you hear the voice of bitter experience? :(

---

### Post by ro2nie on 2009-11-13
> **coffeecat said:**
> ...If you want to share files between Ubuntu and your Mac using hfs+, and be able to write to the drive in Ubuntu, you'll have to use the Mac Disk Utility to reformat that drive to the **non-journalled** version of hfs+. Then Ubuntu will be able to write to it. Of course, you'll have the disadvantages of a non-journalled filesystem...


You don't need to reformat the drive to disable journaling. You just have to press alt and click File>Disable Journaling in Disk Utility and you are done.

I did this yesterday with 2 of my drives. I can successfully write to them from either Mac OS X and Ubuntu with no problems at all.

---

### Post by coffeecat on 2009-11-13
> **ro2nie said:**
> You don't need to reformat the drive to disable journaling. You just have to press alt and click File>Disable Journaling in Disk Utility and you are done.

Thanks for the tip. :)

---

### Post by ColdLunch on 2009-11-14
Thanks guys, this worked out great!

---

