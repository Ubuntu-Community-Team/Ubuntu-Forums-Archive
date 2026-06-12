---
title: "Trying to resize ext3 partition"
date: 2006-06-08
forum: General Help
---

### Post by Enigmatic on 2006-06-08
Here is my HDD config:

[IMG]http://www.gregschneider.net/Screenshot.png[/IMG]

What I want to do is expand the ext3 partition to include the unallocated space. But the partitioner doesn't let me choose a size larger than 31GB (same as it already is, after conversion losses etc) for the ext3 partition.

Is there any way to make this work?

---

### Post by kb3hkg on 2006-06-08
I don't believe it can just be expanded. I don't think ext3 can do that. You would need to completely reformat the partition to include the additional space.

---

### Post by RRS on 2006-06-09
I'm afraid you can only expand an existng partition upward (to the right in your graphic)

It looks like the only way to use your unallocated space is by expanding sda6 to the right. I don't think you'll be able to do anything with the 7.84mb at the beginning of the drive.

Sorry, but of course if I'm wrong hopefully someone else can help you, and I'll learn something new too :)

---

### Post by aysiu on 2006-06-09
RRS is right.

/dev/sda6 can be added to, but no other partition can use that unallocated space.

---

### Post by Enigmatic on 2006-06-09
Interesting, that's a surprise to me that it wouldn't work. 

I guess I could always move the stuff off my NTFS drives then format them as ext3 before moving the files back. After all, it's only another mountpoint and easy to access.

---

### Post by Enigmatic on 2006-06-09
Well, I partitioned the free space to ext3, but I can't mount it. Says it's not removable and that it wasn't able to execute pmount.

Here's a screen of the config now:

[IMG]http://www.gregschneider.net/Screenshot2.png[/IMG]

---

### Post by aysiu on 2006-06-09
Try this: ```
sudo umount /dev/sda7
sudo mkdir /storage
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` If there's already a line for /dev/sda7, delete it. Then add in this line: ```
/dev/sda7 /storage ext3 defaults 0 0
``` Save (control-x), confirm (y), exit (Enter). ```
sudo mount -a
sudo chown -R enigmatic:enigmatic /storage
sudo chmod -R 755 /storage
``` This assumes, of course, that you want it to appear in the folder *storage* and that your username is *enigmatic*.

---

### Post by Enigmatic on 2006-06-09
Okay, I did that, but now when I try to open it nothing at all happens.

---

### Post by aysiu on 2006-06-09
Can you be more specific than "nothing at all"? How are you trying to open it... with the terminal, with a file browser? Does it open as empty... does it not open at all?

---

### Post by Enigmatic on 2006-06-09
Interesting, it seems to work after a reboot. :confused: 

Anyways, I was using Nautilus, and it didn't give me any errors, just didn't open anything.

---

### Post by Enigmatic on 2006-06-09
Is there a way to rename it? It's showing up as 5.9GB: /Storage.

---

### Post by aysiu on 2006-06-09
You could always put it to a different mount point if you make a directory for it and change the /etc/fstab.

---

### Post by Enigmatic on 2006-06-12
Back to this again...

I've been cleaning off my NTFS drives and resized them to the min size. Now I have a few GBs of free space, that I was hoping to resize the Storage partition to include.

However, it doesn't let me increase the storage partition size (see image for structure).

[IMG]http://www.gregschneider.net/Screenshot3.png[/IMG]

Is this just a normal limitation, or do I have a really awkward partition table? Is there any way to expand that partition to include the free space?

---

### Post by aysiu on 2006-06-12
Is it /dev/sda7 you're trying to increase? You can add on only to the end of a partition, not the beginning.

---

### Post by Enigmatic on 2006-06-13
Yes, I'm trying to add the unallocated space to sda7.

---

### Post by em3raldxiii on 2006-08-08
I have to say, this is a pretty wacky partition setup ... yoikes.
 
I dunno ... I think what ya gotta do is to rip off **sda7**, shrink **sda1**, then create a primary partition in the new space between **sda6** and **sda2** formatted as **ext3** 
 
Alternatively (and possibly better), rip off **sda7** by moving your files elsewhere if possible, then increase **sda6** to fit the files from **sda2**, then remove **sda2**, shrink **sda1** (shrink 6 if required before hand) again, then create a brand new big EXT3 partition in the newly created space.
 
follow me?
 
*EDIT: Gah ... I just noticed that 2 is your boot drive. Dude this is an extremely fugly setup. LOL .... scrap it all and start again hahaha ... if only it was so easy.*

---

