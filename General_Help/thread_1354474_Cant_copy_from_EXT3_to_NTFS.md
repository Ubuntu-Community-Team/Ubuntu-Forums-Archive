---
title: "Cant copy from EXT3 to NTFS"
date: 2009-12-13
forum: General Help
---

### Post by Dad1985 on 2009-12-13
When I try and copy files from a ext3 drive to a NTFS drive I always get the following error "Error creating directory: Operation not supported" whether using cp in the terminal or doing a copy and paste in nautilus.  

I have tried to chown and chmod both drives, and neither helps.  Both drives have 777 permissions and all files are owned by my user account.  I have both ntfs-3g and ntfsprogs installed.  I have tried mounting the NTFS drives with a umask of 0, but still get nothing.  I have tried mounting both with the mount command and with nautilus and get the same error.  

any tips would be appreciated

---

### Post by lmarmisa on 2009-12-13
According to your comment, the problem seems limited to the ntfs drive. Are you able to create new dirs there (mkdir)?

Try to check other commands (rm, rmdir, mv, cp) with files located only in that drive and tell us your results.

Best regards,

Luis

---

### Post by Dad1985 on 2009-12-13
> **lmarmisa said:**
> According to your comment, the problem seems limited to the ntfs drive. Are you able to create new dirs there (mkdir)?

Try to check other commands (rm, rmdir, mv, cp) with files located only in that drive and tell us your results.

Best regards,

Luis

I can do all of those tasks on the drive itself, I can even make a directory in ~ and copy it to that drive.  Its just the very large directory tree, maybe il tar and bring it over.  Il try that now.

---

### Post by lmarmisa on 2009-12-13
Could you show me the command that does not work?

---

### Post by Dad1985 on 2009-12-13
> **lmarmisa said:**
> Could you show me the command that does not work?

cp -vr /ext3drive/ /ntfsdrive/


The copying of the tar doesnt work either

 > cp music.tar /media/0E888CC7888CAF31/Users/Birdeye/Documents/My\ Music/
cp: cannot create regular file `/media/0E888CC7888CAF31/Users/Birdeye/Documents/

---

### Post by lmarmisa on 2009-12-13
Is the command aborted very soon or after a while?

Is always the command aborted in the same point?

Is the distination disk full?

---

### Post by oldfred on 2009-12-13
I mount NTFS with fstab and have had no problems with this setting:

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by dcstar on 2009-12-14
> **Dad1985 said:**
> cp -vr /ext3drive/ /ntfsdrive/


The copying of the tar doesnt work either

 > cp music.tar /media/0E888CC7888CAF31/Users/Birdeye/Documents/My\ Music/
cp: cannot create regular file `/media/0E888CC7888CAF31/Users/Birdeye/Documents/

That message indicates that you need to put the **whole** path in quotes:

```
cp music.tar "/media/0E888CC7888CAF31/Users/Birdeye/Documents/My Music/"
```

If indeed you have the "\" character in your path, then that is probably illegal in NTFS (along with anything starting with ".").

---

### Post by Dad1985 on 2009-12-14
> **lmarmisa said:**
> Is the command aborted very soon or after a while?

Is always the command aborted in the same point?

Is the destination disk full?

It aborts instantly and no the disk has alot of space left free on it.

---

### Post by Dad1985 on 2009-12-14
> **dcstar said:**
> That message indicates that you need to put the **whole** path in quotes:

```
cp music.tar "/media/0E888CC7888CAF31/Users/Birdeye/Documents/My Music/"
```

If indeed you have the "\" character in your path, then that is probably illegal in NTFS (along with anything starting with ".").

That does work either

