---
title: "complete system image of wubi ubuntu"
date: 2011-06-25
forum: General Help
---

### Post by pxs096320 on 2011-06-25
Hi. I have Ubuntu 11.04 installed by wubi installer alongside win 7 on a sony vaio AMD athelon AMD x64 laptop. I have two quick questions. The ubuntu is on a separate partition of size 20 GB.

1) How can I get a complete system image or clone of my (wubi) ubuntu's partition so that I can mount it over a fresh installation of wubi ubuntu in case of a disaster? This will be helpful in avoiding installing the whole setup again.

I see somethings like system image, clonezilla etc...but still not clear how these work.

2) Also if I do a system restore of win 7, will it affect my wubi ubuntu and prevent it from booting henceforth? How do I overcome such a situation?

I have glanced through a few threads which maybe touching upon this topic. But I do not have a sound understanding of any of them yet. 

So can anyone give me a simple and lucid explanation on these (for a newbie to linux)?

---

### Post by Frogs Hair on 2011-06-25
2. if you restore Windows to a point prior to the Ubuntu installation it will will no longer work . I don't know if moving forward again would restore a working Wubi installation .

---

### Post by pxs096320 on 2011-06-25
I got your statement. But can I infer from your statement that "as long as the system is restored to a point after wubi was installed, it won't hinder the booting of the wubi ubuntu at system startup in any way."   ????? :confused: (ie will the ubuntu's current scheme of things be retained? ie.packges, installs, apps, panels etc)

---

### Post by mike555 on 2011-06-25
It would be better to use Win. 7 and make a real separate partition for Ubuntu , then install to that partition, make sure you make it big enough.

---

### Post by pxs096320 on 2011-06-25
I did just that initially. I had win 7. I allocated a separate big partition for ubuntu and installed in a full-fledged manner the natty narwhal on the separate partition. But by doing that, the grub bootloader took over from the windows bootloader and I had some issues like system randomly restarting and so on. Am not sure if this was related to the change that happened to the bootloader. 

But thereafter, uninstalling ubuntu was a big pain. Hence I decided to install ubuntu via wubi as an application inside windows and now it is much better and issues-free.

---

### Post by pxs096320 on 2011-06-25
So assuming that I have a wubi based ubuntu, I would like to know if there is a complete disk image method to get a clone (which maybe mountable later on a fresh wubi install) and would like to know if win7 system restore would render wubi ubuntu unbootable!

---

### Post by Frogs Hair on 2011-06-25
> **pxs096320 said:**
> I got your statement. But can I infer from your statement that "as long as the system is restored to a point after wubi was installed, it won't hinder the booting of the wubi ubuntu at system startup in any way."   ????? :confused: (ie will the ubuntu's current scheme of things be retained? ie.packges, installs, apps, panels etc)

I have a friend who has used restore with Wubi and I used it when I was using Wubi . My friend went too far back and Ubuntu was gone . A Wubi installation is hidden from Windows so restore cannot make changes in ubuntu because the file system is different . System restore can remove the files in Windows needed to boot Ubuntu .

---

### Post by pxs096320 on 2011-06-25
> **Frogs Hair said:**
> I have a friend who has used restore with Wubi and I used it when I was using Wubi . My friend went too far back and Ubuntu was gone . A Wubi installation is hidden from Windows so restore cannot make changes in ubuntu because the file system is different . System restore can remove the files in Windows needed to boot Ubuntu .

So
1) While your friend went too far back, can I take it that your ubuntu remained intact despite the system restore on win 7?
2) ""System restore can remove the files in Windows needed to boot Ubuntu""------> Even if we restore the win7 to a very recent point, this statement is true? 

So I understand from your statement that system restore may or may not affect the windows boot files essential to boot ubuntu. So in other words, there is no clear guarantee that ubuntu will boot after a system restore irrespective of the point to which it is restored nearby or too far away. Is my understanding of your statement correct?

If I am wrong, do correct me.

---

### Post by Rubi1200 on 2011-06-25
The easiest method to do what you want is to simply make a backup of the root.disk and copy it to a safe place such as an external medium. It might also be a good idea to copy and save the wubildr and wubildr.mbr files at the root of the drive where Wubi is installed.

In the event something goes wrong with the changes you are talking about, simply copy the root.disk back and it should be fine.

Because Wubi uses a virtual disk stored on the host system it is more susceptible to the kind of changes you propose.

The only way to avoid this is either the method I just proposed or install Ubuntu to a dedicated partition on the drive.

---

