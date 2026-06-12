---
title: "Unable to Mount CD's"
date: 2009-10-29
forum: General Help
---

### Post by jpanoff on 2009-10-29
Hello;

I am an absolute noob, will really appreciate your help.

I'm trying to watch movies or listen to music from dvd's or Cd's but my computer is unable to mount them. Every time I insert a disc it shows as being blank.

Here is the command that I tried and the fstab. 

julio@ubuntu:~$ sudo mount /dev/scd0 /media/cdrom0
[sudo] password for julio: 
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: you must specify the filesystem type
julio@ubuntu:~$ 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3304a6ae-6be3-4e3e-85a5-56db5c258055 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c39a4edb-982c-4199-be51-eb962f3c004b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I'm using 8.10 Ubuntu Hardy

Thank you so much, 
Looking forward to your answers.

PS
I can burn dvds fine.

---

### Post by Zoot7 on 2009-10-29
Normally CDs mount automatically and you don't have to do more. Your fstab looks okay aswell.

Try out this
```
sudo mount -t cd9660 /dev/sdc0 /mnt
```

Then see if you can access /mnt.

Also give this a shot aswell
```
sudo mount /media/cdrom0/ -o unhide
```

---

### Post by jpanoff on 2009-10-29
Hi Zoot 7, thanks alot for your help. 
Unfortunately that didn't work either. 

Here is what I got:

```

julio@ubuntu:~$ sudo mount -t cd9660 /dev/sdc0 /mnt
mount: unknown filesystem type 'cd9660'
julio@ubuntu:~$ sudo mount /media/cdrom0/ -o unhide
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

julio@ubuntu:~$
```

---

### Post by Zoot7 on 2009-10-29
Was it working before or is this only recent? And is this true of all CDs/DVDs?

Also what is the output of 
```
dmesg | tail
```
?
After trying to mount a CD.

---

### Post by nikgare on 2009-10-29
You don't mount audio cds!

---

### Post by jpanoff on 2009-10-29
Hi Zoot7;
I've just inserted an image file of a DVD I made and it works, I also inserted another dvd and it mounted but I was unable to open it's it says contents could not be displayed because You do not have the permissions necessary to view the contents of "DVD_RTAV". I am the administrator for this computer though.

But the CDR cd that I really want to see it does not mount at all. 
here is the dmesg | tail information I got ```
julio@ubuntu:~$ sudo mount /media/cdrom0/ -o unhide
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

julio@ubuntu:~$ dmesg | tail
[19248.520245] end_request: I/O error, dev sr0, sector 0
[19248.520273] Buffer I/O error on device sr0, logical block 0
[19248.524660] end_request: I/O error, dev sr0, sector 0
[19248.524681] Buffer I/O error on device sr0, logical block 0
[19326.667979] end_request: I/O error, dev sr0, sector 64
[19326.688672] end_request: I/O error, dev sr0, sector 1024
[19326.695537] end_request: I/O error, dev sr0, sector 2048
[19326.695596] UDF-fs: No partition found (1)
[19326.711451] end_request: I/O error, dev sr0, sector 64
[19326.711514] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
julio@ubuntu:~$ 

```
[I][/I

---

### Post by jpanoff on 2009-10-29
Hi nikgare, 
What do you mean by you don't mount Audio CD's. How can I listen to them without mounting them?

---

### Post by stinger30au on 2009-10-29
what version of ubuntu are u using???

---

### Post by jpanoff on 2009-10-29
here is an image with the information of my ubuntu. 
Ubuntu Studio 8.10 Intrepid 
Kernel Linux 2.6.27-7-generic
Gnome 2.24.1

I hope that helps. 

By the way audio cds do not work, but some dvd's do. 
Zoot7, it has always been like this. Since I got this Ubuntu Studio version.

---

### Post by Zoot7 on 2009-10-29
> **jpanoff said:**
> julio@ubuntu:~$ dmesg | tail
[19248.520245] end_request: I/O error, dev sr0, sector 0
[19248.520273] Buffer I/O error on device sr0, logical block 0
[19248.524660] end_request: I/O error, dev sr0, sector 0
[19248.524681] Buffer I/O error on device sr0, logical block 0
[19326.667979] end_request: I/O error, dev sr0, sector 64
[19326.688672] end_request: I/O error, dev sr0, sector 1024
[19326.695537] end_request: I/O error, dev sr0, sector 2048
[19326.695596] UDF-fs: No partition found (1)
[19326.711451] end_request: I/O error, dev sr0, sector 64
[19326.711514] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
julio@ubuntu:~$ 
[/CODE]
[I][/I
Based on that I'd nearly say there's a hardware problem with the drive itself. Is there a diagnostic program that you got with the machine you could run to investigate?
Beyond that I'm not sure what to suggest. Sorry I can't be of more assistance. :)

---

### Post by jpanoff on 2009-10-31
> **Zoot7 said:**
> Based on that I'd nearly say there's a hardware problem with the drive itself. Is there a diagnostic program that you got with the machine you could run to investigate?
Beyond that I'm not sure what to suggest. Sorry I can't be of more assistance. :)

Thanks a lot for your help. 

I don't know what to use to run a diagnosis of my hardware, but everything seems to be working fine just some kind of cds wont mount on my machine. 

It's kind of sad.

---

