---
title: "link /home to directory on another partition..."
date: 2011-12-12
forum: General Help
---

### Post by greylander on 2011-12-12
I can find easily instructions to mount a partition to /home, thus making /home an entire partition.

However, i would like if possible to link /home to a directory on another partition, rather than have it be the entire partition.

I am going to have multiple linux installs, but I want just one "home" partition, but I want each install to have its own "home" on that partition.

What is the best/safest way to do this?

Basically I imagine I will mount the partition somewhere other than home, like /mnt/home_partition.  On that partition there may be several directories, /home1, /home2, etc.  So I can I just link like this:

```
ln -s /mnt/home_partition/home1 /home   ?????
```

Should it be (can it be) a hard link rather than symbolic?

How do I make this happens at boot time without causing problems?

Thanks.

---

### Post by nothingspecial on 2011-12-12
The way I do it is to have a seperate data partition and mount(bind) thae directories to my $HOME like this


```
LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/backup  /home/nothingspecial/backup  none  bind  0  0
/media/data/bin  /home/nothingspecial/bin  none  bind  0  0
/media/data/Documents  /home/nothingspecial/Documents  none  bind  0  0
/media/data/Downloads  /home/nothingspecial/Downloads  none  bind  0  0
/media/data/elinks  /home/nothingspecial/elinks  none  bind  0  0
/media/data/images  /home/nothingspecial/images  none  bind  0  0
/media/data/Music  /home/nothingspecial/Music  none  bind  0  0
```

So the settings for each install are different but the data is the same, if you see what I mean.

---

### Post by greylander on 2011-12-12
These don't look like commands, so are these entries in /etc/fstab?  Or somewhere else?

I'm looking at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) to get an idea.

However, the syntax they show is

```
[Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]
```

But your code shows paths to directories within your data partition, not just to device/partition itself.

I think that in fstab, if for "[device]" I could do "[device/path]" that would be getting at what I want, but I don't think that is possible.

---

### Post by spiky001 on 2011-12-12
If your going to install multible OS they are best having there own homes. then just link to a data partition for storage only

---

### Post by nothingspecial on 2011-12-12
> **greylander said:**
> These don't look like commands, so are these entries in /etc/fstab?  Or somewhere else?

I'm looking at [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) to get an idea.

However, the syntax they show is

```
[Device] [Mount Point] [File System Type] [Options] [Dump] [Pass]
```

But your code shows paths to directories within your data partition, not just to device/partition itself.

I think that in fstab, if for "[device]" I could do "[device/path]" that would be getting at what I want, but I don't think that is possible.


Sorry.

Yes they are entries in /etc/fstab

Basically you mount the Data partition to wherever, then bind the individual directories to you $HOME

I should have been clearer.

---

### Post by greylander on 2011-12-12
So then I could also mount the data partition wherever and then bind /home to a path on that partition, right?  So something like...

```

LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/home_Ubuntu_1 /home  none  bind  0  0
```

then in my kubuntu install...

```

LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/home_Kubuntu /home  none  bind  0  0
```

and in another ubuntu install...

```

LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/home_Ubuntu_2 /home  none  bind  0  0
```

...and so forth.  Yes?

The critical thing is that "yes", <device> in fstab can refer to paths (subfolders) on the device, not just to the whole device.

Also, I didn't know fstab can reference device by label.  Cool.

Does my understanding sound correct?  Are there any "gotchas" I should worry about?

Thx.

---

### Post by nothingspecial on 2011-12-13
The point of the way I do it is to keep the configurations seperate. There are very few applications I use with all the installations. So my /home is different on each installation.

For example, I have Lubuntu on an 8 gig usb stick. Using it at home on my netbook, it mounts all the data on the hard disk as well as my music, videos and photos stored on my server. But if I take the stick out and boot it on a different computer it still has all my settings (bookmarks etc).

So at home I get

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             7.4G  4.1G  3.0G  58% /

```

My root partition including /home with all my settings is just over 4 gigabytes but

```
du -h ~

```

After about 10 minutes gives me

```
1.9T	/home/nothingspecial

```

Nearly 2 terabytes of data.

---

### Post by greylander on 2011-12-13
Point taken on the /home for root partitions of flash drive, etc.  That's a good tip.

I am mainly thinking about multiple root partitions on fixed drives in same machine right now.

It is weird but there is nothing about the "bind" option or syntax in the man page for fstab, nor here  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), nor here [http://ubuntuforums.org/search.php?searchid=84541381](http://ubuntuforums.org/search.php?searchid=84541381) (in the OP... a search for 'bind' turns up someone mentioning it deep in the thread).  All of those documents only show referencnig partitions in the [device] parameter, not paths to directories.

Anyway, now that I know how to make fstab do my bidding, I just have to decide exactly what I want.

Thanks for all the help!

---

### Post by oldfred on 2011-12-13
there is a HowTo and several posts:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472) 

I just link each folder into /home but the bind method supposedly works better in some circumstances.

I just have to add one mount in fstab and run this:
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

If using different distributions be aware of UID & GID issues:
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

