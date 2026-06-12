---
title: "HDD dissapears after installation"
date: 2011-03-25
forum: General Help
---

### Post by b737lvr on 2011-03-25
I have 2 HDD's:

C Drive (Windows Installed)
G Drive

I installed Ubuntu 10.10 64 Bit on a partition on the G Drive.

Now my G Drive doesn't show up any more when browsing in the computer. I can select it to start up from but not to browse through.

Any Ideas to solve this?

---

### Post by hal8000 on 2011-03-25
> **b737lvr said:**
> I have 2 HDD's:

C Drive (Windows Installed)
G Drive

I installed Ubuntu 10.10 64 Bit on a partition on the G Drive.

Now my G Drive doesn't show up any more when browsing in the computer. I can select it to start up from but not to browse through.

Any Ideas to solve this?

Linux partitions are not named by a drive letter but have designations
like /dev/sda5.

If you're trying to browse the G drive from windows then it wont show as its now using linux file systems that windows does not understand.

You can however read and write to NTFS partitions from Ubuntu.

---

### Post by Rubi1200 on 2011-03-25
Have you tried Places > Computer > File System > Host or Media?

---

### Post by b737lvr on 2011-03-25
So how can i browse my G Drive from windows, now.  The partition that had all of my files.

---

### Post by b737lvr on 2011-03-25
anyone?

---

### Post by jerome1232 on 2011-03-25
Well if you installed a true dual boot (by the sounds of it you did), and you installed Ubuntu to that partition labeled as G: in Windows, all files on that partition are gone, it was formatted to a Linux File System and the Ubuntu Operating System was installed to it.

Just to get a good idea of what your drives and partitions look like currently can you post the output of fdisk to give us a more clear picture?

You can do that from Ubuntu by clicking Applications->Accessories->Terminal and typing the following code after the prompt and hitting enter

```
sudo fdisk -l
```

Highlight all the output and press ctl+shift+c to copy it, then paste it into a reply, ensure you are in advanced editing mode, highlight all of the output and click on the "#" button to make it easier to read.

It is possible you can recover some of your files, but some may be damaged, they wouldn't retain their original folder hierarchy and they wouldn't retain their original names, we can talk more in depth about that if that is indeed required.

---

### Post by dragonfly41 on 2011-03-25
I'm still struggling to repair my Vista configuration although I can see Windows files from within Ubuntu which is running inside Windows in an ntfs partition.

You've got the opposite problem of not being able to view separate Ubuntu partition.

Here is a windows utility .. there must be others ..

[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)

I sincerely hope you have not wiped your G: partition by installing Ubuntu. I don't know for sure since I'm quite new to Ubuntu and I'm using it in demo mode myself until I can repair and backup my windows files.

If you have wiped you might have to remove your disk and slave it to another PC to analyse it with a windows utility such as recovermyfiles.


...

p.s. I'm adding this link which just might be useful (I've not used it .. yet)

[http://www.diskinternals.com/linux-recovery/](http://www.diskinternals.com/linux-recovery/)

[http://www.diskinternals.com/partition-recovery/](http://www.diskinternals.com/partition-recovery/)

---

### Post by b737lvr on 2011-03-25
Jerome,

I do not have internet connection on the Linux part of my machine so i cant paste the outcome to a post.

But i installed Ubuntu on a partition to the G Drive.  so it was like 100 GB of something were my files and 40 GB was for ubuntu.

---

### Post by jerome1232 on 2011-03-25
Okay.

When you click on the places menu in Ubuntu what is all listed there?


Also you can save the output of fdisk to a text file in Ubuntu, copy that text file to a thumb drive or to the Windows partition (should be in the places menu) then boot into windows, open that text file and paste the output here.

So the command that would automatically create a text file on your Ubuntu Desktop so you could copy would be...
(while your at it we might as well get what is mounted and where)

```
sudo fdisk -l > ~/Desktop/fdisk.txt
mount >> ~/Desktop/fdisk.txt
```

After running that you should be able to drag the file to your windows partition.


Edit: You might want to look at what Windows see as well, If you goto Start->Control Panel->Administrative Tools->Computer Management->Storage, take a screenshot and upload it using the paperclip button in advanced editing mode to show us what Windows sees.

---

