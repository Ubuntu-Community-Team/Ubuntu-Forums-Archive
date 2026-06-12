---
title: "Mistakenly lost data from external HDD"
date: 2010-09-21
forum: General Help
---

### Post by MarkoSub on 2010-09-21
Hello everybody,

I have a problem I don't know how to solve. Today I bought a netbook and while waiting for the new Ubuntu Unity release to come out, I thought of trying out Crunchbang instead of Windows that came with it. Browsing on my Ubuntu desktop machine, I found a guide for making Crunchbang live USB stick, and i followed the procedure. However, I made a very stupid mistake. The guide said I should enter the command:
sudo dd if=/path/to/iso/crunchbang-10-alpha-01-openbox-i686.iso of=/dev/sdX bs=4M;sync

where "of=...." part should be replaced with the name of the HDD. I forgot that I have an external HDD mounted and mistakenly copied the data to it. 
After this, I cannot see the content of my external HDD anymore. Instead, i have this 620mb large Crunchbang-install device. 

I know what I did was stupid, but is there a way to get the content of my HDD back? I have some valuable data on it, so any help would be very much appreciated.

Thankfully,

Marko

PS I haven't formated the external HDD after I bought it, so I believe it used FAT32 file system.

---

### Post by ajgreeny on 2010-09-21
I think you have lost it all, I'm afraid, as the dd command will have overwritten everything on the external disk with the new crunchbang OS files.

Using dd is not the same as a simple re-formatting, which would have left the old files still on disk and simply have changed the partition table.

I suppose it is possible that testdisk may find some old files if the total size of all of all files dd'd across was not the full external disk size, but how you will sort out which are which I simply do not know.

---

### Post by BobVila on 2010-09-21
Depending on how much you dd'd over, you might be out of luck. 

That's a wicked dangerous command to run, 'cause it can do things like this. 

I'm not super familiar with recovery tools for linux, but your best bet may be tracking one down for windows, plugging the drive in to a windows box, and letting it trawl the disk and see what it comes back with. I'm always surprised by how well those programs work. Anything's better than nothing, I'm guessing, in your case.

The partition tables are likely gone, but hey, you might get lucky and get most of your data back.

---

### Post by MarkoSub on 2010-09-21
Thank you both for replying!

I am running Testdisk at the moment - to see if it helps at all.
After that I guess I'm gonna try out some of that Windows recovery software. Any suggestions which ones should I go for?

Really need those lost files, if possible at all.

---

### Post by MarkoSub on 2010-09-22
Testdisk did not help. Couldn't find my external HDD partition.

However, I am running this PowerDataRecovery (Win software) at the moment. It might help. It identified my external HDD correctly and is now scanning for contents. It will take long time (1TB HDD), but it seems it is finding lots of files&folders.

---

