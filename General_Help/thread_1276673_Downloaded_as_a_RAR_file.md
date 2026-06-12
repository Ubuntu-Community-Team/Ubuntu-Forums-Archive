---
title: "Downloaded as a RAR file"
date: 2009-09-27
forum: General Help
---

### Post by Zundap on 2009-09-27
Hi, could anyone please advice me, i have downloaded UBUNTU and it has downloaded in what i think is a  RAR File, is that how it should be?

Thanks in advance for any replies.:)

---

### Post by cariboo on 2009-09-27
All you have to do is double click on the file, and file-roller should open a window and allow you to extract the file.

What file is it that you are trying to install?

---

### Post by howefield on 2009-09-27
What is the name of the file, and where did you download it from ?

---

### Post by CatKiller on 2009-09-27
> **Zundap said:**
> Hi, could anyone please advice me, i have downloaded UBUNTU and it has downloaded in what i think is a  RAR File, is that how it should be?

It's not a rar file, as you can see by the .iso extension. For some reason WinRAR insists on grabbing hold of ISO files. Just ignore that and burn the image to disk using your favourite cd burning application. [Here]("https://help.ubuntu.com/community/BurningIsoHowto")'s some general guidance in case you get stuck.

---

### Post by Zundap on 2009-09-27
I have double clicked the file and then a window opens with all different programs showing ie: Word Photo shop etc, but non of those programs will open it, they various worded  error meesage's but, saying wrong type of file or the file is corrupt.

I downloaded UBUNTU from the link page on this forum. I was wrong about  the RAR file, it does not say RAR, but it daes have the same picture on it as other RAR Files.

I will try burning it disk and see how it goes, thanks very much every one for your replies.:)

I will right back and let you know if it works, then post may help some one else.

---

### Post by jrusso2 on 2009-09-27
Don't extract the iso just burn it.  Its just associated with winrar which you must have installed.

---

### Post by Zundap on 2009-09-27
Hi again, thanks for that, it burnt no problem, but when i did the disk check, it said there was **"errors found in 30 file's"**

I have used the disk on the trial option, running from disk, and it works brilliantly so would it  be ok to install it to the hard drive???

There is an option to install along side windows ie: have a dual boot option.

Could any one tell me if i boot up in UBUNTU and then install it?

 or do i boot up in windows and then install it?

Or do i install it straight away from boot up of the UBUNTU disk?

Thanks

---

### Post by CatKiller on 2009-09-28
> **Zundap said:**
> Hi again, thanks for that, it burnt no problem, but when i did the disk check, it said there was **"errors found in 30 file's"**

I have used the disk on the trial option, running from disk, and it works brilliantly so would it  be ok to install it to the hard drive???

That would be a problem. It's probably worth burning it again at a slower speed just to be sure. It's also probably worth checking the file that you've downloaded. [Here]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")'s a page that describes how to check the hash of a file against what it [should be]("https://help.ubuntu.com/community/UbuntuHashes").

> 
 There is an option to install along side windows ie: have a dual boot option.

Could any one tell me if i boot up in UBUNTU and then install it?

 or do i boot up in windows and then install it?

Or do i install it straight away from boot up of the UBUNTU disk?It depends on what you want to do. The standard method is to install from the Ubuntu environment on the cd. This will let you create partitions and so on, and set up a bootloader menu to let you choose which one you boot into each time. It's important to pay attention to what you're doing.

The other way is to install from inside Windows. This uses [Wubi]("https://help.ubuntu.com/community/Wubi") to install into a container file on your existing partitions. You can then uninstall Ubuntu the same as any other Windows application. I've not used it though.

---

### Post by Zundap on 2009-09-28
Thanks CatKiller, your advise is greatly appreciated, i really want to learn this inside out, so that i can install UBUNTU for other people, i live in a poor area and it would great to help folk save a few quid.

Cheers. :)

---

