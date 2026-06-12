---
title: "Hard Drive wont stay mounted"
date: 2011-03-06
forum: General Help
---

### Post by Crazy K on 2011-03-06
I posted a topic on this before, but I thought I had it figured out. Anyways I have a 500GB External HD that keeps messing up. 

What happens is that sometimes I can't save, edit or delete files on the drive itself I also can't watch videos or listen to music when this happens. I usually unmount and remount whenever it does this, but that is starting to get on my nerves.  I need to know how to get it to stay mounted at all times and stay like that. I have it plugged in all the time to my computer. 

Some info on the drive right now, I have 88.9GB of spaced used and 376.8GB left. 

I want to fix this problem so I don't have to end up deleting everything. I have a lot of music, videos, and photos on here and I'd hate to lose all of them. 

I need you guys to walk me through this step by step, and make it as easy for me as you can. I've been using Ubuntu for 2 years now, but I still feel like a noob when it comes to most of the problems I have. 

Please help!

---

### Post by markeee on 2011-03-06
> **Crazy K said:**
> I posted a topic on this before, but I thought I had it figured out. Anyways I have a 500GB External HD that keeps messing up. 

What happens is that sometimes I can't save, edit or delete files on the drive itself I also can't watch videos or listen to music when this happens. I usually unmount and remount whenever it does this, but that is starting to get on my nerves.  I need to know how to get it to stay mounted at all times and stay like that. I have it plugged in all the time to my computer. 

Some info on the drive right now, I have 88.9GB of spaced used and 376.8GB left. 

I want to fix this problem so I don't have to end up deleting everything. I have a lot of music, videos, and photos on here and I'd hate to lose all of them. 

I need you guys to walk me through this step by step, and make it as easy for me as you can. I've been using Ubuntu for 2 years now, but I still feel like a noob when it comes to most of the problems I have. 

Please help!

you tried forcing the mount? Although I don't think that would fix it

mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force

---

### Post by Crazy K on 2011-03-06
When I go to Places, Computer, and under the devices area in the left side of the page I click on the yellow arrow. It then unmounts the drive so I can safely remove it. I usually don't remove it and I just double click on My Book again and it reloads the HD and works fine. But lately it doesn't seem to be lasting too long. 

Now is that code going to work with my EX HD? The name of it is My Book. Would sda1 be the Ex HD?

---

### Post by markeee on 2011-03-06
> **Crazy K said:**
> When I go to Places, Computer, and under the devices area in the left side of the page I click on the yellow arrow. It then unmounts the drive so I can safely remove it. I usually don't remove it and I just double click on My Book again and it reloads the HD and works fine. But lately it doesn't seem to be lasting too long. 

Now is that code going to work with my EX HD? The name of it is My Book. Would sda1 be the Ex HD?

it should work with your external USB hd yea, sda1 would be the ex hd

I'm assuming there, that you're using it as NTFS

as to sda1 - this might not be what your device is - type fdisk -l to see the device id

then the command

mount -t ntfs-3g /dev/deviceNAME /mountpoint -o force

---

### Post by Crazy K on 2011-03-06
I used GParted to find out what file system it was using, and it's a fat 32 and on the left under partition it says dev/sdb1 so I'm guessing the first command is correct in this case.

---

### Post by markeee on 2011-03-06
> **Crazy K said:**
> I used GParted to find out what file system it was using, and it's a fat 32 and on the left under partition it says dev/sdb1 so I'm guessing the first command is correct in this case.

ok, try

mount -t vfat /dev/sdb1 /media/fat32

---

### Post by Crazy K on 2011-03-06
Now will it stay mounted if I do this?

---

### Post by Crazy K on 2011-03-06
Just did that command and I got this: ```
mount point /media/fat32 does not exist
```

Should I try the first command you posted?

---

### Post by markeee on 2011-03-06
> **Crazy K said:**
> Now will it stay mounted if I do this?

im not entirely sure

but add force to it and lets see


mount -t vfat /dev/sdb1 /mountpoint -o force

---

### Post by markeee on 2011-03-06
> **Crazy K said:**
> Just did that command and I got this: ```
mount point /media/fat32 does not exist
```

Should I try the first command you posted?

sudo mkdir /media/fat32 - thats just to create somewhere to mount the drive

---

