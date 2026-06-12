---
title: "HDD clone"
date: 2010-08-20
forum: General Help
---

### Post by Kmob810 on 2010-08-20
I am running Ubuntu 10.04 as a dual boot with Vista Home on my laptop. I do normal back ups on both but I would like to do a clone (or similar) to my hdd. I have an 80g external usb disc which I would  like to us for this but I need some assistance.
1.what is the best programme to us, is Norton Ghost ok?
2.How do I format the ext hd to enable the clone to use Linux & MS?
3.And will I be able to do incremental backups on the ext hd?
(****Maybe that last one shows just how little I know on this subject lol)
The reason I ask is that I had a recent serious problem with Vista and required an IT engineer to reinstall it. I couldn't even use the backups I had or F8.
Long story but all is ok now but I need a clone or something to set my mind at rest.
Any help would be appreciated. Not too used to Linux yet so could you keep the help at a newbie level please?
Thanks

---

### Post by dcstar on 2010-08-20
> **Kmob810 said:**
> I am running Ubuntu 10.04 as a dual boot with Vista Home on my laptop. I do normal back ups on both but I would like to do a clone (or similar) to my hdd. I have an 80g external usb disc which I would  like to us for this but I need some assistance.
1.what is the best programme to us, is Norton Ghost ok?
2.How do I format the ext hd to enable the clone to use Linux & MS?
3.And will I be able to do incremental backups on the ext hd?
(****Maybe that last one shows just how little I know on this subject lol)
The reason I ask is that I had a recent serious problem with Vista and required an IT engineer to reinstall it. I couldn't even use the backups I had or F8.
Long story but all is ok now but I need a clone or something to set my mind at rest.
Any help would be appreciated. Not too used to Linux yet so could you keep the help at a newbie level please?
Thanks

Boot off the Ubuntu Live CD and use the dd command to clone the disk to a file.

Do a forum search for detailed instructions on using dd.

---

### Post by ushills on 2010-08-20
I did this recently with ddrescue.

See this guide [http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk]("http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk")

---

### Post by Eldera on 2010-08-20
> keep the help at a newbie level please

I, too, am new to Ubuntu, but am glad to share. I am working on a similar project: I have cloned my computer, but have not yet tried to restore the computer from the clone.

> 1.what is the best programme to us, is Norton Ghost ok?

I used Clonezilla. [http://www.clonezilla.org/](http://www.clonezilla.org/)

Clonezilla is a like Norton Ghost, but has downloads specific for Ubuntu versions: Karmic, Lucid, Maverick. If I were dual booting I would use Ubuntu to make my CD.

One does a download and then burns it to a CD to create a bootable disk.
Then one boots from the disk and follows the prompts to create the clone.
(According to the instructions, one restores by booting from the same disk and choosing slightly different prompts, but I have not tried to do that yet.)

> 2.How do I format the ext hd to enable the clone to use Linux & MS?

The clonezilla disk will format your drive for you. Usual warning: it completely wipes the drive so don't use one that has data on it that you want to keep.

I tried to make a clone on a disk that already had something on it, and Clonezilla made an image instead of a clone. I had to go back and use Gparted from a live Ubuntu CD to wipe all the formatting off my drive and do it all over again.

> I have an 80g external usb disc 

I am not sure how to handle this, Clonezilla only clones into a space as large or larger than the drive being cloned. I was cloning to a 320 G external drive.

I think there is also a way to make "images" as opposed to "clones" with Clonezilla, but I have not yet learn how. You might be able to make an image to an 80g usb. I found Clonezilla's site very hard to read because Clonezilla comes in two forms, one for server systems and Clonezilla Live for single stand alone computers. The instructions for both forms were mixed up together. I would read half way through a tutorial and then realize it was for server systems.

> 3.And will I be able to do incremental backups on the ext hd?

I don't know.

Have a great day, Eldera

---

### Post by Kmob810 on 2010-08-21
Thanks for the help everyone. I decided to give Clonezilla a try and it appears to have worked. I won't really know I suppose, until I have a problem and need to run the clone.

):P ):P ):P ):P

---

