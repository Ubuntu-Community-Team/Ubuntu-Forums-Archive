---
title: "Space for new 1TB Hard Drive?"
date: 2012-06-08
forum: General Help
---

### Post by sports fan Matt on 2012-06-08
..and I was wondering what y'all thought would be enough space to place 12.04 on?  I don't do a whole ton of configurations, just simply change pictures/themes every now and again. This is the 1st time with a larger drive so I don't want to half it. Suggestions are welcome!  

Matt

---

### Post by sports fan Matt on 2012-06-08
I was thinking 12-15 gigs.  :)

---

### Post by WorMzy on 2012-06-08
Depends on how you set it up. Most linux distributions will use less than 5GB for /, but if you don't have a dedicated data partition (for user documents, etc) then you'll probably need a much larger partition for /.

For example here's how much space I'm using, and where:

```
Filesystem Mount                                                             Size     Used    Avail %Used  fs Type 
/dev/sda1  /                                                                20.0G     1.6G    17.4G   13%  btrfs   
tmpfs      /home/wormzy/.cache                                               1.0G     0.0G     1.0G    0%  tmpfs   
/dev/sdb12 /home/wormzy/.mozilla/firefox                                   100.0G    35.6G    60.3G   40%  btrfs   
/dev/sdb12 /home/wormzy/.scripts                                           100.0G    35.6G    60.3G   40%  btrfs   
/dev/sdb12 /home/wormzy/.weechat                                           100.0G    35.6G    60.3G   40%  btrfs   
/dev/sde1  /home/wormzy/Collection                                         931.5G   361.0G   570.5G   39%  fuseblk 
/dev/sde1  /home/wormzy/Documents                                          931.5G   361.0G   570.5G   39%  fuseblk 
/dev/sde1  /home/wormzy/Downloads                                          931.5G   361.0G   570.5G   39%  fuseblk 
/dev/sde1  /home/wormzy/Pictures                                           931.5G   361.0G   570.5G   39%  fuseblk 
/dev/sdd1  /home/wormzy/Videos                                             931.2G   570.5G   360.7G   61%  xfs     
/dev/sdb12 /home/wormzy/builds                                             100.0G    35.6G    60.3G   40%  btrfs   
/dev/sdb12 /home/wormzy/projects                                           100.0G    35.6G    60.3G   40%  btrfs   
/dev/sde1  /media/Terastore                                                931.5G   361.0G   570.5G   39%  fuseblk 
/dev/sdb12 /media/shared                                                   100.0G    35.6G    60.3G   40%  btrfs   
run        /run                                                              7.8G     0.0G     7.8G    0%  tmpfs   
/dev/sdb12 /srv/django                                                     100.0G    35.6G    60.3G   40%  btrfs   
/dev/sdb12 /srv/http                                                       100.0G    35.6G    60.3G   40%  btrfs   
tmpfs      /tmp                                                              7.8G     0.0G     7.8G    0%  tmpfs   
/dev/sdb12 /var/abs                                                        100.0G    35.6G    60.3G   40%  btrfs   
/dev/sdb12 /var/cache/pacman/pkg                                           100.0G    35.6G    60.3G   40%  btrfs   
/dev/sda1  /var/lib/btrfs-root                                              20.0G     1.6G    17.4G   13%  btrfs   
/dev/sdb12 /var/tmp/archbuild                                              100.0G    35.6G    60.3G   40%  btrfs   
tmpfs      /var/tmp/archbuild/extra-x86_64/build                            15.0G     0.7G    14.3G    4%  tmpfs   
tmpfs      /var/tmp/archbuild/multilib-x86_64/build                         15.0G     3.3G    11.7G   22%  tmpfs   
```

All in all, I'm using about a terabyte of disk space, but only 1.6GB of that is what my OS needs to boot, the rest is reusable, disposable, or user data and is kept away from the / partition.

---

### Post by sports fan Matt on 2012-06-08
If I wanted 20 GB for the home partition (since everything I have I'd carry over from Windows anyway) , how would this be done? What file system is best?  EXT 3 or 4?  (putting 12.04 on it)

I've never manually divided partitions so I'm asking questions...

---

### Post by sports fan Matt on 2012-06-08
I have Windows on the main drive so far.

---

### Post by WorMzy on 2012-06-08
You can specify partitions during the installation phase, if you choose to partition manually. Or you can create partitions in an existing installation using partitioning software (e.g. gparted), and then declare them in fstab.

ext4 is supposed to be better than ext3, but you should do your own research on that and see which is best for you.

---

### Post by patrickceg on 2012-06-08
> **sox fan Matt said:**
> If I wanted 20 GB for the home partition (since everything I have I'd carry over from Windows anyway) , how would this be done? What file system is best?  EXT 3 or 4?  (putting 12.04 on it)

I've never manually divided partitions so I'm asking questions...

Remember a mistake with partitioning can ruin your data in Windows, so make a backup before playing around.

If Windows is taking up the entire drive with its C:\, then you'll want to resize it before installing Ubuntu. (Preferably using Windows itself to resize the giant partition if you have Vista or later.)

Any of the Ubuntu installers will allow  you to partition the way you want. Select to manually partition in the installer when it asks about partitions. (See [https://help.ubuntu.com/community/WindowsDualBoot#Manual_partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual_partitioning))

Then set up a simple scheme like listed below:
/ (ext4) ~10GB
/home (ext4) 20GB (as you asked)
swap (at least the size of your RAM unless your needs are different)

Ext4 is Ubuntu 12.04's default, so there's no reason not to choose that if you are unsure. Other filesystems can give performance benefits but it'll be hard to notice doing "normal" desktop activities on a midrange 1TB drive.

Further reading:
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by sports fan Matt on 2012-06-09
That's about what I thought-just wanted to give it enough space.  So If I have 2 gigs of ram, can i just put in 2 gigs and it will figure it out?

---

### Post by jmore9 on 2012-06-09
I use 30 gig and put everything in / .  That leaves all the rest of whatever it is for files , games , etc.  Also store backups there.  When i need to do clean install most of my files are safe on the other partitions , same for upgrades put everything on the other partiton and very little worry.

---

### Post by Paqman on 2012-06-09
> **sox fan Matt said:**
> That's about what I thought-just wanted to give it enough space.  So If I have 2 gigs of ram, can i just put in 2 gigs and it will figure it out?

Er, I don't quite understand what you mean. The amount of RAM you have doesn't really have any bearing on partition sizes.

If you have plenty of space I would go for at least 20GB. You can get away with 10GB (or even 5GB at a squeeze) but some jobs like authoring DVDs will create multi-GB files in /tmp so it doesn't hurt to have some spare room.

It really depends where you're putting your data. If you're putting it elsewhere then 20GB is tons. Another thing to watch out for is Windows apps installed through Wine. Windows apps are massive, and it would all end in /home, so allow plenty of space if you're going to use Wine.

---

