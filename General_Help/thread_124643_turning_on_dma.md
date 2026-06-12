---
title: "turning on dma"
date: 2006-02-01
forum: General Help
---

### Post by psilo357 on 2006-02-01
im trying to follow this guide [http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/) and i cant seem to get DMA enabled, this is what i get when i check with hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

and when i try to turn it on i get this

randy@ubuntu:~$ hdparm -d /dev/hdd

/dev/hdd:
 using_dma    =  0 (off)
randy@ubuntu:~$ hdparm -d /dev/hdd

/dev/hdd:
 using_dma    =  0 (off)

the same crap over and over again, it will not turn on, and if i try and follow the guide above to turn it on this is what it says

randy@ubuntu:~$ sudo /etc/hdparm.conf
sudo: /etc/hdparm.conf: command not found

so i think a little and try this

randy@ubuntu:~$ sudo gedit /etc/hdparm.conf

and this is the bottom part of the file it opens in gedit

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
       dma = on
}

first off, i see no dev/hdd, and every line that says DMA is set to on already, any help on what im doing wrong or what i need to change would be great.

thanks

---

### Post by soulestream on 2006-02-01
is your device /dev/hdd?

post your /etc/fstab


soule

---

### Post by psilo357 on 2006-02-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/my_media vfat    iocharset=utf8,umask=000 0 0
/dev/hdb5       /media/my_storage vfat  iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


thanks for the quick help, also, i will be using dvddecrypter to rip the dvd to the media/my_storage/dvdtemp file if that is possible

thanks for the help and quick reply

EDIT:   some more info i thought might help, it seems that DMA is turned ON with one dvdrom, but not the other, wierd, well here is the hdparm of each of the roms

randy@ubuntu:~$ hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
randy@ubuntu:~$ hdparm /dev/hdc

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
randy@ubuntu:~$

---

### Post by rharris on 2006-02-01
Have you checked this out:

[https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)

Just follow the wiki instructions but substitute hdd for hdc as used in the example.

Worked for me but YMMV

Rob

---

### Post by akiro.yamamoto on 2006-02-01
sudo hdparm -d1 /dev/hdd
Note the [ 1 ] is very important..... otherwise all your doing is quering about the dma status of /dev/hdd. To set dma to off use [ 0 ] instead.
To make it permanent
add this to the end of /etc/hdparm.conf

/dev/hdd {
       dma = on
}

That should do the trick....  ;)

---

### Post by psilo357 on 2006-02-02
thanks guys, i got it working

now to try wine, dvd decrypter, and dvd shrink

peace

---

