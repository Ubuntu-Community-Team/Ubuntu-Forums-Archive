---
title: "Request help with combining logical/primary partitions"
date: 2011-09-15
forum: General Help
---

### Post by iconoclast hero on 2011-09-15
I was looking at [http://ubuntuforums.org/showthread.php?t=1032234](http://ubuntuforums.org/showthread.php?t=1032234) and hoping someone would be able to help me take the two unformatted partitions and combine them into one for a /home directory.  

Here is what I have:
ubuntu server 10.10
3 HDDs, but I'm only concerned with the 30 GB on dev/sda.
On sda, there is a partition for XP, a swap partition, some unformatted space then on sda5 there is some more unformatted space and the operating system.  I think I may bump up the size of my swap file by a couple of MB although I'm open to suggestions as to how big it should be.  I might want to hibernate that machine and the RAM is listed as 1001MB.  

Other than that I'd like to basically just combine the two partitions and then from there I can follow directions for a separate /home (i.e. I've done it before).

fdisk -lu:

```
Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x820f820f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16361471     8180704+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        19531774    58632191    19550209    5  Extended
/dev/sda3        16361472    18411519     1025024   82  Linux swap / Solaris
/dev/sda5        20678656    58632191    18976768   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000dc2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x67b9bf91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   234436544   117218241   83  Linux

```


Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

sfdisk -d /dev/sda
```

/dev/sda1 : start=       63, size= 16361409, Id= 7, bootable
/dev/sda2 : start= 19531774, size= 39100418, Id= 5
/dev/sda3 : start= 16361472, size=  2050048, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 20678656, size= 37953536, Id=83

```

---

### Post by srs5694 on 2011-09-16
> **iconoclast hero said:**
> I was looking at [http://ubuntuforums.org/showthread.php?t=1032234](http://ubuntuforums.org/showthread.php?t=1032234) and hoping someone would be able to help me take the two unformatted partitions and combine them into one for a /home directory.  

Here is what I have:
ubuntu server 10.10
3 HDDs, but I'm only concerned with the 30 GB on dev/sda.
On sda, there is a partition for XP, a swap partition, some unformatted space then on sda5 there is some more unformatted space and the operating system.  I think I may bump up the size of my swap file by a couple of MB although I'm open to suggestions as to how big it should be.  I might want to hibernate that machine and the RAM is listed as 1001MB.  

Other than that I'd like to basically just combine the two partitions and then from there I can follow directions for a separate /home (i.e. I've done it before).

fdisk -lu:

```
Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders, total 58633344 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x820f820f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16361471     8180704+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        19531774    58632191    19550209    5  Extended
/dev/sda3        16361472    18411519     1025024   82  Linux swap / Solaris
/dev/sda5        20678656    58632191    18976768   83  Linux

Partition table entries are not in disk order

```

These sorts of problems are often easier to see (as in the display of GParted) than read (as in fdisk output), so if I've made an error, my apologies....

It appears that you've got some free (unpartitioned) space between /dev/sda3 and /dev/sda5, but that it's split between space that's inside of and outside of your /dev/sda2 extended partition. You want to create a single partition that spans this entire unpartitioned space. If I'm interpreting this correctly, there are several ways to proceed. The most conventional would probably be to use GParted to resize the extended partition. You could either shrink it so that all of the free space is outside of the extended partition (which would then necessitate creating a new primary partition) or expand it so that all of the free space is inside the extended partition (which would then necessitate creating a new logical partition). Either would be fine, although expanding the extended partition would give you more flexibility for future changes, since you'll then have one primary partition slot free, so I'd probably go with that option myself.

As to the swap space, if you want to use the suspend-to-disk feature, you must have at least as much swap space as you've got RAM. If I'm interpreting that display correctly, you've got 1001 MiB of swap space, so you're (barely) set. If you think there might be some rounding error going on, you could expand the swap space a bit. Do this before resizing the extended partition, since swap space is outside of and before the extended partition (in terms of disk sector use).

---

### Post by iconoclast hero on 2011-09-17
> **srs5694 said:**
> These sorts of problems are often easier to see (as in the display of GParted) than read (as in fdisk output), so if I've made an error, my apologies....

