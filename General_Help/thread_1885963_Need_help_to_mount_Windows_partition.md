---
title: "Need help to mount Windows partition"
date: 2011-11-24
forum: General Help
---

### Post by woam on 2011-11-24
Hi all!

My windows crashed yesterday, and now it won't boot (See this thread for more info: [http://www.pchelpforum.com/windows-vista-7/123552-cannot-start-windows-help.html](http://www.pchelpforum.com/windows-vista-7/123552-cannot-start-windows-help.html))

Anyways, I want to rescue my files from the windows partition, and I have not succeeded so far.

I've looked at several guides, who all, pretty much, uses the same method. However, this method is not working for me.

When I try to just view to OSDisk it says:

```
Error mounting: mount exited with exit code 12: Failed to read last sector (312575999): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

My guess is that the Windows partition is corrupted.

I've tried several times to mount it with both ntfs-3g and ntfsprogs, and failed.

Here are some of my tried outputs:


```
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo mkdir /media/windows sudo ntfs-3g -o rw /dev/sda1 /media/windows
[sudo] password for ubuntu: 
mkdir: ogiltig flagga -- "o"
Försök med "mkdir --help" för mer information.
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo ntfs.3g .o force,rw /dev/sda1/media/windows
sudo: ntfs.3g: command not found
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo ntfs-3g .o force,rw /dev/sda1/media/windows
ntfs-3g: Failed to access volume '.o': Filen eller katalogen finns inte

ntfs-3g 2011.4.12AR.4 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 7, XATTRS are on, POSIX ACLS are on

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2011 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

News, support and information:  [http://tuxera.com](http://tuxera.com)
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo apt-get install ntfs-3g
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
ntfs-3g är redan den senaste versionen.
Följande paket har installerats automatiskt och är inte längre nödvändigt:
  libntfs10
Använd "apt-get autoremove" för att ta bort dem.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 238 att inte uppgradera.
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo mkdir /media/windows
mkdir: kan inte skapa katalog "/media/windows": Filen existerar
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo ntfs-3g -o rw /dev /media/windows
Error opening '/dev': Är en katalog
Failed to mount '/dev': Är en katalog
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo ntfs-3g -o rw /dev/ /media/windows
Error opening '/dev': Är en katalog
Failed to mount '/dev': Är en katalog
ubuntu@ubuntu-ThinkPad-X100e:~$ sudo ntfs-3g -o rw /dev/sda1/ /media/windows
ntfs-3g: Failed to access volume '/dev/sda1/': Inte en katalog

ntfs-3g 2011.4.12AR.4 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 7, XATTRS are on, POSIX ACLS are on

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2011 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows


```
Some of the output responses are in swedish, and i'm sorry for that, but I hope that you can see what's happening anwyays.

Thanks a lot for your time!!! :)

---

### Post by Script Warlock on 2011-11-24
have you tried slaving the hard drive to another computer running ubuntu?

---

### Post by nothingspecial on 2011-11-24
Hi there,

When posting terminal output or code/scripts etc please use code tags. They make it a lot easier to read and therefore help with your issue.

The easiest way to do this is to highlight the text then click the # in the formatting options at the top of the posting box.

Thanks.

---

### Post by satanselbow on 2011-11-24
[edit]You made and error in your initial "mount" and the folder would not have been created - using a "." where a "-" should be in the subsequent mount command - so the mount point folder would not have been created and the mount command was badly formed...

the mkdir and mount command should be on separate lines (ie press enter between each one)

Given that the command was wrong - output could be suspect or misleading...

What does fdisk tell you?

```
# fdisk -l
```

BTW if you open up nautilus you might be able to see your windows partitions there and simply click to mount ;)

---

### Post by WasMeHere on 2011-11-24
Välkommen till UbuntuForums, woam!

> **Script Warlock said:**
> have you tried slaving the hard drive to another computer running ubuntu?
... or slaving the hard drive to another computer running Windows and run ```
chkdsk /r [COLOR="Red"]F:[/COLOR]
``` ([COLOR="Red"]F:[/COLOR] or whatever volume ID for the windows partition)

This simple method has helped me several times. By the way, I have ***BartPE*** on CD and USB drives, to run  [FONT="Courier New"]chkdsk /r[/FONT] directly in the damaged computer.

Lycka till :-)
Olle

---

### Post by rustyD on 2011-11-24
If you have the windows disc you can run that and use the option to repair the installtion, I've done that a few times.
 
If you have another windows pc available you can run the HD as a slave and use the command prompt for the bcd and also check the master boot record. There are plenty of posts around to follow which give good step-by-step instructions how to do that.

---

### Post by woam on 2011-11-24
> What does fdisk tell you?


```
ubuntu@ubuntu-ThinkPad-X100e:~$ fdisk -1
fdisk: ogiltig flagga -- "1"
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

ubuntu@ubuntu-ThinkPad-X100e:~$ 
```


> If you have the windows disc you can run that and use the option to repair the installtion, I've done that a few times.

I do not have the windows disc available, since it is a school pc. (Assuming you mean the Windows installation disc)


> BTW if you open up nautilus you might be able to see your windows partitions there and simply click to mount 

I can see "OSDisk" under Devices (which I assume is windows?), though when I click on it I get an error message, the one I wrote in my first post.

Also, how do I slave the harddrive to another computer? Is it done by taking apart the hdd from the pc, and connect to another?
In that case I'd like to avoid it, if possible, to ensure no void guarantee.

Thanks a ton for your help guys/gals!!! :)

---

### Post by motoso on 2011-11-24
If it's a problem with the NTFS partition, you can try a fix I just used for my external, although the error code wasn't exactly the same.

Try this in a terminal :
```
sudo apt-get install ntfsprogs
```

and 

```
sudo ntfsfix /dev/sda1
```

replacing /dev/sda1 with whatever harddrive you are trying to read.

---

### Post by collisionystm on 2011-11-24
try installing ntfs-config from the software center. It has always worked for me to mount a windows drive.

---

### Post by fdrake on 2011-11-24
@woam
its fdisk -l(lower case "L") not fdisk -1. Also you need root priviledge to run it. so try
```

sudo fdisk -l

```

---

### Post by woam on 2011-11-24
> **motoso said:**
> If it's a problem with the NTFS partition, you can try a fix I just used for my external, although the error code wasn't exactly the same.

Try this in a terminal :
```
sudo apt-get install ntfsprogs
```

and 

```
sudo ntfsfix /dev/sda1
```

replacing /dev/sda1 with whatever harddrive you are trying to read.

YES!! Thank you so much :grin:

that seems to work!!

Also, thanks to everybody else who answered!

I posted this on a windows forum too, and wow. On the windows-forum i've gotten like 2 answers in 2 days.
Here i've gotten like 10 in 1 day!!! :D

Yet again, I can't thank you enough for this, thanks to you all!

---

