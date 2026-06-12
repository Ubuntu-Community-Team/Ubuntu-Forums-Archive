---
title: "Recovering from canceling gparted"
date: 2010-01-10
forum: General Help
---

### Post by R3N3G4D3 on 2010-01-10
Before I start, I'm still in the process of running gparted and haven't canceled yet, so I have a choice of when to cancel to cause the least data loss.

Basically, I have a 1.5 TB harddrive, that I used to use for data storage (ext3 partition). After moving to a smaller computer case I had to get rid of the other harddrive I used for booting. So I resized the partition and added Linux at the end. To make long story short, I eventually ended up with a couple bootable partitions at the end after the data partition and now need to move them to the front. So I tried to use gparted to do just that.

Since it took me about 30-60 mins each time before to shrink my data partition, I didn't realize that moving/resizing partition from the left side takes a lot longer than the right. I set up a sequence of operations in gparted to shrink/copy/move/expand partitions as needed until it ends up with my bootable partitions in the beginning and data at the end.

Now, 12 hours later, I'm still stuck on doing the first of 16 operations (I didn't optimize the shrinking/moving since I didn't realize it would take so long) with gparted expecting operation 1 to complete in 5 hours (it's in the middle of copying sectors now).

Seeing as this will likely take a few weeks to complete the entire sequence, I would rather cancel this and deal with repairing my partitions instead of being stuck with only a LiveCD for a month. I mostly care about the data partition (which is 1.3 TB in size and about 25% full) and my user files in Ubuntu (I don't mind reinstalling it, as long as I can retrieve the data from my home folder).

When is it safest to cancel? Based on sector numbers, right now gparted is copying free space from my data partition. Should I cancel now, or wait until it's doing read operation for second task (also on the data partition)? Can I cancel right after it's done with task 1 but before it starts task 2 or will I not be able to time it? My data partition is formatted as ext3, Ubuntu is ext4, and I don't really care about other bootable partitions.

---

### Post by John Bean on 2010-01-10
If you cancel the chance of total success is small and the possibility of catastrophic data loss on one or more partitions is quite high.

Let it run is my advice.

---

### Post by R3N3G4D3 on 2010-01-10
Even if I use Testdisk afterwards? I heard it's pretty good at recovering partitions, and majority of my harddrive is empty space.

---

### Post by John Bean on 2010-01-11
> **R3N3G4D3 said:**
> Even if I use Testdisk afterwards? I heard it's pretty good at recovering partitions, and majority of my harddrive is empty space.

It's your data, your call; all I can offer is advice based on what I would do.

---

### Post by SecretCode on 2010-01-11
I have to agree with John Bean.

> **R3N3G4D3 said:**
> Even if I use Testdisk afterwards? I heard it's pretty good at recovering partitions, and majority of my harddrive is empty space.

But you'll be in a situation where some data has been moved. Testdisk may detect the new partition layout but the contents won't be compliant to ext3, I'm pretty sure. Even fsck may not be enough to make it readable.

However, if it's mostly empty space, the operations may speed up at the end.

---

### Post by Elfy on 2010-01-11
> **R3N3G4D3 said:**
> Even if I use Testdisk afterwards? I heard it's pretty good at recovering partitions, and majority of my harddrive is empty space.

What if it doesn't ? Do you have backups ? 

I would also be extremely wary of cancelling - perhaps post here [http://gparted-forum.surf4.info/](http://gparted-forum.surf4.info/)

---

### Post by SecretCode on 2010-01-11
That's a good idea. The gparted forum is very helpful.

---

### Post by Grenage on 2010-01-11
Unless you have backups, cancelling is the last thing you want to do.

---

