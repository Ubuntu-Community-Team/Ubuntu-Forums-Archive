---
title: "Question about a Unique Partition Model for /home"
date: 2009-11-27
forum: General Help
---

### Post by crazyness003 on 2009-11-27
Hi all,

I just recently upgraded (clean install) to 9.10, and judging by the looks it's pretty neat.

Onto business:
I left [FONT=Fixedsys]/home[/FONT] within [FONT=Fixedsys]/[/FONT] but was wondering if i can move [FONT=Fixedsys]/home[/FONT] to another partition without dedicating that entire partition to [FONT=Fixedsys]/home[/FONT]

instead of mounting (ex.) [FONT=Fixedsys]/dev/sda2[/FONT] as [FONT=Fixedsys]/home[/FONT] I was wondering if it it possible to mount a folder inside of [FONT=Fixedsys]/dev/sda2[/FONT] as [FONT=Fixedsys]/home[/FONT]

Basically: is there a way to specify [FONT=Fixedsys]/dev/sda2**/folder** as /home[/FONT]

Or if I should approach this in another way entirely?

Example: can I use symlinks to just point [FONT=Fixedsys]/home[/FONT] to another folder on another partition?

I don't even know if I'm explaining this correctly. If anyone can give me a heads up, or needs further clarification, just let me know. I just dont want to dedicate all of [FONT=Fixedsys]/dev/sda2[/FONT] to [FONT=Fixedsys]/home[/FONT], since I wanna install another distro and do the same thing; without them conflicting with each other, and without setting up 2 different partitions.

---

### Post by coffeecat on 2009-11-27
I don't think you can mount a folder to a mountpoint - you have to mount a device. With a separate partition for home, you mount - say - /dev/sda2 to an empty /home folder in your root partition. So, you won't be able to mount /dev/sda2/folder to the root partition /home.

Yes, you can symlink folders in another (mounted) partition to your /home/*username* in the root partition. That's a good way of going about it. I often do that myself with a shared data partition, so that /music (say) is available in Ubuntu, another distro and Windows (with a shortcut).

But I have another way if you want two distros to have entirely independent home folders but both mounted on /dev/sda2. It's easy. When you create the user accounts, give them different names. You could have bill in Ubuntu and fred in Fedora. Both Ubuntu and Fedora will be able to see the /bill and /fred folders in /home in the filesystem, but if you open home in Ubuntu, you'll go to /home/bill, and in Fedora you'll go to /home/fred.

---

### Post by crazyness003 on 2009-11-27
that's interesting.
So with different names they can still rw from each other?
oh, and when I do install my other distro (whatever it may be) all I have to do is NOT format my /home partition, and it will just add things in there like delicious pie?

What if I wanted to get rid of my secondary distro and make a new one, is there anything special to do to that distro's /home?

Also, since symlinks *should* work, can I symlink the entire *home* folder to the data partition, since I want documents and app-configurations to me housed there as well?

And am I too late in the game do achieve this (since I already have / and /home on 1 partition)?

---

### Post by coffeecat on 2009-11-27
> **crazyness003 said:**
> So with different names they can still rw from each other?

It depends. The first created user in Ubuntu, other Debian derivatives and openSUSE is 1000. In Fedora and Mandriva (last time I checked) it's 500. If the UID is different, you will run into permission problems.

> **crazyness003 said:**
> oh, and when I do install my other distro (whatever it may be) all I have to do is NOT format my /home partition, and it will just add things in there like delicious pie?

You'll have to tell it to use the separate partition for /home and it *should* set up the mount for you and create the account. But I'm not guaranteeing what other distro's installers will do. And I'm not making any guarantees about the Ubuntu installer either. :wink:

> **crazyness003 said:**
> What if I wanted to get rid of my secondary distro and make a new one, is there anything special to do to that distro's /home?

Um - I don't know. If that secondary distro's user was bert and you replaced that distro with another and setup a new user cecil, then /bert would simply stay there until you deleted it. I guess. :?

> **crazyness003 said:**
>  Also, since symlinks *should* work, can I symlink the entire *home* folder to the data partition, since I want documents and app-configurations to me housed there as well?

I think it would be a nightmare symlinking the large number of hidden configuration files and folders. I wouldn't even attempt it. No - it wouldn't work. Every time you installed a new app that needed its own hidden config folder, it would create it in your root partition /home, not in the data partition.

> **crazyness003 said:**
> And am I too late in the game do achieve this (since I already have / and /home on 1 partition)?

That's doable, but somewhat challenging. Say you have /home/norbert in your root partition. You need to copy /norbert + contents to /dev/sda2, remove /norbert + contents from the original /home folder and add a line to fstab so that /dev/sda2 is mounted to /home. But that's not the end of the story. If /dev/sda2 is ext3/4 (as it should be) you can't just copy /norbert/* - you'll run into permissions problems. And don't copy them as sudo/root - the whole of /norbert will end up owned by root. At the moment it's too late here for me to think this one through, so I'll stop there and hopefully someone else can come in on this point. But I'll check this thread tomorrow.

---

### Post by crazyness003 on 2009-11-27
Thanks, I appreciate the help thusfar.

I presume you cant just symlink /home. Can it be done recursively, so that anything that tries to make a folder in /home will be jumped to the data partition and make it there?

I'll try to figure this stuff out another day as well. I think I jumped the gun when I installed. I shoulda done more research.

Again thanks

---

### Post by scorp123 on 2009-11-27
> **crazyness003 said:**
>  Basically: is there a way to specify [FONT=Fixedsys]/dev/sda2**/folder** as /home[/FONT]