### Post by pxs096320 on 2011-06-25
@Rubi1200, thanks for that suggestion. That sounds a lot nice but I would just appreciate if you could enlist those finite steps that i need to do to take a backup copy of wubildr and wubildr.mbr files and also duplicate the root.disk. Thanks a lot for that piece of advice though. 

(for now, I would prefer not to re-do a dedicated install of ubuntu on a separate partition. Rather, I would want to just retain my 20GB wubi ubuntu partition as such.)

---

### Post by Rubi1200 on 2011-06-25
Sure, no problem.

In the /ubuntu folder there is a /disks folder and in there is the root.disk. Simply right-click and Copy then Paste it where you want. I suggest something like a USB stick or wherever you know it will be safe. Same goes for the other 2 files which can be found at the root of the drive where Wubi was installed.

The operation could take some time since the root.disk is a large file and contains not only all your installed programs, files etc., but also the free space from the original install.

If you ever encounter problems after restoring the root.disk back to its original folder (such as Wubi not booting and giving you error messages), come back here and ask as the method to fix any problems is relatively easy.

---

### Post by pxs096320 on 2011-06-25
@Rubi2100,
Thanks for writing down the steps. Its very clear and easy to understand. 

1) I presume that a backup of "swap.disk", ".fuse_hidden0000000400000001" file inside the "install" folder , "wubildr.cfg", "wubildr.tar", "wubildr-bootstrap.cfg" inside the winboot folder and a copy of "ubuntu.ico" are not needed right?

2) So in the event of a disaster such as wubi ubuntu not booting up because of a win 7 system restore, what I do is I reinstall a fresh copy of wubi ubuntu and just copy and replace the root.disk file , wubildr and wubildr.mbr files with the old ones right? Is that all?
Correct me if this sequence is wrong. Thanks.

---

### Post by Rubi1200 on 2011-06-25
You can also make a copy of the swap.disk if you want, but the other files are not needed.

The root.disk is the important file to save.

In the event that something goes wrong you actually have 2 options;

1. either copy the root.disk only back to its original folder (assuming the whole install wasn't wiped out by a system restore or anything else). Bear in mind that if you go back to a time before the original Wubi install that there may be a chance that all the files and folder structures would be lost. If that was to happen see 2.

OR

2. make a fresh install of Wubi and then copy your saved version of the root.disk back over the new root.disk (make sure you reinstall the same version of Wubi though). On a fresh install the wubildr and wubildr.mbr files would automatically be installed to the correct place, so no need to replace them.

You probably don't need the other files I suggested copying but it is prudent to do so just in case you *might* need them.

---

### Post by pxs096320 on 2011-06-25
Yes I already have all the necessary files in my external hard disk already:P. Thanks a lot Ruby. Your instructions were pretty lucid. So I guess, that wraps up the system restore issue and system image issue. 
Good day!! :)

---

### Post by Rubi1200 on 2011-06-25
You are more than welcome and I hope all goes well with the changes.

If you run into difficulties with restoring the root.disk (should it become necessary), post here again and I will do my best to help you get things fixed.

---

### Post by pxs096320 on 2011-06-25
Sure, thanks.

---

### Post by Frogs Hair on 2011-06-25
> **pxs096320 said:**
> So
1) While your friend went too far back, can I take it that your ubuntu remained intact despite the system restore on win 7?
2) ""System restore can remove the files in Windows needed to boot Ubuntu""------> Even if we restore the win7 to a very recent point, this statement is true? 

So I understand from your statement that system restore may or may not affect the windows boot files essential to boot ubuntu. So in other words, there is no clear guarantee that ubuntu will boot after a system restore irrespective of the point to which it is restored nearby or too far away. Is my understanding of your statement correct?

If I am wrong, do correct me.

If you restore to a point prior to the wubi installation it removes Ubuntu from add/remove programs just as it does with any windows program  , also it removes the MBR and the wubildr file.

System restore will not  revert your  Ubuntu to earlier state it is a Windows tool . There is a risk that Ubuntu will not boot after a system restore . Wubi is meant for trial use and is much less stable than a traditional dual boot . One reason is that it has a virtual file system.

---

### Post by pxs096320 on 2011-06-25
@Frogs Hair
Yes I do fear that ubuntu may not boot in the event of a system restore. Hence I have taken a back up of root.disk, wubildr , wubildr.mbr and other files in an external hard disk. If I am not able to boot wubi ubuntu, then I will install a fresh copy of wubi ubuntu from the same version of wubi installer and copy and replace the old root.disk file over the new one so that I don't need to re-install all the packages and settings once again. 

I hope that is a good idea from your perspective and angle of thinking as well. ;)

---

