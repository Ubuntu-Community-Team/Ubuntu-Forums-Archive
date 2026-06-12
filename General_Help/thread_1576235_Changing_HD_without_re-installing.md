---
title: "Changing HD without re-installing"
date: 2010-09-16
forum: General Help
---

### Post by Ranko Kohime on 2010-09-16
I've got Ubuntu set up just about the way I want it to be setup in my EeePC, and I'm thinking about swapping out the 8GB SSD for a larger one now.

What I'd like to do, is do a complete image of the entire contents of my existing SSD, (1 partition for / and /home) to a USB flash drive, and then transfer the data back from the flash drive to the new SSD.  I don't exactly want to copy the partition directly, just a sufficient copy as to make the system bootable as is on the new drive.

So is there a utility which will do this?  :)

---

### Post by harrismh777 on 2010-09-17
No utility. 
It can be done, but its a ton of work. Forget it.

Add another SSD to the system and expand the file system. 


Why do you think you need more disk space?  Not for the system!

Move stuff to archive... you know... all of your videos, photos, movies, netflicks, base ball card collection, ..... external USB drives work great for this. 


If what you are really trying to do is to create a disk image you are going to have to build an installer. It is possible to build a disk image (clone) for identical hardware, except that you'll want to disable all the uuid stuff. 

(sorry, realized that I am rambling here....)

---

### Post by john newbuntu on 2010-09-17
Try Clonezilla.  It will image your existing drive (or partitions) and you can copy it back to your new drive once you swap it.
I did not get this part though:
> I don't exactly want to copy the partition directly
You may have to re-install grub although I am not a 100% sure.

---

### Post by Ranko Kohime on 2010-09-17
> **john newbuntu said:**
> Try Clonezilla.  It will image your existing drive (or partitions) and you can copy it back to your new drive once you swap it.
I did not get this part though:

You may have to re-install grub although I am not a 100% sure.
What I meant was, I don't want to copy the 8GB partition from the old drive, to an 8GB partition on the new drive, I want a single partition on the new drive that completely fills it.

I'll give Clonezilla a try.

---

### Post by Ranko Kohime on 2010-09-17
> **harrismh777 said:**
> Add another SSD to the system and expand the file system.
That's rather difficult on a laptop.  :p

As for the need for disk space, there are a few large files I'd like to take with me, without having to plug in a USB stick every time I want to access them.  The total sum of the files exceeds the current disk capacity, so unless Ubuntu can be configured to take a negative amount of space, a bigger SSD it is!  ;)

---

### Post by john newbuntu on 2010-09-17
> **Ranko Kohime said:**
> What I meant was, I don't want to copy the 8GB partition from the old drive, to an 8GB partition on the new drive, I want a single partition on the new drive that completely fills it.

I'll give Clonezilla a try.
Ahh. not a problem. Clonezilla just creates a folder and a number of subfolders and copies only the used data blocks not entire partitions.

---

