---
title: "Windows Partition Gone!"
date: 2010-05-10
forum: General Help
---

### Post by SirRedTooth on 2010-05-10
I recently upgraded from Karmiac to Lucid.

However now my windows, and the recovery partition (made by my manufacturer to reset the windows partition back to the way it was when I bought the computer) no longer work.

I still have my windows serial key.

Is there anyway to solve this?
I really need the windows partition back before the 'co-owner' of this computer finds out what I have done :(

---

### Post by doas777 on 2010-05-10
you best bet may be testdisk. it is for recovering lost partitions.  the only problem will be that you will need a disk of equal or greater size than the partition lost to write it back out to. 

[here is some info on testdisk]("http://ubuntuforums.org/showthread.php?t=387922"). I usually download it as part of the [ubuntu-rescue-remix cd]("http://ubuntu-rescue-remix.org/").

---

### Post by SirRedTooth on 2010-05-10
By a disk do you mean a CD?
Can I not copy it to a memory stick or a partition?
(Thanks for your response though)

---

### Post by doas777 on 2010-05-10
> **SirRedTooth said:**
> By a disk do you mean a CD?
Can I not copy it to a memory stick or a partition?
(Thanks for your response though)
well whatever type of media will probably work, but it needs to have greater capacity than the original partition that you want to recover. 

while testdisk is scanning your harddisk to get the information from the old partition, it needs somewhere to write it. you can't write to the area that you are trying to recover though, because you would be overwriting the very data you are trying to recover.

---

### Post by sedawk on 2010-05-10
Do you still have the partitions, e.g. is grub showing some
entries to let you boot different Windows partitions, or
does grub only show the Ubuntu installation (or is there
no grub screen because you only have one OS on the disk?).

It is hard to give some tips without more input, e.g.
any error messages.
If the windows partitions are still there and you
can see the files from the Desktop I recommend
to create a backup first( e.g one backup on partition level with
partimage, and an additional backup one on file level with tar).
Get a external USB drive with enough space before messing
around. There might be a simple way to fix this, but it also
might be really hard and need some experience with 
Windows, Virtual PCs (testing changes on a backup), etc.

If you did a full installation (instead of an upgrade) and
told Ubuntu to use the whole disk, you might be beyond
repair.

---

### Post by SirRedTooth on 2010-05-10
Okay thanks, I am having some troubles understanding how to get testdisk works...

I run sudo update-grub2 and got the following response [http://pastebin.com/XZiRPdWF](http://pastebin.com/XZiRPdWF)
Still cannot load windows or the recovery.

---

### Post by SirRedTooth on 2010-05-10
> **sedawk said:**
> Do you still have the partitions, e.g. is grub showing some
entries to let you boot different Windows partitions, or
does grub only show the Ubuntu installation (or is there
no grub screen because you only have one OS on the disk?).
I can see the windows and window recovery partition on the GRUB screen.
When trying to load the windows partition I get a blank screen for a few secs then it goes back to grub.
When trying ti load the windows recovery it goes to a blank screen and I have to shutdown.

> If the windows partitions are still there and you
can see the files from the Desktop
I can see all program files by going into /media/HDD/Program Files


Me running: sudo update-grub2
resulted in this: [http://pastebin.com/XZiRPdWF](http://pastebin.com/XZiRPdWF)

---

### Post by Calash on 2010-05-10
The good news is that the partition is there, you are just having trouble accessing it.

For reference, if you could give us the output of the following it will help.

```

sudo fdisk -l

```

Some good information from this search on fixing the problem.

[http://www.google.com/search?q=lucid+cannot+start+vista&ie=utf-8&oe=utf-8&aq=t&rls=Swiftfox:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=lucid+cannot+start+vista&ie=utf-8&oe=utf-8&aq=t&rls=Swiftfox:en-US:unofficial&client=firefox-a)

---

### Post by SirRedTooth on 2010-05-10
Output of 
sudo fdisk -l
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9eb47d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1045     8393931   27  Unknown
/dev/sda2   *        1046       13903   103280640    7  HPFS/NTFS
/dev/sda4           16545       19457    23398672+   5  Extended
/dev/sda5           16545       19331    22386546   83  Linux
/dev/sda6           19332       19457     1012063+  82  Linux swap / Solaris


And the attached image for a more graphical view of the same thing xD

---

### Post by SirRedTooth on 2010-05-10
I just ran bootscript:
[http://pastebin.com/ZLE9QfCn](http://pastebin.com/ZLE9QfCn)

I have two grub's one on sda1 and another on sda2 is that normal?

---

