---
title: "using fsck to fix a problem"
date: 2010-03-28
forum: General Help
---

### Post by engine on 2010-03-28
Trying to solve a black-screen problem, I've found the following through etc/fstab

```
# /  	was on  	/dev/sda1  	during installation  	ext4  	errors=remount
# / home 	was on 	/dev/sda10 	during installation 	ext4 	defaults
# / opt 	was on 	/dev/sda8 	during installation 	ext4 	defaults
# / tmp 	was on 	/dev/sda9 	during installation 	ext4 	defaults
# / usr 	was on 	/dev/sda6 	during installation 	ext4 	defaults
# / var 	was on 	/dev/sda7 	during installation 	ext4 	defaults
# swap 	was on 	/dev/sda5 	during installation 	swap 	sw

```

I've had it suggested that "all I need to do" is run fsck on /dev/sda1

Double-checked that /dev/sda1 isn't mounted (though that, indeed, could be the problem), tried fsck ...

```
No fs2 file-system found
```

Well I never =8-} Of course there isn't. So if fsck doesn't cut it, what's the equivalent for trying to fix an ext4 partition?

---

### Post by Herman on 2010-03-28
My all-time favorite is this one to start off with,
```
sudo e2fsck -C0 -f -v -p /dev/sda1
```

---

### Post by ajgreeny on 2010-03-28
But you will have to run fsck from a live CD.

Your root partition must be unmounted when using fsck on it, so of course, you can't use the filesystem you are checking to run the check.

---

### Post by engine on 2010-03-29
```
sudo e2fsck -C0 -f -v -p /dev/sda1
```

... which, according to man e2fsck, means: force checking even if the file system seems clean, print a completion bar, be verbose and automatically fix any filesystem problems that can be safely fixed without human intervention.

Sounds good to me! now to fire up the box in question, boot it from a live CD and hope for the best.

```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -v -p /dev/sda1
                                                                               
   10334 inodes used (3.38%)
       1 non-contiguous file (0.0%)
       5 non-contiguous directories (0.0%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 9526
  119176 blocks used (9.76%)
       0 bad blocks
       1 large file

    7905 regular files
    1521 directories
      68 character device files
      26 block device files
       0 fifos
       2 links
     805 symbolic links (704 fast symbolic links)
       0 sockets
--------
   10327 files

```

Doesn't look as if there was anything wrong there, so what to do next about the original
```
# /  	was on  	/dev/sda1  	during installation  	ext4  	errors=remount
```

---

### Post by Herman on 2010-03-29
I don't know about your /etc/fstab file, it doesn't look like a proper /etc/fstab file to me. You have no active UUID lines and all of the lines I can see there are just comments.

The question I was responding to was: "(using fsck to fix a problem) what's the equivalent for trying to fix an ext4 partition?     ".

Maybe I can help you with your /etc/fstab file as well, but first you'll have to give me a little more background information. Is this some kind of special installation, like a wubi install?

Here's what a fairly standard /etc/fstab should look like, except I commented the floppy line because this machine doesn't have a floppy drive. The other difference is I have a swap file instead of a swap area. Otherwise this is an example of a fairly normal /etc/fstab file for a Ubuntu OS,
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdi1 during installation
UUID=51e9238e-90f1-4ef8-8a36-9c631511b3ec /    ext4    errors=remount-ro  0     1
/swapfile          none         swap       sw           0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Herman on 2010-03-29
:D Here's an example of an /etc/fstab file that's a little bit different, this one's from one of my LUKS encrypted LVM flash memory installations.
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/lvm-root /               ext4    noatime,errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=7cca2a2c-c4df-4970-b389-1f297dd13ec4 /boot   reiserfs notail     0       2
/dev/mapper/lvm-home /home           ext4    noatime         0       2
/dev/mapper/lvm-tmp /tmp            reiserfs nolog,notail,noatime  0       2
/dev/mapper/lvm-usr /usr            ext4    noatime         0       2
/dev/mapper/lvm-var /var            reiserfs nolog,notail,noatime  0       2
/dev/mapper/lvm-swap none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

A good site for information about /etc/fstab files is [How to Edit and Understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")[**]("http://www.tuxfiles.org/linuxhelp/fstab.html") -tuxfiles. 
Also see [How to fstab]("http://ubuntuforums.org/showthread.php?t=283131"), by bodhi.zazen.

---

### Post by engine on 2010-04-01
Thanks for the offer of farther help! here's some more context to start with.

step 1
[INDENT]Full install of 9.10 with CD after replacing defunct hard drive, followed by fine-tuning upgrades on-line
Almost completely successful, and a quick rootle round the forum sorted the "black desktop" question[/INDENT]

step 2
[INDENT]Settle down to using 9.10 (only o/s on the machine, auto login) and installing a couple of non-packaged apps I've been using since 7. All goes well.[/INDENT]

step 3
[INDENT]Fire up PC one morning ... result, black screen with "busy" cursor, plus white terminal window top left where I'm correctly logged in.[/INDENT]

From then on, it's been a Hall of Mirrors experience following different directions/tips from the forum: many other people have had the same problem, but there doesn't seem to be one, consistent cause. The only thing the various tips have in common is that none of them has worked for my situation :-{

I'll follow your links to possible sources of information, but don't know how much I'll actually understand!

I see I'd not included the UUID information in the /fstab extract, to save space and typing – can't copy/paste anywhere useful when the machine's not giving me anything beyond a terminal. The full first line is more like
```
# /  	was on  	/dev/sda1  	during installation
UUID=3c0d71be-4e48-411a-a29a-da1256c458df /	ext4	errors=remount -ro 0 1

```

Enough for an Aha! moment and an instant fix? <g>

---