### Post by Crazy K on 2011-03-06
I get this when I do the first command: ```
mount point /mountpoint does not exist
```

---

### Post by Crazy K on 2011-03-06
Also, did the very first command you suggested, and I got this: ```

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

---

### Post by markeee on 2011-03-06
> **Crazy K said:**
> Also, did the very first command you suggested, and I got this: ```

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

ok , the first command was when I thought your drive was NTFS - sorry if I said the first command

needs to be the one with vfat as the type and its /dev/DEVICENAME (sda1) in the example..so yours would be sdb1


sudo mkdir /media/fat32 -- do that to create somewhere to mount your fat drive

second command is to mount the device

mount -o filetype /dev/DEVICE /mountpoint

so for you

mount -o vfat /dev/sdb1 /media/fat32 (after you create /media/fat32)

make sense? :)

---

### Post by Crazy K on 2011-03-07
Yeah I think I got it. It's staying mounted right now, so if I encounter anymore problems I'll update this thread.

---

### Post by markeee on 2011-03-07
> **Crazy K said:**
> Yeah I think I got it. It's staying mounted right now, so if I encounter anymore problems I'll update this thread.
cool :)

---

### Post by Crazy K on 2011-03-08
Having same problem again. Here are some things I did: 

Put this command in: ```
mount -o vfat /dev/sdb1 /media/fat32
```

I then get this: ```
mount: /dev/sdb1 already mounted or /media/fat32 busy
mount: according to mtab, /dev/sdb1 is mounted on /media/My Book

```

I change fat32 to My Book and I get this: 

```

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

Also, would connecting a 30GB MP3 player mess up the mount for my HD? Or does that matter?

---

### Post by markeee on 2011-03-09
> **Crazy K said:**
> Having same problem again. Here are some things I did: 

Put this command in: ```
mount -o vfat /dev/sdb1 /media/fat32
```

I then get this: ```
mount: /dev/sdb1 already mounted or /media/fat32 busy
mount: according to mtab, /dev/sdb1 is mounted on /media/My Book

```

I change fat32 to My Book and I get this: 

```

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

Also, would connecting a 30GB MP3 player mess up the mount for my HD? Or does that matter?
shouldnt matter, and as to the last one - its due to the space when you said  My Book :)

---

### Post by Crazy K on 2011-03-09
Yeah I thought so too. But when I take the space out it says this: 

```
mount: mount point /media/MyBook does not exist
```

When I put a _ I get the same thing. 

