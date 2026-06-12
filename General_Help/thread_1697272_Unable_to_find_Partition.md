---
title: "Unable to find Partition"
date: 2011-02-28
forum: General Help
---

### Post by Aesthria on 2011-02-28
Hello, I am very new to Linux and not exactly sure how to go about this. I recently installed Ubuntu 10.10 on my computer from Windows 7. Originally my Hard Drive was Split into two separate partitions. One was for the OS and the other was basically a storage drive. During the install of Ubuntu I deleted the OS Partition, Installed Ubuntu in that Partition, and used my Storage partition as a Swap.

After the install was complete Ubuntu loaded great and works just fine, the only issue is I can't find the other Partition where all my files were stored.

Is there any way to locate this partition and access it as you would with Windows Computer>D:>etc or is there some other way to go about this?

---

### Post by Hedgehog1 on 2011-02-28
Welcome Aesthria!

We need to get a look at your disk partitions to help you.

In the Terminal (Menu to: Applications >> Accessories >> Terminal)

please run this command:  (the -l is a lower case 'L')

```
sudo fdisk -l
```

Then copy the text from the output and paste it in your next post.

***The Hedge...***

:KS

---

### Post by Aesthria on 2011-02-28
Alright, here's that bit of info.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7919a62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        1306       20110   151040001    5  Extended
/dev/sda3           20110       38914   151042048   82  Linux swap / Solaris
/dev/sda5            1306       20110   151040000   83  Linux

---

### Post by Hedgehog1 on 2011-02-28
> **Aesthria said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        1306       20110   151040001    5  Extended
/dev/sda3           20110       38914   151042048   82  Linux swap / Solaris
/dev/sda5            1306       20110   151040000   83  Linux


Aesthria,

I think you needed to press enter to get more to list in the terminal.  You you try again, please?

:confused:

---

### Post by Aesthria on 2011-02-28
That appears to be all the info it's going to give me. Not too sure what else should be there.

---

### Post by Hedgehog1 on 2011-02-28
> **Aesthria said:**
> Alright, here's that bit of info.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7919a62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        1306       20110   151040001    5  Extended
/dev/sda3           20110       38914   151042048   82  Linux swap / Solaris
/dev/sda5            1306       20110   151040000   83  Linux

I was afraid of that. Drat.

Well, the bad news is your disk is rather messed up.  The good(ish) news is you may be able to recover the shared data partition (unless you have a backup of that data?)

here is what this listing tells us:
> 
   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]--> Sectors 1-1305 are not being referenced[/COLOR]
/dev/sda2   *        1306       20110   151040001    5  Extended [COLOR="Lime"]--> This parition is a locigal one, and /dev/sda5 lives inside it[/COLOR]
/dev/sda3           20110       38914   151042048   82  Linux swap / Solaris[COLOR="lime"]--> Your swap space[/COLOR]
/dev/sda5            1306       20110   151040000   83  Linux[COLOR="lime"]--> Your linux data partition[/COLOR] 


I expect your missing data was in /dev/sda1.

It is still on the disk (most likely) - but nothing is pointing to it right now.

There is a tool to recover this, it is called testdisk.  It must also be run from the terminal:

```
sudo testdisk
```

You will have to load testdisk using the Ubuntu Software Center.

---

### Post by Hedgehog1 on 2011-02-28
I just noticed a thread nearby of someone else using testdisk for the first time, and folks helping him:

[http://ubuntuforums.org/showthread.php?t=1696531]("http://ubuntuforums.org/showthread.php?t=1696531")

I expect he is asking many of the same question you are about to.

Take a read of it before you try running testdisk yourself. It might save you some suffering.

:KS

---

### Post by Aesthria on 2011-02-28
sda1 Was a 10gb Partition where Vista was housed, Deleted that Partition so now it's free space. SDA3, Is the Partition that had All of the files and became unusable. Would there be any way to Delete the partition and merge it with the current one I'm using for more File space? At this point I'm not too worried anymore about the files, and more about Disk Space.

I know Disk Utility has the ability to Delete Partitions or change Partition type, I'm just not sure how to go about making it usable after that point. Perhaps deleting it, and then formating it again?

Thank you so far for your assistance =)

---

### Post by Hedgehog1 on 2011-02-28
Right now your computer is using sda3 as swap space.

Also, because sda2 is a logical partition filled with sda5, you need to extend the logical partition before you can extend sda5.

If your situation allows, can you do a clean install? We can set you up so this is less likely to happen again, as well.

In the manual setup when using the 'entire disk' of the install, you would break up your 320 gig hard driver this way:

/sda1 would be 20 gigs, and it would hold '/' and '/boot'.
/sda2 would be 290 gigs, and it would hold '/home'
/sda3 would be whatever is left, and made 'lunix swap'

By seperating your system ('/' and boot '/boot') from your data ('/home'), you can change/upgrade Distros with much less risk to your data.

You will need to backup your current data, but would be in better shape from then on.

What do you think?

:KS

---

### Post by Aesthria on 2011-02-28
Sounds like a good plan. Somewhere along the line my other Partition became corrupt. So a clean Full disk install would be the way to go. Will do that now and see how it goes.

---

### Post by Hedgehog1 on 2011-02-28
Let us know how it goes.

You can surf the forums from the LiveCD while you install.

*p.s. If you don't assign a specific partition as '/boot', it will go into the the '/' partition, and that is the same as assigning both to /sda1*

:KS

---

