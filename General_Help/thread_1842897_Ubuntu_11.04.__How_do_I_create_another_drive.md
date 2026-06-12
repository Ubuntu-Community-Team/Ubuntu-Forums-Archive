---
title: "Ubuntu 11.04.  How do I create another drive?"
date: 2011-09-12
forum: General Help
---

### Post by pretty_whistle on 2011-09-12
I want to create another drive on my computer for the fun of it.

Now that that&#8217;s out of the way, how do I do it?  I did it in Windows but since I&#8217;m new to Linux I have little knowledge of what&#8217;s involved.


    
    1st off, wouldn&#8217;t I need to do it while the OS is not mounted?  If yes, then I need a boot CD or something similar.  And what else do I need to do, if anyone knows. :)

---

### Post by docbop on 2011-09-12
your use of "drive" is throwing me.  You want to add another physical drive to the computer, or your want to partition your drive and create another mount point?  

After you get your "drive" via adding or creating a partition (fdisk).  Then you have to format it like any OS to create a file system you can use mkfs.ext3 for and ext3 filesystem. There are simular commands for other filesystem types. 

The you will be able to mount the drive.  If you just want it occasional then can make a mount point, i.e. a directory to use like /mnt/nu_drive.     Then use the mount command to mount the new drive/partition.   I would say do that to test things.   if you want to have that drive every time your bootup then you will need to modify they /etc/fstab  file.   That is what gets read at boot time to mount your drives and assign them mount points.   

That the gist of what you need to do. Now spend a little time with your favorite Linux book or the man pages for the details of using those commands.

---

### Post by pretty_whistle on 2011-09-12
> **docbop said:**
> your use of "drive" is throwing me.  You want to add another physical drive to the computer, or your want to partition your drive and create another mount point?  

After you get your "drive" via adding or creating a partition (fdisk).  Then you have to format it like any OS to create a file system you can use mkfs.ext3 for and ext3 filesystem. There are simular commands for other filesystem types. 

The you will be able to mount the drive.  If you just want it occasional then can make a mount point, i.e. a directory to use like /mnt/nu_drive.     Then use the mount command to mount the new drive/partition.   I would say do that to test things.   if you want to have that drive every time your bootup then you will need to modify they /etc/fstab  file.   That is what gets read at boot time to mount your drives and assign them mount points.   

That the gist of what you need to do. Now spend a little time with your favorite Linux book or the man pages for the details of using those commands.

I want to partition it and create another mount point but not to be included in boot.

Does anyone know of a good tutorial online for this?

---

### Post by pretty_whistle on 2011-09-12
For anyone who comes looking for what I asked for, I found a how-to on ubuntu.org.  Here it is:

				[B]HowTo: Partitioning Basics

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)


[/B]

---

### Post by pretty_whistle on 2011-09-12
Wow.  All that link I gave does is describe what's called what but doesn't cover the 'how'.

So, I still need to know how.  Can anyone clue me in?

---

### Post by RJ12 on 2011-09-12
> **pretty_whistle said:**
> Wow.  All that link I gave does is describe what's called what but doesn't cover the 'how'.

So, I still need to know how.  Can anyone clue me in?

I recommend a GUI tool called GParted. If you will be resizing your partition where Ubuntu is running, you will need to boot off of your installation media (LiveUSB/LiveCD) to do resizing. As for getting it set up in fstab (Others can tell you how) which is how it would be mounted every boot up, I can't really help you with that.

---

### Post by pretty_whistle on 2011-09-12
> **RJ12 said:**
> I recommend a GUI tool called GParted. If you will be resizing your partition where Ubuntu is running, you will need to boot off of your installation media (LiveUSB/LiveCD) to do resizing. As for getting it set up in fstab (Others can tell you how) which is how it would be mounted every boot up, I can't really help you with that.
Thanks.  Just got the GParted livecd for booting with.

---

### Post by as2000 on 2011-09-12
Have you looked into Disk Utility? It is pretty straight foreword and can resize, format and run benchmarks.

---

### Post by pretty_whistle on 2011-09-13
> **as2000 said:**
> Have you looked into Disk Utility? It is pretty straight foreword and can resize, format and run benchmarks.
No I haven't.  I'll check into that.

---

### Post by PFactorial on 2011-09-13
So can I partition the drive when I'm using it? No?

---

### Post by pretty_whistle on 2011-09-13
> **PFactorial said:**
> So can I partition the drive when I'm using it? No?

I figure not. It has to be unmounted and not in use. It'll give a message saying it can't.  (Good thing I've got the GParted livecd to boot with then.)

---

### Post by pretty_whistle on 2011-09-13
> **docbop said:**
> your use of "drive" is throwing me.  You want to add another physical drive to the computer, or your want to partition your drive and create another mount point?  

After you get your "drive" via adding or creating a partition (fdisk).  Then you have to format it like any OS to create a file system you can use mkfs.ext3 for and ext3 filesystem. There are simular commands for other filesystem types. 

The you will be able to mount the drive.  If you just want it occasional then can make a mount point, i.e. a directory to use like /mnt/nu_drive.     Then use the mount command to mount the new drive/partition.   I would say do that to test things.   if you want to have that drive every time your bootup then you will need to modify they /etc/fstab  file.   That is what gets read at boot time to mount your drives and assign them mount points.   

That the gist of what you need to do. Now spend a little time with your favorite Linux book or the man pages for the details of using those commands.

I have a question of you or anyone who knows.  About having it available when booting, doesn't GParted take care of this?  Couldn't I use GParted to take care of this?

---

### Post by oldos2er on 2011-09-13
> **pretty_whistle said:**
> I have a question of you or anyone who knows.  About having it available when booting, doesn't GParted take care of this?  Couldn't I use GParted to take care of this?

No, you'll need to edit your /etc/fstab file after you've created, formatted, and made a mount point for the partition. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by pretty_whistle on 2011-09-13
> **oldos2er said:**
> No, you'll need to edit your /etc/fstab file after you've created, formatted, and made a mount point for the partition. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Thanks for the info.

This brings me to another question:  I take it I would be using terminal for that part.

---

### Post by pretty_whistle on 2011-09-13
> **oldos2er said:**
> No, you'll need to edit your /etc/fstab file after you've created, formatted, and made a mount point for the partition. 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Nevermind my last question.  I didn't see the link you gave.  Lol.

---

### Post by pretty_whistle on 2011-09-13
Update:

Doing this with Windows was easy but with this, nope.

I made a drive, named it "Dubbins", but it won't let me put a folder or file on it.  I made it as a primary partition, ext4, and set it to mount when booted.

I presume why I have a problem is because I failed to format it, at least I'm hoping it's nothing more complex.  :o

Anyone with some advice would be appreciated.

Edit:  I just formatted it and can put a folder in it but not a file (nevermind-it DOES let me put a file there). 

So, that's all cleared up.............

But... I have a "lost & found" folder there.  What's that about?

---

### Post by pretty_whistle on 2011-09-14
A better question:

Can I delete that folder off?

.

---

### Post by oldos2er on 2011-09-14
The lost+found folder is used by ext3 and ext4 filesystems to store files recovered by fsck. You could delete it, but that's kind of pointless because the system will recreate it. It can be safely ignored.

---

