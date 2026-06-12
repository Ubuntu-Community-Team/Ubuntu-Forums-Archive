---
title: "How to display my /home partition in Nautilus?"
date: 2009-12-10
forum: General Help
---

### Post by OldGrantonian on 2009-12-10
I have dual-boot Windows XP and Karmic.

My Karmic is only a few weeks old, with only a few of my files. So this is the best time to try disaster recovery. 

I backed up the following folders to an HDD:

/home
/etc
/usr/local
/var 

I had two XP partitions, and three Ubuntu partitions:

Linux swap
/
/home

From the ISO CD, I re-installed Ubuntu, and mounted it on "/"

The other existing partitions were unchanged.

After reboot, when I click "Home" in "Places" in Nautilus, the folder is empty apart from all the default stuff.

My old /home partition is visible as "30GB file system". All my files are still on this partition.

What do I need to do so that my /home partition will appear under "Places" in Nautilus?

---

### Post by rahilm on 2009-12-10
when you re-installed ubuntu, did you place /home on your home partition?
this tells ubuntu to use that partition as /home instead of creating another one

---

### Post by OldGrantonian on 2009-12-10
> **rahilm said:**
> when you re-installed ubuntu, did you place /home on your home partition?
this tells ubuntu to use that partition as /home instead of creating another one

I only made a decision about one partition. From the list of partitions, I selected the partition that I knew was the "old" system partition. I asked for "ext4 journaling". I selected a mount point as "/".

I think you are suggesting that I could have also selected the "old" home partition and specified a mount point of "/home".

I'm quite willing to re-install yet again, for future experience.

But I suspect (I'm no techie) that the "old" home partition, with all my files (only a few) will be overlaid with a new home partition containing the default directories.

(That actually doesn't matter, because I've backed up the home partition to HDD.)

I think I've been assuming that I could use some geekie Linux commands to permanently "re-attach" my old home partition :)

---

### Post by rahilm on 2009-12-10
Be sure when you specify /home to one partition, remove check for 'format this partition'.
That way your partition won't get formatted and you will retain all your data.

I did that with the ' / ' partition once and ubuntu replaced everything there was originally but was intelligent enough to keep my /home folder untouched.

---

### Post by louieb on 2009-12-10
> I think I've been assuming that I could use some geekie Linux commands to permanently "re-attach" my old home partition :smile:

\\:D/Old geeks (dinosaurs)  have there ways.

By messing with the file /etc/fstab - you can reattach your old home to your new install. - Thats  assuming you kept the same user id. 
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")

If you need some help please post the content of /etc/fstab.

and the output of the following commands.
```
sudo fdisk -l 
sudo blkid -c /dev/null 
```

from the fdisk or blkid  output you will need to figure out which partition held your old home - then you change or add a mount point in /etc/fstab to use it.

---

### Post by OldGrantonian on 2009-12-10
Well now. This is embarrassing :(

After waiting all day to make my first post, I get several hits at the same time. Like Tiger Woods :)

> **rahilm said:**
> Be sure when you specify /home to one partition, remove check for 'format this partition'.
That way your partition won't get formatted and you will retain all your data.


I tried this immediately. It works :)

> **louieb said:**
> By messing with the file /etc/fstab - you can reattach your old home to your new install. - Thats assuming you kept the same user id.

Thanks for the advice :)

For my own benefit, I'm now trying to figure out the easiest way to test your idea without having two do several more re-installs.

Maybe I could use your idea to "unattach" my /home partition, and then "re-attach" it.