It appears that you've got some free (unpartitioned) space between /dev/sda3 and /dev/sda5, but that it's split between space that's inside of and outside of your /dev/sda2 extended partition. You want to create a single partition that spans this entire unpartitioned space. If I'm interpreting this correctly, there are several ways to proceed. The most conventional would probably be to use GParted to resize the extended partition. You could either shrink it so that all of the free space is outside of the extended partition (which would then necessitate creating a new primary partition) or expand it so that all of the free space is inside the extended partition (which would then necessitate creating a new logical partition). Either would be fine, although expanding the extended partition would give you more flexibility for future changes, since you'll then have one primary partition slot free, so I'd probably go with that option myself.

As to the swap space, if you want to use the suspend-to-disk feature, you must have at least as much swap space as you've got RAM. If I'm interpreting that display correctly, you've got 1001 MiB of swap space, so you're (barely) set. If you think there might be some rounding error going on, you could expand the swap space a bit. Do this before resizing the extended partition, since swap space is outside of and before the extended partition (in terms of disk sector use).

Here you are: 
[[IMG]http://i.imgur.com/keSCg.png[/IMG]](http://imgur.com/keSCg)

I cut back the NTFS partition by a bit and gave most of it to the swap and left the rest on the other side.  The changes are processing now although it should require moving any data so hopefully it finishes quickly.  I think I like the idea of leaving a spare primary partition...and I think what you suggested can be done via a boot into the live CD and using gparted.  Is that correct?  Is there any advantage of using the live boot from 11.04 over 10.10?

On a side note, if you know the answer to this great, if not, ok...  So since this is a 10.10 server, what is the best way to call the GUI?  I used ```
sudo startx &
``` but then it launched the gui as root which I'm sure isn't good, then I went in via vnc to get the screenshot.  I am going to have to connect to a monitor to use the live cd, but for future reference...

---

### Post by srs5694 on 2011-09-17
> **iconoclast hero said:**
> I think what you suggested can be done via a boot into the live CD and using gparted.  Is that correct?  Is there any advantage of using the live boot from 11.04 over 10.10?

I don't know what versions of the programs are included in 11.04 vs. 10.10, offhand, but 11.04 is likely to be more recent. That could translate into bug fixes or other improvements, so as a general principle I'd suggest 11.04, although I don't know if it has any specific and important improvements.

> On a side note, if you know the answer to this great, if not, ok...  So since this is a 10.10 server, what is the best way to call the GUI?  I used ```
sudo startx &
``` but then it launched the gui as root which I'm sure isn't good,

You should be able to do "startx" without the "sudo" and then launch individual programs using "sudo" (or "gksudo" for GUI programs) from a Terminal window. If the relevant software is installed, you should also be able to launch GDM (the GUI login tool) by typing "sudo start gdm".

---

### Post by iconoclast hero on 2011-09-17
> **srs5694 said:**
> I don't know what versions of the programs are included in 11.04 vs. 10.10, offhand, but 11.04 is likely to be more recent. That could translate into bug fixes or other improvements, so as a general principle I'd suggest 11.04, although I don't know if it has any specific and important improvements.



You should be able to do "startx" without the "sudo" and then launch individual programs using "sudo" (or "gksudo" for GUI programs) from a Terminal window. If the relevant software is installed, you should also be able to launch GDM (the GUI login tool) by typing "sudo start gdm".

Ok...  I think I am squared away on this.  Out of curiosity, what is the advantage of having the swap on its own primary partition as opposed to a logical partition?

As for starting the GUI:
If I log in from the local terminal there is no problem with 'startx' without invoking it via sudo, however if I ssh in, I get:
```
@luckier:~$ startx
xauth:  creating new authority file /home/     /.Xauthority
X: user not authorized to run the X server, aborting.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```
odd.

---

### Post by srs5694 on 2011-09-17
> **iconoclast hero said:**
> Ok...  I think I am squared away on this.  Out of curiosity, what is the advantage of having the swap on its own primary partition as opposed to a logical partition?

There's little practical difference between primary and logical partitions for anything (swap space, filesystem, LVM, etc.) from a Linux perspective. The only differences are those that relate to what these partition types are, namely:


[list]
[*]Primary partitions are limited in number to 4 (or 3 and one extended partition), whereas you can have as many logical partitions as you like.
[*]Primary partitions are defined in the primary partition table in the MBR, whereas logical partitions are defined in data structures called Extended Boot Records (EBRs), which are scattered about the disk. Each EBR links to a subsequent one. This makes them somewhat more susceptible to damage; if you've got six logical partitions and something trashes the first one's EBR, you'll lose *all* of the logical partitions, but none of the primary partitions.
[*]Some boot loaders, such as the standard Windows boot loader, can boot only primary partitions. This is of course unimportant for swap space; however, if swap is on a primary partition, this may limit options should you need a primary partition for an OS that requires one to boot.
[/list]


> As for starting the GUI:
If I log in from the local terminal there is no problem with 'startx' without invoking it via sudo, however if I ssh in, I get:
```
@luckier:~$ startx
xauth:  creating new authority file /home/     /.Xauthority
X: user not authorized to run the X server, aborting.
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```odd.

The startx command launches X on the current login device. This works fine if you've logged in at the console; however, if you use SSH to log in remotely, the current login device is that SSH session, and you won't be able to start X over that SSH session. (SSH can run X programs remotely, but to do so you must already have X running on the SSH client computer.)

If you want to log in remotely and start X on the remote computer, the conventional way is to launch an X Display Manager (XDM) program, such as the GNOME Display Manager (GDM) that Ubuntu uses. In Ubuntu, this would be done with the "sudo start gdm" command I mentioned earlier.

---

### Post by iconoclast hero on 2011-09-18
> **srs5694 said:**
> There's little practical difference between primary and logical partitions for anything (swap space, filesystem, LVM, etc.) from a Linux perspective. The only differences are those that relate to what these partition types are, namely:


[list]
[*]Primary partitions are limited in number to 4 (or 3 and one extended partition), whereas you can have as many logical partitions as you like.
[*]Primary partitions are defined in the primary partition table in the MBR, whereas logical partitions are defined in data structures called Extended Boot Records (EBRs), which are scattered about the disk. Each EBR links to a subsequent one. This makes them somewhat more susceptible to damage; if you've got six logical partitions and something trashes the first one's EBR, you'll lose *all* of the logical partitions, but none of the primary partitions.
[*]Some boot loaders, such as the standard Windows boot loader, can boot only primary partitions. This is of course unimportant for swap space; however, if swap is on a primary partition, this may limit options should you need a primary partition for an OS that requires one to boot.
[/list]




The startx command launches X on the current login device. This works fine if you've logged in at the console; however, if you use SSH to log in remotely, the current login device is that SSH session, and you won't be able to start X over that SSH session. (SSH can run X programs remotely, but to do so you must already have X running on the SSH client computer.)

If you want to log in remotely and start X on the remote computer, the conventional way is to launch an X Display Manager (XDM) program, such as the GNOME Display Manager (GDM) that Ubuntu uses. In Ubuntu, this would be done with the "sudo start gdm" command I mentioned earlier.

This gets a bit complicated since, when I was first starting out with installing ubuntu on this computer, I had no idea what I was doing...  I installed Server 10.10 and did a decent job with the partitions.  From there I decided I wanted a gui, so from the apt logs it looks like I did 'sudo apt-get install ubuntu-desktop' (3/23).  Then I got things set up the way I wanted them (like wireless which I no longer use) and was told that GUI was a liability on a server so I decided to get rid of it with 'sudo apt-get remove ubuntu-desktop' then a bunch of other stuff like 'sudo apt-get purge ubuntu-deskop' then it looks like I reinstalled it and then on 3/29 I did 'sudo apt-get purge gdm' so basically the gdm wasn't there to use.

So anyway, when I SSH to the machine from a client running an X session and execute sudo startx, it does work without the server running any instance of X.  I reinstalled gdm last night and, from an SSH session, called sudo start gdm and was able to get it to bring up a login screen.

Now I'm going to try to disable the startup of gdm via rcconf so that it doesn't boot into the GUI...  I don't really need that drag on the system although since March I have migrated the server to a much more powerful machine which is quite capable of handling the GUI interface where the other one really was not.

Does that sound about right?

---

