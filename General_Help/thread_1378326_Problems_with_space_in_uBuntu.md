---
title: "Problems with space in uBuntu"
date: 2010-01-11
forum: General Help
---

### Post by iPhoneB on 2010-01-11
Hello,

If anyone can help on this would be great... as i can't figure it out...

Yesterday I installed ubuntu inside windows in 3 computers 2 of the computers run windows 7 the one at work runs XP professional, 1 of the computers is going to be running as a media server to stream movies across the PLAYSTATION 3 and i like it because is stable.

Now before i istalled ubuntu, i partitioned my windows hdd. The total on my hdd is 250gb so xp has like 50 gig, and is installed under C:/ i made a partition with like 30 gigs for ubuntu (more than it needs to install little apps, like a Java PS3 media server etc..) and i have about 200 GB unallocated space..

[COLOR=Orange]Now here is a screenshot of GParted[/COLOR]
[IMG]http://albfriend.com/uploads_user/1000/213/290.jpg[/IMG]

Now a folder in the File system called /host has the 28 gb of freespace that i gave to ubuntu.. and i am running out of space.

[COLOR=Orange]Here is a screenshot of File System[/COLOR]
[IMG]http://albfriend.com/uploads_user/1000/213/291.jpg[/IMG]

Here is what sudo fdisk -l shows...
[COLOR=Red]
Disk /dev/sda: 300.1 GB, 300090728448 bytes
240 heads, 63 sectors/track, 38764 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xd2edf57b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5283    39939448+   7  HPFS/NTFS
/dev/sda2            5284        9414    31230360    7  HPFS/NTFS
[/COLOR]
Here is what  df -h shows...

[COLOR=DarkOrchid]Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            4.6G  2.5G  2.0G  56% /
udev                  1.5G  240K  1.5G   1% /dev
none                  1.5G  296K  1.5G   1% /dev/shm
none                  1.5G  100K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda2              30G  5.7G   25G  19% /host
[/COLOR]
As you can see all my 30 GB is going for [COLOR=DarkOrchid]/dev/sda2              30G  5.7G   25G  19% /host


[COLOR=Black]This is what is going on on my machine right now, i can't download a movie because i'm always running out of space, My Video Folder has 1.1 GB of free space?????


Any Help would be appriciated. I'm a n00b when it comes to linux.

Gracias!
Amigos!
[/COLOR]
[/COLOR]

---

### Post by warfacegod on 2010-01-11
If I were on a strictly linux machine, I would do this:

```
tune2fs -m x% /dev/sd
```
Where x = the amount of reserved drive space Ubuntu defaults at 5%. For instance, my external doesn't need a system reserve on it so I changed it to 0%

In the code you will also need to add the appropriate letter at the end of *sd*. In your case it looks like it would be sda2.

It also looks like you have room to resize the offending partition to make it bigger.

I don't have any idea how your set up will react to either suggestion so be careful.

FYI It's hard to read screenshots when they are embedded in posts, attach them instead so that we can see them in a bigger view.

---

### Post by iPhoneB on 2010-01-11
Here im attaching the screen shot of my discs. thank you

---

### Post by warfacegod on 2010-01-11
Yup, much easier to read, thanks. I would try resizing the partition first, you have over 200 GB of unallocated space to burn up.

Always be careful with Gparted, go over the steps you are taking at least twice, to make *sure* you aren't going to harm another partition. Again, I don't know how your system will react to this. I don't see why it would be an issue. Double check to be certain that the unallocated space is actually unallocated so that you aren't resizing into, say, a Windows partition that Gparted isn't seeing.

---

### Post by iPhoneB on 2010-01-11
Hello,

Is there anyway i can make this my primary  [COLOR=DarkOrchid]/dev/sda2              30G  5.7G   25G  19% /host is mounted on the folder Host.
[COLOR=Black]
Isn't there a easy way around this, for me to make the 30gb partition that i made for ubuntu as primary? THis way i'll have some room..

Any help/commands are appriciated...!

I'm stuck at this point.
[/COLOR][/COLOR]

---

### Post by warfacegod on 2010-01-11
> **iPhoneB said:**
> Hello,

Is there anyway i can make this my primary  [COLOR=DarkOrchid]/dev/sda2              30G  5.7G   25G  19% /host is mounted on the folder Host.
[COLOR=Black]
Isn't there a easy way around this, for me to make the 30gb partition that i made for ubuntu as primary? THis way i'll have some room..

