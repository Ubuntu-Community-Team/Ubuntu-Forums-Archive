---
title: "formatting in ubuntu"
date: 2006-02-01
forum: General Help
---

### Post by xturmn8r on 2006-02-01
I have a partition which I'd like to format in fat32 in ubuntu (so that both windows and ubuntu can see it) 

how do I find out what it is called? (hda1 or 2 or 3 etc).. I recall using fdisk once, but when I tried this time it didn't give me the info I wanted.  Is there a hardware browser application like fedora has that will show me this?

second, can I format this in ubuntu? windows is giving me a pain in the neck because it wants to use ntfs for that partition (I know you can use fat32, I just don't know how I did it last time)  

Thanks for putting up with my noobish questions!

---

### Post by Sutekh on 2006-02-01
[QUOTE=xturmn8r]I have a partition which I'd like to format in fat32 in ubuntu (so that both windows and ubuntu can see it) 

how do I find out what it is called? (hda1 or 2 or 3 etc).. I recall using fdisk once, but when I tried this time it didn't give me the info I wanted.  Is there a hardware browser application like fedora has that will show me this?[/QUOTE]
```
sudo fdisk -l
```
should display everything you need.  Or you could try Applications -> System Tools -> System Monitor -> Devices.  There is another application that I can't remeber, that shows disc partitions.   

**Edit:** its in System -> Administration -> Discs

Alternatively you can use Gparted, which is a formatting GUI.

[QUOTE=xturmn8r]
second, can I format this in ubuntu? windows is giving me a pain in the neck because it wants to use ntfs for that partition (I know you can use fat32, I just don't know how I did it last time)  

Thanks for putting up with my noobish questions![/QUOTE]
Try Gparted.  *I* think its pretty easy to use.  Its in the repositories so you could use Synaptic or
```
sudo apt-get install gparted
```

---

### Post by akiro.yamamoto on 2006-02-01
You can also use GParted, it can create fat32 partitions.

---

### Post by Adrian on 2006-02-01
[QUOTE=xturmn8r]I have a partition which I'd like to format in fat32 in ubuntu (so that both windows and ubuntu can see it) 

how do I find out what it is called? (hda1 or 2 or 3 etc).. I recall using fdisk once, but when I tried this time it didn't give me the info I wanted.  Is there a hardware browser application like fedora has that will show me this?

second, can I format this in ubuntu? windows is giving me a pain in the neck because it wants to use ntfs for that partition (I know you can use fat32, I just don't know how I did it last time)  

Thanks for putting up with my noobish questions![/QUOTE]

I always use the partitioner on the Ubuntu install disk (i.e. the one you get when you boot the CD). It's not the most elegant solution, but it works :)

You might also want to check out this driver to make Windows capable of accessing ext2/ext3 partitions:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by xturmn8r on 2006-02-02
gparted worked extremely well in the end.   The first time windows didn't show the partition under my computer, so I formatted it in NTFS, booted into ubuntu, and converted it into FAT32, and voila, both OSes see it.  \\:D/   

I say that gparted should be included in the base install of ubuntu, utilities such as this are indispensable.

---

