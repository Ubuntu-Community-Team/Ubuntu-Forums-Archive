---
title: "WUBI: Saving onto Host HDD"
date: 2011-03-17
forum: General Help
---

### Post by kawaiipikachu on 2011-03-17
I'm basically trying out Ubuntu via a WUBI install.
What I want to do is to save some of my downloads directly into the host HDD so Windows can access plus I'm not quite ready to increase the WUBI image yet.

Any solutions would be usefull.
Thanks in advance.

---

### Post by Frogs Hair on 2011-03-17
Hi and Welcome

Wubi installs Ubuntu inside the Windows partition  , so it is on the same drive . It is possible access Windows trough the File system /Host in Ubuntu , but the reverse is not possible and saving to Windows or host is not an option .

It is possible to create a data partition that can be accessed by both operating systems , but that would require a dual boot and creating the partitions . I don't know what is meant by increase the Wubi image.

---

### Post by bcbc on 2011-03-17
As Frogs Hair says you can access the windows partition as /host (ALT-F2, nautilus /host) and you can copy files on to it without any issues.

You should also be able to symlink your folders to one on /host as well e.g. so that /home/user/Pictures is actually on /host

---

### Post by kawaiipikachu on 2011-03-18
> **bcbc said:**
> As Frogs Hair says you can access the windows partition as /host (ALT-F2, nautilus /host) _and you can copy files on to it without any issues._

You should also be able to symlink your folders to one on /host as well e.g. so that /home/user/Pictures is actually on /host

Um when I save into host the file simply just disappears as in it's not saving into the host itself.
I can access & read the host's files but no write.

---

### Post by bcbc on 2011-03-18
> **kawaiipikachu said:**
> Um when I save into host the file simply just disappears as in it's not saving into the host itself.
I can access & read the host's files but no write.

That's strange...

I just booted Wubi, created a directory Pictures under /host, then symlinked it to /home/bcbc/MyPictures, then saved a screenshot to /home/bcbc/MyPictures... and then booted into Windows.
```
cd /host
mkdir Pictures
cd /home/bcbc
ln -s /host/Pictures MyPictures
```

And the file C:\Pictures\Screenshot.png is sitting there. 

I'm using a standard Wubi install (actually not really as it's an alpha version of Natty - but what I mean is I haven't done anything special to the way the /host is mounted). So... it should work fine for you.

Also you kindof need full write access to /host with Wubi as otherwise it couldn't save the Ubuntu virtual disk.

---

### Post by kawaiipikachu on 2011-03-18
> **bcbc said:**
> That's strange...

I just booted Wubi, created a directory Pictures under /host, then symlinked it to /home/bcbc/MyPictures, then saved a screenshot to /home/bcbc/MyPictures... and then booted into Windows.
```
cd /host
mkdir Pictures
cd /home/bcbc
ln -s /host/Pictures MyPictures
```

And the file C:\Pictures\Screenshot.png is sitting there. 

I'm using a standard Wubi install (actually not really as it's an alpha version of Natty - but what I mean is I haven't done anything special to the way the /host is mounted). So... it should work fine for you.


Typed in ```
mkdir pictures
```& it comes upi with this message
"mkdir: cannot create directory `pictures': Permission denied
"

[quote=bcbc]

Also you kindof need full write access to /host with Wubi as otherwise it couldn't save the Ubuntu virtual disk.[/QUOTE]

I thought that the administrator account means yo can do anything with at most need is the password?
Anyway how do I enable full Write access?

---

### Post by bcbc on 2011-03-18
I didn't need to elevate my privileges to root to do that. 

What is the output of:
```
cat /etc/default/grub
cat /etc/fstab
```

---

### Post by kawaiipikachu on 2011-03-18
> **bcbc said:**
> I didn't need to elevate my privileges to root to do that. 

What is the output of:
```
cat /etc/default/grub
cat /etc/fstab
```
Here is the result
```
james@ubuntu:/host$ cat /ect/default/grub
cat: /ect/default/grub: No such file or directory
james@ubuntu:/host$ cat /ect/fstab
cat: /ect/fstab: No such file or directory


```

---

### Post by bcbc on 2011-03-18
> **bcbc said:**
> I didn't need to elevate my privileges to root to do that. 

What is the output of:
```
cat /etc/default/grub
cat /etc/fstab
```

> **kawaiipikachu said:**
> Here is the result
```
james@ubuntu:/host$ cat /[COLOR="Red"]ect[/COLOR]/default/grub
cat: /ect/default/grub: No such file or directory
james@ubuntu:/host$ cat /[COLOR="red"]ect[/COLOR]/fstab
cat: /ect/fstab: No such file or directory


```

That should have been "etc" not "ect"

---

### Post by kawaiipikachu on 2011-03-18
> **bcbc said:**
> That should have been "etc" not "ect"

Woops!
Any way here goes
For the "cat /etc/default/grub"came up with
```
james@ubuntu:/host$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
james@ubuntu:/host$ 

```


for the "cat /etc/fstab"command
```
james@ubuntu:/host$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/usr.disk /usr            ext4    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
james@ubuntu:/host$ 

```

