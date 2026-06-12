---
title: "Move whole system to other partition"
date: 2012-09-16
forum: General Help
---

### Post by elemenophee on 2012-09-16
Actually I have:
sda1 (physical): Windows 7 boot partition
sda2 (physical): Windows
sda3 (physical): Games (run under Windows)
sda4 (logic)
sda5 (logic): Linux
sda6 (logic): swap

I'm thinking in remove sda3 and put Linux in a physical partition (so later I could resize it whether I need it).

But don't know whether is possible or no, and if it is possible... how to do it?

---

### Post by Bucky Ball on 2012-09-16
Simplest is to delete sda3 and do a fresh install to that partition. You can use the existing /swap (sda6) for as many installs as you like. What is on sda4?

---

### Post by elemenophee on 2012-09-16
I know that is the simplest but just made a fresh install like 4 days ago... and install and configure everything again.. pfff

On sda4 there isn't nothing. It is the first logic partition root of the other ones.

---

### Post by Bucky Ball on 2012-09-16
Easy then. Delete sda3/4, expand the Linux install sda5 to the left using the free space so now it butts up with sda2. Shrink it from the right if you like but that will  leave free space between the end of the Ubuntu install and /swap. 

Done. This could take awhile to move things around so put aside some time to do. If you've only just installed shouldn't be too bad. This MUST be done booting from the LiveCD as the partitions you're manipulating  need to be unmounted and, of course, can't be if you're running the OS  from one. 

You have a few options and if you want to share data between win and Ubuntu an NTFS partition would be a consideration. There are options for how you set that up, also. For instance, you could delete the directories in you /home directory inside /, create directories like /documents, /music, whatever in the NTFS share partition and then create symlinks to them inside the /home directory of your Ubuntu install, if that makes sense.

That way the data in /documents, /music etc in the NTFS partition will be available to both installs. Bit of food for thought ... ;)

---

### Post by elemenophee on 2012-09-16
You can't move a logical partition and also, since I delete sda4, automatically sda5 and sda6 are deleted too.

Thats why I asked for move (maybe bad spelled, I should have written "copy" instead) whole system to other partition.

Seems that I'll have a busy week reinstalling everything xD

---

### Post by Bucky Ball on 2012-09-16
The answer here looks promising:

[http://askubuntu.com/questions/20460/move-installation-to-new-disk](http://askubuntu.com/questions/20460/move-installation-to-new-disk)

You'd need to get your details and change the details here, naturally.

You can't expand the extended partition then the logical partition in it?

---

### Post by malspa on 2012-09-16
> **Bucky Ball said:**
> The answer here looks promising:

[http://askubuntu.com/questions/20460/move-installation-to-new-disk](http://askubuntu.com/questions/20460/move-installation-to-new-disk)

As you can see if you follow that link, it can definitely be done, and there are different approaches for doing it.

I'm not sure if it would be best for the OP's situation, but a few different times now, I've used **rsync** from a live session to move Linux installations from one set of partitions to another (I wrote "one set of partitions" because I normally have separate / and /home partitions). For example, copying from sda3 to sda6, I used:

```
# rsync -av /mnt/sda3 /mnt/sda6
```

In this case, I was using a Mepis live CD, and the partitions were mounted in /mnt. If I had been using a Ubuntu live disk, I think it would have been /media instead of /mnt.

---

### Post by elemenophee on 2012-09-16
> **Bucky Ball said:**
> The answer here looks promising:

[http://askubuntu.com/questions/20460/move-installation-to-new-disk](http://askubuntu.com/questions/20460/move-installation-to-new-disk)

You'd need to get your details and change the details here, naturally.

You can't expand the extended partition then the logical partition in it?
seems so, I guess a 2h cp is coming xD

ty

---

