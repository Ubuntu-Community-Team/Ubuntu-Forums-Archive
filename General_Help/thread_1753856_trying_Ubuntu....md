---
title: "trying Ubuntu..."
date: 2011-05-09
forum: General Help
---

### Post by Phaze08 on 2011-05-09
Ok so I'm thinking of installing dual boot vista/Ubuntu. My question is, if I decided to go full Ubuntu later could I without wiping and installing full Ubuntu?

---

### Post by jeremy1138 on 2011-05-09
I'm assuming that you will be installing Ubuntu on its own partition and using Grub to dual boot and not using a Wubi installation.

If that is the case, then yes you can dual boot for now and then get rid of Windows later if you decide you want to use only Ubuntu.

You will need to delete the partition that contains Windows and resize the partition that contains Ubuntu to fill the empty space.  Be sure to back up all your data before you do this just in case.

---

### Post by TheHimself on 2011-05-09
Sure you can. You can just delete Windows' partition and format it as ext3 or ext4 (using gparted). 

If you want to merge the deleted partition with the Ubuntu partition (i.e. not a new partition) things may become a bit more complicated as gparted has to "move" the Ubuntu partition to the beginning of the disk. But you don't have to do this.

---

### Post by JayWalker256 on 2011-05-09
I'm not an expert so correct me if I'm mistaken, but I think the point of LVM (Logical Volume Manager) is to seamlessly integrate extra hard drive space with your Ubuntu installation once it becomes available. You can set up Ubuntu with LVM at install, so this should make it much easier to use the extra space if you wipe your Windows partition.

---

### Post by Phaze08 on 2011-05-09
Ok, sorry for slow reply-Im at work. So, I just install ubuntu, tell it to make its own partition, blah blah blah. How big does the Ubuntu partition need to be? And these are Ubuntu programs I assume? I'd really like to try this because from what Ive seen Ubuntu is really cool, advanced and technical and once I got the hang of it I'd really enjoy I think but I wouldnt want to just wipe my entire harddrive to try it and not like it lol. Can someone explain Grub and Wubi?

---

### Post by jeremy1138 on 2011-05-09
Grub is the bootloader used by Ubuntu to allow you to select which operating system you'd like to load when you start up your computer.

Wubi allows you to install Ubuntu from within Windows as though it was just another program.  This allows you to easily remove Ubuntu should you choose to do so right from add/remove programs in Windows.  I think this is typically recommended as a way to try out Ubuntu and it's not really meant as a way to install Ubuntu for long-term, everyday use.

Also, yes, there is a program included with Ubuntu that will allow you to edit your partitions.  The best way to go about deleting and resizing partitions is to boot a live Ubuntu cd and use that to make the edits you want so that you don't have the disc mounted while you're trying to edit it.

I'm not sure about LVM as mentioned above.  I just did a clean install of Ubuntu on my machine when 11.04 released and I don't think it set up LVM (or even offered to do so) during the install process.  I could be wrong.

(edit)
Oh and as for the size of the partition for Ubuntu, you're probably going to want at least like 20GB (more if you have room or you aren't making a separate partition for home) for the root partition and also a swap partition that is about twice the amount of RAM you have.  You could also create a separate partition for home if you wish.

---

### Post by Topsiho on 2011-05-09
The size of the Ubuntu partition should be at least some 3 to 5 GiB.
But more is better.
You could if you try Ubuntu use 2 partitions, one for root ( / ), and one for swap, which is necessary and used for swapping: writing the contents of memory to disk when the memory is needed for something else.
If you plan to use Ubuntu for a longer time (and you will, I hope), then you should use more partitions for Ubuntu:
Leave Windows in the first partition, which will probably be called /dev/sda1 (the first partition on the first hard disk).
If Windows is sitting in more partitions (disk D:/ etc), then probably these are really partitions /dev/sda2, etc.
These are probably primary partitions of which only 4 are possible.
If you need more partitions, one of the primary should be sacrificed, to make an extended partition, which is used to contain one or more logical partitions. Of course the extended partition should be large enough to contain all your logical partitions :)
Knowing this you should do next (possibly after making one or more  Windows disk(s) empty):
Make a partition for / (the root partition), about 3 to 10 or even 20 GiB. This will contain all the system programs and applications and so on. 20 is really quite sufficient, and even 10 is quite OK. But better be safe than sorry.
Then you make a swap partition. Rule of thumb is 2 times the memory in your computer. If this memory is huge however the swap will most never be needed. But it must be there.
And then you should make a partition for /home, this is where the data comes of all the users of your computer, the files, documents, pictures, movies, and so on (and which you would hate to lose, so always should back up). /home should be as large as you need, and far more, for this ...
You will also be asked what file systems to use.
Swap has it's own file system, called ... (linux) swap.
/ and /home are usually ext3 or ext4, of which ext4 is the newest, and as far as I know now quite dependable.

Hope this will help you,

Topsiho

---

### Post by Phaze08 on 2011-05-09
Wow, this is alot of information, thanks you guys. Ill have to look over it when I get home and do this. Does it really take that many partitions? Seems like its a little much to me, but I dont know much about linux so Im probably wrong lol.

---

### Post by jeremy1138 on 2011-05-09
> **Phaze08 said:**
> Wow, this is alot of information, thanks you guys. Ill have to look over it when I get home and do this. Does it really take that many partitions? Seems like its a little much to me, but I dont know much about linux so Im probably wrong lol.

I'm pretty sure when you install Ubuntu that it has an option to "install alongside your existing windows installation" or something to that effect.  I believe it just resizes your windows partition in half and sets up Ubuntu in an extended partition on the other half.  If you don't want to get your hands dirty mucking about in the business of manually setting up partitions, then that's probably the way to go.

---

### Post by collisionystm on 2011-05-09
> **Phaze08 said:**
> Wow, this is alot of information, thanks you guys. Ill have to look over it when I get home and do this. Does it really take that many partitions? Seems like its a little much to me, but I dont know much about linux so Im probably wrong lol.


Put in your ubuntu cd. 

Run the setup.

Click Install next to windows.

---

### Post by stber321 on 2011-05-09
> **Phaze08 said:**
> Ok so I'm thinking of installing dual boot vista/Ubuntu. My question is, if I decided to go full Ubuntu later could I without wiping and installing full Ubuntu?


absolutely, you would just open up gparted remove the windows partition and fill the empty space with ubuntu (dont make a mistake), but i would like you to be aware of the fact that ubuntu has just switched to unity and i recommend GNOME so you may like Linux Mint a little better:P:P

---

### Post by bcbc on 2011-05-09
> **stber321 said:**
> absolutely, you would just open up gparted remove the windows partition and fill the empty space with ubuntu (dont make a mistake), but i would like you to be aware of the fact that ubuntu has just switched to unity and i recommend GNOME so you may like Linux Mint a little better:P:P

Gnome desktop is still available - just choose the "Classic" desktop when you login.

---