---

### Post by bcbc on 2011-03-18
OK I don't see anything that indicates some sort of override on your /host mount options.

But is /host a FAT32 partition? The reason I ask is that you have a root.disk and a usr.disk and Wubi normally only does that if you have FAT32.

Whether this makes a difference to your ability to create files on /host - I cannot say. I have previously installed Wubi on FAT32 but never experimented with writing files to it. Still, I don't see why it should complain. 

But obviously something is different in your setup.

---

### Post by kawaiipikachu on 2011-03-18
> **bcbc said:**
> OK I don't see anything that indicates some sort of override on your /host mount options.

But is /host a FAT32 partition? The reason I ask is that you have a root.disk and a usr.disk and Wubi normally only does that if you have FAT32.

Whether this makes a difference to your ability to create files on /host - I cannot say. I have previously installed Wubi on FAT32 but never experimented with writing files to it. Still, I don't see why it should complain. 

But obviously something is different in your setup.

Host is fat32 formatted via my win98 startup floppy

---

### Post by bcbc on 2011-03-18
> **kawaiipikachu said:**
> Host is fat32 formatted via my win98 startup floppy

OK... I really don't have any ideas. I will boot up my fat32 wubi at some point and try it - but it will be at least 12 hours before you'll see a response on that. 

I can't really understand what the issue is though. Maybe someone else seeing this will be able to contribute.

Good luck

---

### Post by kawaiipikachu on 2011-03-18
> **bcbc said:**
> OK... I really don't have any ideas. I will boot up my fat32 wubi at some point and try it - but it will be at least 12 hours before you'll see a response on that. 

I can't really understand what the issue is though. Maybe someone else seeing this will be able to contribute.

Good luck

Thanks anyway & I'm glad to get some help on this forum as I'm pretty much new to Linux.

---

### Post by dragonfly41 on 2011-03-18
As another newbie I'm puzzled why you have quite a lot of info on host from cat /etc/fstab
but all I have is ...

[COLOR=Blue]ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$[/COLOR] 

I'm using Ubuntu in dual boot mode (wubi) and in Demo Mode.  
I've avoided a full installation until I could backup files.

---

### Post by bcbc on 2011-03-18
> **bcbc said:**
> OK... I really don't have any ideas. I will boot up my fat32 wubi at some point and try it - but it will be at least 12 hours before you'll see a response on that. 

I can't really understand what the issue is though. Maybe someone else seeing this will be able to contribute.

Good luck
I found my external drive, but as it turned out I had previously formatted my Fat32 partition and reused it as ext4 for Ubuntu. So... it's not going to be easy to test this. I also couldn't find any info on the net that indicated this was a known problem.

I'll see if I can figure something out.

> **dragonfly41 said:**
> As another newbie I'm puzzled why you have quite a lot of info on host from cat /etc/fstab
but all I have is ...

[COLOR=Blue]ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$[/COLOR] 

I'm using Ubuntu in dual boot mode (wubi) and in Demo Mode.  
I've avoided a full installation until I could backup files.

Dragonfly, you're booting a 'live CD' except with some Wubi help (the CD gets copied to the hard drive). So you don't have the virtual disks and the swap file. I doubt any changes you make are persisted the next time you boot.

---

### Post by kawaiipikachu on 2011-03-19
Problem solved.
Found the solution within this thread here [http://ubuntuforums.org/showthread.php?t=922360](http://ubuntuforums.org/showthread.php?t=922360) & teh command I needed to give myself permission to have wright access within the host was "gksu nautilus"


Anyway thanks for the help anyway.

---

### Post by bcbc on 2011-03-20
I'm glad you got it solved. It's strange though - I haven't had to elevate my privileges to do this.

---

### Post by kawaiipikachu on 2011-03-20
> **bcbc said:**
> I'm glad you got it solved. It's strange though - I haven't had to elevate my privileges to do this.

I actually spoke up too soon.
It worked but several hours later after my last post I ended up finding that I needed to reenter the command.

So it's actually halved solved just needed to be more permanent.

Computers, it can certainly a challenge for the best of us.

---

### Post by bcbc on 2011-03-20
Using sudo or gksudo to elevate privileges only lasts for a certain time period.

Try this [http://ubuntuforums.org/showthread.php?t=1657964](http://ubuntuforums.org/showthread.php?t=1657964)

The relevant part is changing /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="rootflags=umask=002,uid=1000,gid=1000 quiet splash"

Then run "sudo update-grub" before rebooting.

Make sure your userid number is 1000 (probably is) :
> You can find out your UID by opening a terminal and running "echo $UID".

---

### Post by kawaiipikachu on 2011-03-20
> **bcbc said:**
> Using sudo or gksudo to elevate privileges only lasts for a certain time period.

Try this [http://ubuntuforums.org/showthread.php?t=1657964](http://ubuntuforums.org/showthread.php?t=1657964)

The relevant part is changing /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="rootflags=umask=002,uid=1000,gid=1000 quiet splash"

Then run "sudo update-grub" before rebooting.

Make sure your userid number is 1000 (probably is) :

Unfortunately I could not quite get that to work.

---

