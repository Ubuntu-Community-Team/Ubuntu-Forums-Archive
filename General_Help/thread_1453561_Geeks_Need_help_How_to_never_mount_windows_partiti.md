---
title: "Geeks? Need help? How to never mount windows partitions during boot?"
date: 2010-04-13
forum: General Help
---

### Post by schwabdale on 2010-04-13
Can someone tell me how to do this?

---

### Post by schwabdale on 2010-04-13
By the way, I am running this off a flash drive. I want to move it from one computer to another. 
No matter what I plug this in to, I don't want the OS to ever mount a windows partition. Please help.

---

### Post by hackb0y294 on 2010-04-13
What do you mean by never mount them? If you're never going to use the partition, why not format it or remove the drive?

---

### Post by schwabdale on 2010-04-13
I want to modify a Ubuntu USB stick and put some tools on it and move it from one computer to the next. 
I also want to be able to hand one to some sales people for when their computer crashes, they wouldn't be able to see their partitions.

---

### Post by hackb0y294 on 2010-04-13
Well, I don't know how to do that, sorry.

---

### Post by prodigy_ on 2010-04-13
Normally, if it's not present in **/etc/fstab** it won't be mounted automatically. Also you may want to unistall GVFS to prevent auto-mounting any partitions in user mode.

Alternatively, you can mount partitions with read-only access (changing **rw** to **ro** in **/etc/fstab**).

---

### Post by nothingspecial on 2010-04-13
You could try moving the ntfs module out of /lib/modules/$(uname -r)/kernel/fs

but I wouldn`t recommend it - really I wouldn`t.

---

### Post by aysiu on 2010-04-13
> **schwabdale said:**
> I want to modify a Ubuntu USB stick and put some tools on it and move it from one computer to the next. 
I also want to be able to hand one to some sales people for when their computer crashes, they wouldn't be able to see their partitions. I don't get it. If their computer crashes, wouldn't you want them to be able to see their partitions so they could rescue the data off those crashed computers?

As far as I know, Ubuntu doesn't automatically mount *internal* drives. You have to go to Places and click on the drive to get it to actually mount. *External* drives do, however, get automatically mounted.

If you remove that package (mentioned above) to prevent automounting, it will probably affect automounting of all drives (NTFS, Ext3, FAT32).

By the way, if you want to modify a Ubuntu live CD, I'd recommend using Remastersys.

---

### Post by schwabdale on 2010-04-13
Maybe I should have explained a little further... Sorry...

I want my sales guys to boot of the flash drive, then they can use terminal services.
I will get any data they need from their pc, I just want a backup method they can use. 

It looks like "hard drives" are not automounted... however "partitions" seem to be. 
I want Ubuntu to not mount anything but the flash drive. Do any of the previous posts look like 
they would work?

---

### Post by schwabdale on 2010-04-14
Is there a way to make sure the partition on the flash drive is always set at /sda....
Maybe I could make sure it never changes. If I do that, couldn't I tell the OS to never 
mount /sdb through something like PYSDM?

Any other ideas?

---

### Post by mikewhatever on 2010-04-14
> **schwabdale said:**
> ...
It looks like "hard drives" are not automounted... however "partitions" seem to be. 
I want Ubuntu to not mount anything but the flash drive. Do any of the previous posts look like 
they would work?

There seems to be a terminology problem. Hard Drives are black metal boxes with circular magnetic platters and heads inside. You can connect them to the motherboard with cables, but you can't mount them.

Partitions (or file systems) is the only thing you can mount, and, as mentioned above, Ubuntu does not automount partitions, unless told to. 

[http://computer.howstuffworks.com/hard-disk.htm](http://computer.howstuffworks.com/hard-disk.htm)

---

### Post by schwabdale on 2010-04-14
There may have been some misunderstanding on my part. 
Example: My hard drive is /sda... My windows partition is /sda1...
              : My flash drive is /sdb... My ubuntu partition is /sdb1

When I open Places/Home folder I see both filesystems.... So I am lead to believe that the Filesystems (Partitions) are mounted automatically. Until I click the arrow next to them, they seem to be mounted. 

All I want to do is make sure no other partitions are available at all except the flash drive. 

If this is not possible please let me know.

---

### Post by Monotoko on 2010-04-14
Post the contents of your /etc/fstab here :)

If you give the sales people a limited account without sudo access, they cannot mount anything at all, but from what your saying it seems as though they are already mounted? Which is strange..

---

### Post by Vaphell on 2010-04-14
you can see the partition and not have it mounted, doubleclicking it will try to mount it and later you can unmount it. That's the case on my current computer. Ubuntu lists  windows recovery and vista partitions but doubleclicking on any of them shows dialog window to type in password to allow mounting.
From your description it's not that clear whether these partitions are really mounted or merely visible as able to be mounted - though you said something about 'unmount arrow' which would indicate they are mounted.

---

### Post by mikewhatever on 2010-04-14
> **schwabdale said:**
> There may have been some misunderstanding on my part. 
Example: My hard drive is /sda... My windows partition is /sda1...
              : My flash drive is /sdb... My ubuntu partition is /sdb1

When I open Places/Home folder I see both filesystems.... So I am lead to believe that the Filesystems (Partitions) are mounted automatically. Until I click the arrow next to them, they seem to be mounted. 

All I want to do is make sure no other partitions are available at all except the flash drive. 
If this is not possible please let me know.

I think your problem is the Nautilus file browser, or perhaps the Gnome DE as a whole. The default behavior here is to show all available partitions in the left panel or under Places, and  I don't know of any 'easy' way to disable that.
I don't think Thunar or PCmanFM file managers do that, so you might want to try Xubuntu, Lubuntu, or other xfce and lxde distros. On the other hand, you could make a custom Ubuntu installation without a file browser, and with only the programs you need.

---

### Post by Alabamaschalk on 2010-04-14
How about compiling a kernel without the option to use windows file systems?
I do not know the exact option in the configuration, but there may be one.

---

### Post by schwabdale on 2010-04-14
Thanks for the posts. Maybe I should just try another distro.

---