> cp music.tar "/media/0E888CC7888CAF31/Users/Birdeye/Documents/My Music/"
cp: cannot create regular file `/media/0E888CC7888CAF31/Users/Birdeye/Documents/My Music/music.tar': Operation not supported


Thogh what you said, did hold weight because, I am currently copying to the directory before My Music without the space and it seems to be working, finger crossed.

---

### Post by Dad1985 on 2009-12-14
I was able to copy over the tar, but am unsable to extract it.  I really think something is wrong with ntfs-3g

---

### Post by coffeecat on 2009-12-14
> **Dad1985 said:**
>   I really think something is wrong with ntfs-3g

There's nothing intrinsically wrong with ntfs-3g. I use it on three machines with NTFS partitions and I haven't come across your problem. That being said, I can't see where you're going wrong in the cp command, except for one detail. In fact your use of '\' was quite correct - you needed that to escape the space in 'My Music'. But this is interesting:

> > cp music.tar /media/0E888CC7888CAF31/Users/Birdeye/Documents/My\ Music/
cp: cannot create regular file `/media/0E888CC7888CAF31/Users/Birdeye/Documents/     Presumably your path (in Windows speak) is C:\Users\Birdeye\Documents\My Music. So, I ask myself, why is cp thinking it needs to create a file called Documents? Double-check you've got the path right.

Alternatively, cd into My Music...

```
cd /media/0E888CC7888CAF31/Users/Birdeye/Documents/My\ Music
```... and then try to copy the file the other way around, as it were:

```
cp /home/yourusername/music.tar ./
```But don't use cp by itself or with just the v and r flags. You'll lose the date and time and possibly some other attributes. Have a look at man cp. I always use 'cp -av'.

Two questions:

Are you able to copy with a simple drag and drop? And what do you mean by not being able to extract the tar? What did you try? What happened?

One last comment: your fstab line for ntfs is just fine. That's what I use and I don't get problems.

---

### Post by Dad1985 on 2009-12-14
> **coffeecat said:**
> There's nothing intrinsically wrong with ntfs-3g. I use it on three machines with NTFS partitions and I haven't come across your problem. That being said, I can't see where you're going wrong in the cp command, except for one detail. In fact your use of '\' was quite correct - you needed that to escape the space in 'My Music'. But this is interesting:

Presumably your path (in Windows speak) is C:\Users\Birdeye\Documents\My Music. So, I ask myself, why is cp thinking it needs to create a file called Documents? Double-check you've got the path right.

Alternatively, cd into My Music...

```
cd /media/0E888CC7888CAF31/Users/Birdeye/Documents/My\ Music
```... and then try to copy the file the other way around, as it were:

```
cp /home/yourusername/music.tar ./
```But don't use cp by itself or with just the v and r flags. You'll lose the date and time and possibly some other attributes. Have a look at man cp. I always use 'cp -av'.

Two questions:

Are you able to copy with a simple drag and drop? And what do you mean by not being able to extract the tar? What did you try? What happened?

One last comment: your fstab line for ntfs is just fine. That's what I use and I don't get problems.

I have also done this before, many times over the years and have not had any trouble.  I now only have this trouble in 9.10, possibly a bad update of ntfs-3g.  Im not sure. 


When I cd into the 
<u M<usic" and cp the data, it just tells me the same error as when I do it the original way.  

A simple drag and drop in nautilus yields the same result.  

When I tried to extract the tar, I got file not found/file cannot be created error, in the tars output.


Some of the trouble is the space in "My Music".


BTW, when I mount the windows drive it always says root owns the drive.  Why is this, other drives I mount via fstab are owned by me.

---

### Post by Dad1985 on 2009-12-14
I can also created a directory named "Bird Bird", notice the space, in the windows drive and delete it.    Though I cannot operate on the already made directories with spaces./

---

### Post by sdowney717 on 2009-12-14
> BTW, when I mount the windows drive it always says root owns the drive. Why is this, other drives I mount via fstab are owned by me.

perhaps this is it.
I open my windows drive and it says owned by me

also cant use slash in a folder name

---