Any help/commands are appriciated...!

I'm stuck at this point.
[/COLOR][/COLOR]

I'm not sure that's such a good idea.

---

### Post by iPhoneB on 2010-01-11
Hello,

Well, since there isn't anyway around this, how can i give ubuntu enough space do i need to reinstall the whole thing and give it more space?

Thank You

---

### Post by iPhoneB on 2010-01-11
Here a screenshot of the Video Folder says i only have 1.9 GB

---

### Post by iPhoneB on 2010-01-11
It didn't take the screenshot here it is..

---

### Post by warfacegod on 2010-01-11
> **iPhoneB said:**
> Hello,

Well, since there isn't anyway around this, how can i give ubuntu enough space do i need to reinstall the whole thing and give it more space?

Thank You

It's unlikely that you will need to reinstall. I sent a link to this thread to someone that knows more about this than I do (not saying that I know nothing though). I would recommend having patience until they can take a look.

If you're just too itchy about this to wait, then here:

Go to System> Admin.> Gparted> highlight the drive that needs more room (be certain it's the right one!)> right click and select unmount> right click again and select resize. You can grab the arrow on either side of the drives "picture bar" and slide it. Looks like you want to slide the right arrow. Again, be careful if you do this.

---

### Post by iPhoneB on 2010-01-11
Hello,

Thanks for the quick replay... i just did exactly what you said and i have tried this before to unmount the partition but it wont let me, i get an error saying:
[COLOR=Magenta]
Could not unmount /dev/sda2/
unmount : /host: device is busy
(IN some case useful info about proccess that use the device is found by Isof(8) or fuser(1))[/COLOR]

Thats the error and i cannot go past this screen.

Thank You

---

### Post by iPhoneB on 2010-01-11
This is from the termial

helbasani@ubuntu:~$ sudo umount /host
umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
helbasani@ubuntu:~$

---

### Post by warfacegod on 2010-01-11
> **iPhoneB said:**
> This is from the termial

helbasani@ubuntu:~$ sudo umount /host
umount: /host: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
helbasani@ubuntu:~$

It looks like that is the drive that Ubuntu is installed on. Can't unmount a drive that Ubuntu is running on, it's a logical impossibility. A resize operation would have to be done in Windows or from the Ubuntu LiveCD. I suggest Ubuntu LiveCD. My previous instructions will still apply in LiveCD (Ubuntu install disc).

---

### Post by Leppie on 2010-01-11
unfortunately i am not familiar with wubi installs (ubuntu in windows).

may i ask first of all why you want to run an Ubuntu server (stable system with very fast filesystems available) within a Windows environment (quite unstable system with slow and unreliable filesystems)? i ask this, because most of the wubi installs are on unpartitioned drives (e.g. a large file hosting the ubuntu filesystem within the windows system partition). this seems to defy the pro of a wubi install.
furthermore, in a wubi install the root of the ubuntu filesystem isn't / but /host. furthermore i believe that the /dev/loop is because you're not really mounting a partition but an image which is to serve as the filesystem. hence, both cannot be unmounted while in your ubuntu system.

furthermore, if you have installed grub to the mbr, you cannot remove ubuntu from your system by simply deleting the large file from the partition.

---

### Post by iPhoneB on 2010-01-11
Hello,

I installed ubunti inside windows because i wanted to test it first...

Anyway i booted into ubuntu LIVECD and lol i dont know what the hell i did, but i expanded the 29gb to 50 gb the formated it as ext3 and guess what? the kernel is gone lol, i cannot boot into ubuntu anymore, i get a black screen a command line like with the word grup:sh something and it wants me to enter a command which i dont know... it says hit TAB for more help options and it shows avialable commands that i can use...

Arghh...

---

### Post by warfacegod on 2010-01-11
I did warn you.

See post #8. Although this probably won't work now.
[http://ubuntuforums.org/showthread.php?t=1377175]("http://ubuntuforums.org/showthread.php?t=1377175")

If you wanted to just try Ubuntu, selecting "Try Ubuntu without making any changes" From the Install disc would have been sufficient. I suggest giving up this wubi thing and installing Ubuntu to it's own hard drive or partition.

---

