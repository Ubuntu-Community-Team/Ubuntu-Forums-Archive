---
title: "Resizing Ubuntu partition"
date: 2010-07-26
forum: General Help
---

### Post by pixiesnoot on 2010-07-26
Hi everyone,

When I installed Ubuntu I set it up to dual-boot with windows and didnt put much thought into the partition sizes, and now I want to make the ubuntu partition bigger. I shrunk the windows partition from gparted fine and then booted up off my ubuntu 10.04 disk to make the ubuntu partition bigger, but it won't let me do so from gparted. Anyone know how I could do this?

Attached is a picture of how my hard drive's currently set up.

Thanks!

---

### Post by wojox on 2010-07-26
You can't right click on ext4 and select resize?

---

### Post by pixiesnoot on 2010-07-26
It will only let me expand it 1 MB. I'm not very knowledgeable when it comes to partitions, could it be that the extended partition limits it to that space/size? cause I can't resize the extended partition either. (light blue in the screenshot)

---

### Post by wojox on 2010-07-26
I don't know what the Keys are for. I usually do manual partitioning. Have a look through here [GParted partitioning software - Full tutorial ]("http://www.dedoimedo.com/computers/gparted.html#mozTocId335513")

---

### Post by pixiesnoot on 2010-07-26
it says that the keys mean that "it is used (mounted) and that operations cannot be performed on it", but the keys also show up on the extended partition and the swap partition when I boot off the dvd. Which in my opinion doesnt make any sense. Also unmounting the extended partition isn't an option.

---

### Post by wojox on 2010-07-27
> **pixiesnoot said:**
> it says that the keys mean that "it is used (mounted) and that operations cannot be performed on it", but the keys also show up on the extended partition and the swap partition when I boot off the dvd. Which in my opinion doesnt make any sense. Also unmounting the extended partition isn't an option.

Your running a Live-CD and it's showing that?

---

### Post by pixiesnoot on 2010-07-27
Yes. And I'm not being silly and mounting anything before opening gparted.

---

### Post by Don1500 on 2010-07-27
In GParted:
Highlight the partition with the keys

goto

PARTITION

UNMOUNT

---

### Post by pixiesnoot on 2010-07-27
it won't let me. that option is grayed out.

---