Also, when I go to the media tab where My Book is located this is what I see: [http://i.imgur.com/yO06T.png](http://i.imgur.com/yO06T.png)

When My HD is having problems, it also has the lock over it. What I'm also wondering, is why do I have 4 Vado HD folders? I have my Vado camera connected, but I would like to know why there are 3 more folders for it. Also, is this a problem, or is this normal?

Also, I checked Gparted again. And I noticed something about it. Here I noticed a caution sign by it: 
[http://i.imgur.com/oKW0A.png](http://i.imgur.com/oKW0A.png)

And I right click and go to "manage flags" or something along those lines and I get this: 
[http://i.imgur.com/fuF2v.png](http://i.imgur.com/fuF2v.png)

What's this lba? And should I uncheck that and check boot?

---

### Post by markeee on 2011-03-11
ok

well, i think you need to use backslash space when dealing with spaces

i.e. cd /home/mark/My\ Book/

or use quotations

but re below, thats because the actual location doesn't exist

if you cd /media/MyBook you wont be able to change dir there as it doesnt exist

:)

sudo mkdir /media/MyBook

---

### Post by markeee on 2011-03-11
> **Crazy K said:**
> Yeah I thought so too. But when I take the space out it says this: 

```
mount: mount point /media/MyBook does not exist
```

When I put a _ I get the same thing. 

Also, when I go to the media tab where My Book is located this is what I see: [http://i.imgur.com/yO06T.png](http://i.imgur.com/yO06T.png)

When My HD is having problems, it also has the lock over it. What I'm also wondering, is why do I have 4 Vado HD folders? I have my Vado camera connected, but I would like to know why there are 3 more folders for it. Also, is this a problem, or is this normal?

Also, I checked Gparted again. And I noticed something about it. Here I noticed a caution sign by it: 
[http://i.imgur.com/oKW0A.png](http://i.imgur.com/oKW0A.png)

And I right click and go to "manage flags" or something along those lines and I get this: 
[http://i.imgur.com/fuF2v.png](http://i.imgur.com/fuF2v.png)

What's this lba? And should I uncheck that and check boot?

looking at the first screenshot it appears to have the old ones half mounted

run df -h and paste the output

also why are you using fat32 for such a big drive? Any particular reason?!

---

### Post by Crazy K on 2011-03-11
> **markeee said:**
> looking at the first screenshot it appears to have the old ones half mounted

run df -h and paste the output

also why are you using fat32 for such a big drive? Any particular reason?!

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   24G   11G  69% /
none                  305M  312K  305M   1% /dev
none                  312M  684K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw

```

Also, I'm not sure why it's a fat32 file system. I had it on a windows machine for a year before I went to Ubuntu. So could that be why?

After I did the make dir for MyBook and mounted it, I now get this with the df -h prompt: 

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   24G   11G  69% /
none                  305M  312K  305M   1% /dev
none                  312M  684K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
/dev/sdb1             466G   89G  377G  20% /media/My Book
/dev/sdb1             466G   89G  377G  20% /media/MyBook

```

---

### Post by markeee on 2011-03-11
> **Crazy K said:**
> ```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   24G   11G  69% /
none                  305M  312K  305M   1% /dev
none                  312M  684K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw

```

Also, I'm not sure why it's a fat32 file system. I had it on a windows machine for a year before I went to Ubuntu. So could that be why?

After I did the make dir for MyBook and mounted it, I now get this with the df -h prompt: 

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   24G   11G  69% /
none                  305M  312K  305M   1% /dev
none                  312M  684K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
/dev/sdb1             466G   89G  377G  20% /media/My Book
/dev/sdb1             466G   89G  377G  20% /media/MyBook

```
I'm just surprised its fat32 being that it's that size

ok im not sure why it's mounted twice-unmount them both

sudo umount /dev/sdb1

then df -h

we only need it mounted once!!

---

### Post by Crazy K on 2011-03-11
Here you go: 

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   25G   11G  71% /
none                  305M  308K  305M   1% /dev
none                  312M  684K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
/dev/sdb1             466G   89G  377G  20% /media/My Book

```

Reason it's mounted twice is because I made a new dir. Instead of My Book I made MyBook

---

### Post by markeee on 2011-03-11
> **Crazy K said:**
> Here you go: 

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   25G   11G  71% /
none                  305M  308K  305M   1% /dev
none                  312M  684K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
/dev/sdb1             466G   89G  377G  20% /media/My Book

```

Reason it's mounted twice is because I made a new dir. Instead of My Book I made MyBook

ok can you access it all ok now? asit says it's mounted or are there still some problems?!

---

### Post by Crazy K on 2011-03-11
It's working like normal now. I'm just worried when I turn it off for the night and come back on it tomorrow that it'll do it again.

If it still happens tomorrow I'll update you on it right away.

---

### Post by markeee on 2011-03-11
> **Crazy K said:**
> It's working like normal now. I'm just worried when I turn it off for the night and come back on it tomorrow that it'll do it again.

If it still happens tomorrow I'll update you on it right away.
unmount it when finished with it for the day ? :)

sudo umount /dev/sdb1

could always make it auto mount ..edit /etc/fstab

---

### Post by Crazy K on 2011-03-11
How do I auto mount it?

---

### Post by Crazy K on 2011-03-12
So how do I auto mount it? 

I turned my computer on this morning around 9 or 10am and It's now 12:30 PM and I did the df -h prompt and got this: 

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   25G   11G  70% /
none                  305M  308K  305M   1% /dev
none                  312M  656K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
none                   37G   25G   11G  70% /var/lib/ureadahead/debugfs

```

I then checked to see if my HD was mounted and it wasn't. I clicked it, which mounted it and here is what I got from the prompt: 

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   25G   11G  70% /
none                  305M  308K  305M   1% /dev
none                  312M  656K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
none                   37G   25G   11G  70% /var/lib/ureadahead/debugfs
/dev/sdb1             466G   89G  377G  20% /media/My Book

```

So I just need to know how to make it mount at startup and keep it mounted forever.

Also, when I try to get into /etc/fstab I get permission denied.

I was able to get into the file, but I have no idea what to do to make my HD auto mount.

---

### Post by markeee on 2011-03-12
> **Crazy K said:**
> So how do I auto mount it? 

I turned my computer on this morning around 9 or 10am and It's now 12:30 PM and I did the df -h prompt and got this: 

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   25G   11G  70% /
none                  305M  308K  305M   1% /dev
none                  312M  656K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
none                   37G   25G   11G  70% /var/lib/ureadahead/debugfs

```

I then checked to see if my HD was mounted and it wasn't. I clicked it, which mounted it and here is what I got from the prompt: 

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G   25G   11G  70% /
none                  305M  308K  305M   1% /dev
none                  312M  656K  311M   1% /dev/shm
none                  312M  212K  312M   1% /var/run
none                  312M     0  312M   0% /var/lock
none                  312M     0  312M   0% /lib/init/rw
none                   37G   25G   11G  70% /var/lib/ureadahead/debugfs
/dev/sdb1             466G   89G  377G  20% /media/My Book

```

So I just need to know how to make it mount at startup and keep it mounted forever.

Also, when I try to get into /etc/fstab I get permission denied.

I was able to get into the file, but I have no idea what to do to make my HD auto mount.

givce me a few minutes and il post how to, just at work

---

### Post by markeee on 2011-03-12
> **markeee said:**
> givce me a few minutes and il post how to, just at work

sudo gedit /etc/fstab

then add

/dev/sdb1      /media/MyBook ntfs-3g    default  0   0

---

### Post by Crazy K on 2011-03-12
Where do I add that line exactly? Bottom of the page? Top? In between a certain area? 

Here's my etc/fstab page:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=787c83c7-d60c-462d-81e0-3e8218ae563a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8330fba5-7ff0-4bdf-8d74-f67d14f39227 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by markeee on 2011-03-12
> **Crazy K said:**
> Where do I add that line exactly? Bottom of the page? Top? In between a certain area? 

Here's my etc/fstab page:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=787c83c7-d60c-462d-81e0-3e8218ae563a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8330fba5-7ff0-4bdf-8d74-f67d14f39227 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

add it at the bottom mate

---

### Post by Crazy K on 2011-03-12
Thanks! 

If I have anymore problems I'll make sure to update you. :)

---

### Post by markeee on 2011-03-12
> **Crazy K said:**
> Thanks! 

If I have anymore problems I'll make sure to update you. :)

Restart and lets see if it works buddy

---

### Post by Crazy K on 2011-03-13
Yup, it isn't working yet. I turned it on this morning and the HD wasn't mounted. Clicked on it like I normally do and I got this: [http://i.imgur.com/HqqoU.png](http://i.imgur.com/HqqoU.png)

I then tried to mount it through the terminal with the mount -t vfat /dev/sdb1 /media/MyBook prompt but I got this: 

```


mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

EDIT:

I was able to get the prompt to work, but I can't mess with the files or anything. I can see them, but I can't delete or open any of them. 

Also, when I try to unmount, I get a warning saying only root can unmount.

---

### Post by markeee on 2011-03-13
> **Crazy K said:**
> Yup, it isn't working yet. I turned it on this morning and the HD wasn't mounted. Clicked on it like I normally do and I got this: [http://i.imgur.com/HqqoU.png](http://i.imgur.com/HqqoU.png)

I then tried to mount it through the terminal with the mount -t vfat /dev/sdb1 /media/MyBook prompt but I got this: 

```


mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

EDIT:

I was able to get the prompt to work, but I can't mess with the files or anything. I can see them, but I can't delete or open any of them. 

Also, when I try to unmount, I get a warning saying only root can unmount.

you need to run the command using sudo (allows you to run command with privs of a superuser/root) ,

---

### Post by Crazy K on 2011-03-14
I used the prompt to mount MyBook and it seems to be working. Only thing is that there's two folder for it. I really don't care too much for that because it does seem to be working.

---

### Post by markeee on 2011-03-16
> **Crazy K said:**
> I used the prompt to mount MyBook and it seems to be working. Only thing is that there's two folder for it. I really don't care too much for that because it does seem to be working.

will be an old mountpoint-could just delete the old mount point if it's not going to be used

---

