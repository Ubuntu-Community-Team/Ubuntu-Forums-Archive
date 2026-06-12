---
title: "Drive not mounting correctly"
date: 2009-10-06
forum: General Help
---

### Post by david davidson on 2009-10-06
Hi. I added the following to my Fstab

```
/dev/sdb1 /media/F vfat rw,user,auto,exec
```and yet after boot, F is read only. This is what I get when I try to copy a file to it:

```
Error opening file '/media/F/test.txt': Permission denied
```and I can't create folders or delete anything.

Obviously I am doing something wrong but I am stumped. Somebody suggested that I tried

```
sudo chown root /media/F
```but the same thing happened after a reboot.


Any help will be gratefully received,
Dave

---

### Post by beastrace91 on 2009-10-06
You need to do ```
sudo chown myusernamehere /media/F
```

~Jeff

---

### Post by david davidson on 2009-10-06
Thanks a lot for your swift response. Unfortunately doing that hasn't changed the situation at all.

---

### Post by beastrace91 on 2009-10-06
Its been awhile since I tinkered with my fstab file but the settings I use for my internal partition I mount to a set point looks like this: ```
/dev/sdb1 /media/F vfat defaults,exec 0 0
```

Like I said I don't recall off the top of my head what the trailing 0s are for but I remember them being needed... Give that a go as your fstab (remember to reboot after editing to test it & chown it again.)

~Jeff

---

### Post by david davidson on 2009-10-06
Unfortunately that hasn't worked either.

---

### Post by beastrace91 on 2009-10-06
Huh thats truly odd, could you post the entire contents of your fstab file? For instance my extra entry looks like: ```
/dev/sda5	/media/storage	ext3	defaults,exec	0	0
```

Just for comparison.

~Jeff

---

### Post by david davidson on 2009-10-06
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# / was on /dev/sda7 during installation
UUID=1900d049-3508-4032-8f22-b1f41970269a  /               ext3         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda8 during installation
UUID=eb803b7d-7f75-4bba-8326-41ab1bd7ef94  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1 /media/F vfat defaults,exec 0 0
```

---

### Post by beastrace91 on 2009-10-06
Alrighty I am slightly lost then... Everything looks like it should be just skippy.

And just to be clear when you ran: ```
sudo chown myusernamehere /media/F
``` You replaced "myusernamehere" with your own username right?

~Jeff

---

### Post by fluffman86 on 2009-10-06
Also, are you sure F is a fat32 formatted drive? like a thumbdrive?  If it's a normal windows hard drive it'll probably be ntfs, so you should change the vfat part of fstab to ntfs-3g.

---

### Post by beastrace91 on 2009-10-06
> **fluffman86 said:**
> Also, are you sure F is a fat32 formatted drive? like a thumbdrive?  If it's a normal windows hard drive it'll probably be ntfs, so you should change the vfat part of fstab to ntfs-3g.

I'm assuming he has the file system correct as the drive is getting mounted but he simply lacks read/write privileges.

~Jeff

---

### Post by bigboy_pdb on 2009-10-07
Nevermind, I was looking at the wrong post when I posted this. You appear to be doing things correctly.

---

### Post by bigboy_pdb on 2009-10-07
I tried mounting my usb flash drive to see how it was mounted.

The mount command produced the following:
```

/dev/sdb1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

You might want to try adding uid with your user id and possibly a umask.

Have you looked at the "mount options for fat" and "mount options for vfat" in the mount man page?

---

### Post by david davidson on 2009-10-07
Thanks for the continuing replies.

I did change myusername to dave.

The drive is definitely fat32 (I formatted it that way a long time ago so that all operating systems would be able to read and write to it - OSX86 etc.)


EDIT: didn't see the second page. I will look in to what bigboy_pdb said.
[ ]("http://ubuntuforums.org/member.php?u=305128")

---

### Post by andy034 on 2009-10-07
Hi

   I am new ubuntu. When I instlled Ubuntu 9.04 I forgot  giving mount points to my ntfs partitions( which I think enables me to access without mounting each drive when logged in).
 
I created a shell script wherein i mount my ntfs partitions.. but the problem i face is when i run the script the filesystems are mounted alright but I do not get the shortcuts or whatever to these filesystems which i do get when i mount using Places->removable...->{partitionname}

hope I got my point through..

Thanks

---

### Post by theDaveTheRave on 2009-10-08
my experience with the fstab is not huge, as it has allways just "worked" for me!

Quick observations from the thread, the parital output of the OP's fstab is...

```

/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1 /media/F vfat defaults,exec 0 0

```

I'm curious as to why on the final line the "space" bestween 
<dev/sdb1> and </media/F vfat defaults,exec 0 0> is less than for the other lines?? can the OP confirm that it is definately a <tab space> and not a <normal space> in the file? would this even make a difference?

Also the OP says he can "read" the disk by cannot write??

A possiblitiy is that the permissions are "wrong" for the whole disk, so changing the owner may not help.

Can you save a file to the disk if you are working as root (try this to open a "sudo nautilus")
```

sudo nautilus --no-desktop

```

if you can, then check (whilst nautilus is open as sudo) the permissions for read and write permisions for the whole disk.

Also why you are here check out the location of the /dev/sdb1 to see if you are able to access / read / write to the disk while it is here. I am assuming that if for some  reason /dev/sdb1 has some sort of "read only" permisions for all users, no matter what you do to the mount point you will not be able to gain write if the permision there is "read only, pass to all sub folders" or similar?

The last (extremely daft suggestion), if you have recently moved this disk from elsewhere is there a "switch" or "jumper" setting to mark it as read only? I have a USB key that has a "lock position" on it, that occasionally gets "pushed" into the wrong position, and gives me real grief as I forget that it has it!

Anyway, they are my (probably stupid and not very helpful) observations.

good luck

David

ps. have you tried doing the mount command from the terminal after you have started? obviously change the mount location from /media/F to something else
```

/dev/sdb1 /media/testing vfat defaults,exec 0 0

```

 and see if you are able to read / write from this new location, if so it would suggest there is an error in your fstab somewhere (see above).

---

### Post by bigboy_pdb on 2009-10-08
andy034, based on your post I'm not certain if you're saying that you've been able to mount your drives (to indicate that it can be done) or if you're asking for help with getting the icons to show up.

If you want help with a problem, it's always best to create a new thread.

If you do that and post a link to the thread, we can help you there.

---

### Post by bigboy_pdb on 2009-10-08
david davidson, you might want to try mounting the drive using the "gnome-mount" command. You can then use the "mount" command to see how it got mounted. Hopefully, that will provide some more insight into how you can edit the fstab file so that the drive gets mounted during start up.

---