Something like this?

```
sudo mount -o bind /path/to/folder1 /home
```

---

### Post by nerdopolis on 2009-11-27
you can "mount" folders. you need to use the --bind option

example:
```
sudo mount --bind /path/to/source_folder /path/to/target_folder
```
If you were to cd into /path/to/target_folder then run ls, all the files will be from /path/to/source_folder. 

If you where to run ls within /path/to/source_folder, it will still be all the files under /path/to/source_folder. 

If you where to create a file in /path/to/target_folder, it will write it to /path/to/source_folder, but will be accessible from /path/to/target_folder. 

If you were to create a file in /path/to/target_folder, it will write the file to /path/to/target_folder, and will still be accessible from /path/to/source_folder 


all you need to do is change the names of the folders in the above command


Edit: **scorp123 **beat me to it. I didn't mean to do a duplicate post.

---

### Post by crazyness003 on 2009-11-27
> **scorp123 said:**
> Something like this?

```
sudo mount -o bind /path/to/folder1 /home
```
can this be added to fstab? if so, how?

```
/dev/sda2 /mnt/data ext3 default 0 0
/mnt/data/folder /home ext3 default 0 0
```

I dont know where to add bind.

---

### Post by nerdopolis on 2009-11-27
from **SilentRage** at [http://www.linuxforums.org](http://www.linuxforums.org)  ([http://www.linuxforums.org/forum/servers/28252-fstab-mount.html](http://www.linuxforums.org/forum/servers/28252-fstab-mount.html))

> ```
/my/real/dir /to/mount/dir            none rw,bind 0 0
```


---

### Post by crazyness003 on 2009-11-27
Awesome Sauce. Thank you gentle-people. Your infinite cumulative knowledge has enlightened a lost soul, and set him on a path of righteousness.

Of course I do thank you for the knowlege, I have yet to try this procedure out. I will report in any case.

Again. Thank you(s).

---

### Post by crazyness003 on 2009-11-27
Just wanted to get back and say: ALL IS A GO! It worked, holy crap it worked. Thanks again guys. Super internet cookies *and* pie for all of you!

Just to let people see: my fstab (and all of it's glory) nevermind the bizzaroness, its weird.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# / was on /dev/sdc3 during installation
UUID=f39cba46-8609-4fc0-a969-c81ee1d2be18 /               ext3    relatime,errors=remount-ro 0       1

# /boot was on /dev/sdc1 during installation
UUID=4094425e-60ca-4c54-9c26-27ff10307c3e /boot           ext3    defaults        0       2

# swap was on /dev/sdc6 during installation
UUID=d171f6a3-21bb-41e6-a919-221edcea5c71 none            swap    sw              0       0

[B]## Manual Entry 20091127
# /data was on /dev/sdc7 during and after installation
UUID=baec14e1-2b15-40be-a789-0fe1f4a7727a /media/data     ext3      defaults      0      2

## Manual Entry 20091127
# /home was on /home but I decided to move it another place after installation
/media/data/.home-1_9.10 /home                            none      rw,bind      0      0[/B]  

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I verified this by placing a little text file in the new destination (after the copy over) titled 'SUCCESS'. The old /home location did not have this file. So, after a restart, I was able to successfully boot right back in and when I used the Places -> Home Folder approach in gnome: lo, there it was; sweet success!

I dont know if i have all of the mount options at efficient values, but it works.

I hope others can learn from this, and I thank all of you that helped me out.

---

