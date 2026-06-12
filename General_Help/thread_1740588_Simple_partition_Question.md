---
title: "Simple partition Question"
date: 2011-04-27
forum: General Help
---

### Post by Ronalddig on 2011-04-27
guys , my query :

I have  2 partition swap and / (root )


but now i see in forum  that people suggest that you should make separate partition for /home.

my question is Lets say I  have separate partition for /home , and now I decide to do fresh install of new release

1. do i delete only swap and root (for fresh installation and preserve /home) ?
2. on fresh installation, do i only make swap and / partition, so  home partition be visible to it (from previous installation )

3. so how much space should be given to root then ?

---

### Post by nothingspecial on 2011-04-27
1 Yes
2 Yes
3 About 10-15 gigs

If your talking about natty, during the installation at the partitioning bit, choose "something else".

Choose your root partition and choose to use it as an ext4 journaling file system, give it a mountpoint of /,  check/tick the format box.

Choose you home partition and choose to use as whatever file system it is. Give it a mountpoint of /home but

[COLOR="Red"][SIZE="3"]DO NOT CHECK/TICK THE FORMAT BOX[/SIZE][/COLOR]

Just choose to use the swap space as swap, no need to format.

It's the same for previous versions, it's just not called "some thing else", it's called advanced or manual or something like that.

---

### Post by MARP1961 on 2011-04-27
The benefit of having a separate '/Home' parition is that personal settings and files are preserved if you want to reinstall Ubuntu (or even another Linux disro). However, do not depend absolutely on this technique to preserve data. It is always wise to make backups before reinstalling and playing with partitions.

If you wish to install with a separate '/Home partition then choose the manual or 'advanced' install to set up your own partitions. 20GB is more than ample for the Root partition and Swap should be around twice your RAM. Give as much space as you can afford to your new Home partition which will hold your data files.

If you ever wish to reinstall then you just pop in a live disk, boot from it and select manual partitioning. You click on the Root partition and change it (select ext 4 journalling file system, mount it as / and check the box to format it. Then you select the Home partition, click change and once again select ext4 as an option but **most importantly make sure you leave the ****box for formatting empty, do not format the Home partition you have used which is full of data and settings you wish to keep.** Finally click on Swap and keep it as it is (no mount point) just select Swap.

You will find that reinstallation is now quicker.

---

### Post by Ronalddig on 2011-04-27
thanks guys for the solution , :P

---