I think the question I have is this. If I had tried your idea first (before trying rahilm's idea), what would have happened to the directory that is currently called /home?

Would it be overwritten and simply disappear for ever? Or would I have two /home directories? One would be my "old" /home directory with all my own files. The other would be the "new" /home directory with the default directories.
.

---

### Post by louieb on 2009-12-10
> **OldGrantonian said:**
> , what would have happened to the directory that is currently called /home?

the /home directory will still be there and the data in it will still be there.  

> **OldGrantonian said:**
> 
Would it be overwritten and simply disappear for ever? Or would I have two /home directories? One would be my "old" /home directory with all my own files. The other would be the "new" /home directory with the default directories..

The 64 thousand dollar question. -  In your case - I'm not sure - If you could post the output of the commands I gave earlier - I could give you a better answer.

It could disappear  if you do not now have a separate /home partition.  The data would still be there taking space but you would not be able to get to it.

If you still have a separate /home partition. one you switch /home to the other partition. The partition that was home will show up in the places menu  as " "<some>GB file system". 

The difference  being is how /home is used. - either as a directory in the main file system - or - as the mount point for another partition.

---

### Post by oldfred on 2009-12-10
There are a lot of instructions on how to "move" home from root to a separate partiton. They also explain the process of mounting & unmounting home to get it to work.

One of many 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by OldGrantonian on 2009-12-11
Thanks to everyone for all the help so far :)

> **louieb said:**
> 

[quote=OldGrantonian]
                                                                  [I]Would it be overwritten and simply disappear for ever? Or would I have two /home directories? One would be my "old" /home directory with all my own files. The other would be the "new" /home directory with the default directories..
[/I]

The 64 thousand dollar question. -  In your case - I'm not sure - If you could post the output of the commands I gave earlier - I could give you a better answer.
[/quote]

Here are the results of your commands. Remember that all this is now theoretical, because I used rahilm's suggestion and simply re-installed Ubuntu, mounting the "old" /home partition at the same time.

```

sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1923    15446466    7  HPFS/NTFS
/dev/sda2            1924        4598    21486937+   7  HPFS/NTFS
/dev/sda3            4599        9729    41214757+   5  Extended
/dev/sda5            4599        5149     4425876   82  Linux swap / Solaris
/dev/sda6            5150        6430    10289601   83  Linux
/dev/sda7            6431        9729    26499186   83  Linux


``````

sudo blkid -c /dev/null

/dev/sda1: UUID="6C6C88476C880DD0" TYPE="ntfs" 
/dev/sda2: UUID="648EB39C8EB36568" TYPE="ntfs" 
/dev/sda5: UUID="958fd681-2f7b-46f3-a00c-17b8975f8043" TYPE="swap" 
/dev/sda6: UUID="69d57984-7d49-4512-8789-ce9ace05e19f" TYPE="ext4" 
/dev/sda7: UUID="7e65945e-9acb-43cf-936c-0d752da69c1d" TYPE="ext4" 

```sda1, sda2 are Windows XP and a data partition
sda6 is Ubuntu
sda7 is the home partition

---

### Post by louieb on 2009-12-11
> My old /home partition is visible as  All my files are still on this partition.So you no longer have  a  "30GB file system". showing up in the places menu?. 
> Remember that all this is now theoretical, because I used rahilm's suggestion and simply re-installed Ubuntu, mounting the "old" /home partition at the same time.
Anyway you could have done the same thing by adding this to **/etc/fstab** - in fact if you look at the file now you should see a couple of lines that look very similar to this.
```

# /dev/sda7
UUID=7e65945e-9acb-43cf-936c-0d752da69c1d /home           ext4    defaults        0       2

```:D Good luck and safe surfing.

---

### Post by OldGrantonian on 2009-12-11
> **louieb said:**
> So you no longer have a "30GB file system". showing up in the places menu?.

That's correct :)

In "Home Folder", I see all my old files.

[quote=louieb]Anyway you could have done the same thing by adding this to /etc/fstab - in fact if you look at the file now you should see a couple of lines that look very similar to this.
```

# /dev/sda7
UUID=7e65945e-9acb-43cf-936c-0d752da69c1d /home           ext4    defaults        0       2

```[/quote]

You're right again :)

```

# / was on /dev/sda6 during installation
UUID=69d57984-7d49-4512-8789-ce9ace05e19f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7e65945e-9acb-43cf-936c-0d752da69c1d /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=958fd681-2f7b-46f3-a00c-17b8975f8043 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```So I'll know the easy way to do this in future.

Thanks for your help :)

---