### Post by sdowney717 on 2009-12-14
[http://forums.pcpitstop.com/index.php?showtopic=130206&pid=1296828&mode=threaded&show=&st=&](http://forums.pcpitstop.com/index.php?showtopic=130206&pid=1296828&mode=threaded&show=&st=&)

this guy says owned by root is good, but i change ownership using chown on the drive. otherwise inconvenient to keep using sudo

for example open a terminal and type in 
gksu nautilus

see if you can drop copy paste into the windows drive.

if so then you can change ownership using chown command on the drive

---

### Post by Dad1985 on 2009-12-14
> **sdowney717 said:**
> perhaps this is it.
I open my windows drive and it says owned by me

also cant use slash in a folder name

Nope, my folders and drive are opwned by root and I cant get around it,. chown certainly doesn't work.

---

### Post by coffeecat on 2009-12-14
First, when I said your fstab was OK, I mistook oldfred's post for yours. Re-reading the thread, I think your mount options may be the problem. Either post your /etc/fstab line for the ntfs partition, or try oldfred's line, a simple:

```
device     mountpoint     ntfs     defaults     0 0
```That works fine for me too, and you can have either 'ntfs' or 'ntfs-3g' in the third field. It makes no difference - you still get to use the ntfs-3g driver.

Or try that line **and** post your fstab line.

> **Dad1985 said:**
> Some of the trouble is the space in "My Music".

Yes, I've already partly explained this. Spaces in file or folder names in the terminal cause problems whatever the context. 'cd My Music' will be parsed by the bash shell as 'cd My' and you will get a 'cannot stat...' error. That's why you need the backslash (\) - to escape the space. A backslash tells the bash shell that the next character should be interpreted as part of the filename. Yes, a NTFS file/folder name can't have a backslash, but that's irrelevant here. The backslash is a message to the bash shell and is not seen as part of the folder name.

> **Dad1985 said:**
>  BTW, when I mount the windows drive it always says root owns the drive.  Why is this, other drives I mount via fstab are owned by me.

No, that's OK. NTFS does not support Linux/Unix permissions, so the ownership is immaterial. All the files on my NTFS partitions are seemingly owned by root but that doesn't stop me copying/editing/moving/deleting them as an ordinary user. You **don't** have to use a root Nautilus.

> **Dad1985 said:**
> Nope, my folders and drive are opwned by root and I cant get around it,. chown certainly doesn't work.

Chowning and chmodding files and folders on a NTFS (or VFAT) filesystem is futile, since chown and chmod are commands to modify Linux/Unix permissions and NTFS (and VFAT) does not support Linux permissions. You can chown the mountpoint, but that's pointless as well. It's the fstab mount options that are important.

So - let's have a look at your fstab. Also - one other thought. The NTFS filesystem you are copying to is clearly your Windows C:\ partition. Is that XP, Vista or Windows 7? If Vista or W7 you might want to think of not doing that. Vista (and I assume W7) can react very badly to finding files it did not write itself. XP doesn't have this problem. That's why I always set up a shared NTFS data partition - so that I don't have to write directly to the Vista or Win7 partition from Ubuntu.

---

### Post by Dad1985 on 2009-12-15
Here is a copy of my fstab

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cffdd514-a0d6-400d-890a-7af9fe05e131 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=b3dfe5b5-e363-45ff-8d14-342eef208af3 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=fcd5802c-b0d4-4179-958e-a9d6a809804b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdc1 /media/win ntfs-3g defaults,locale=en_US.UTF-8, umask=000 0 0
/dev/sdb1 /media/Black ext3 defaults 0 0




I only use windows to put music on my ipod, I have a windows 7 install solely for that purpose.

---

### Post by coffeecat on 2009-12-15
In your ntfs fstab line I can see three possible problems.

```
/dev/sdc1 /media/win ntfs-3g defaults,locale=en_US.UTF-8, umask=000 0 0
```1 - The umask=000 option is not necessary. I've come across an instance where a permissions-related option actually caused problems. I'm not saying that's so here, but you might as well take it out.

2 - There is a space between the comma after UTF-8 and umask. That would affect how that line is parsed.

3 - Your 'en_US.UTF-8' should be of the form  'en_US.utf8'. Notice that there should be no hyphen, and lower-case 'utf'.

Taking all those in account, your ntfs fstab line would become:

```
/dev/sdc1 /media/win ntfs-3g defaults,locale=en_US.utf8 0 0
```

Now compare that with what's in this Ubuntu community page:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

> ntfs

 This example is perfect for a Windows partition. 

```
/dev/hda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```If that doesn't work, then - well I don't know.

---

