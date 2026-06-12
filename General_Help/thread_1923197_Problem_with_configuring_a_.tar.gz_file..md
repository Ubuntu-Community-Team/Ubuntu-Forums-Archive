---
title: "Problem with configuring a .tar.gz file."
date: 2012-02-10
forum: General Help
---

### Post by mistersnrub on 2012-02-10
I can't configure a .tar.gz archive after extracting it, because the terminal reports as follows:

```
ubuntu@ubuntu:~/Downloads/ms-sys-2.2.1$ ./configure
bash: ./configure: No such file or directory

```I am operating from a ubuntu 11.10 live USB right now. The package I'm trying to install is ms-sys so **I can't use the repositories.**

Thanks for reading, please help :(

---

### Post by nothingspecial on 2012-02-10
Is there a README or INSTALL file with instructions in the extracted folder?

---

### Post by mistersnrub on 2012-02-10
> **nothingspecial said:**
> Is there a README or INSTALL file with instructions in the extracted folder?
yes:-

> 1. General
----------

This program is used to create Microsoft compatible boot records. It is able
to do the same as Microsoft "fdisk /mbr" to a hard disk. It is also able to
do the same as Microsoft "sys d:" to a floppy or FAT partition except that
it does not copy any system files, only the boot record is written.
Specifications of boot records is taken from
[http://www.geocities.com/thestarman3/asm/mbr/MBR_in_detail.htm](http://www.geocities.com/thestarman3/asm/mbr/MBR_in_detail.htm)

The program is useful when using Linux to restore a backup of a reference
Microsoft Windows installation.

Author of this program is Henrik Carlqvist (henca@users.SourceForge.net), it
is available for download from [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

2. Installation
---------------

Step 1, unpack the archive:

tar -xzvf ms-sys*.tgz

Step 2, compile:

cd ms-sys
make

Step 3, become root and install

su (and give password)
make install

3. Examples
-----------

Please note that Windows ME is not useful for making standalone bootable
floppies. However, Win9x and DOS works fine with example 1 and example 3.

Example 1, creating a 1.68 MB bootable floppy:
This example assumes that you have your windows installation mounted at /dosc
and also have mtools and fdformat installed.

fdformat /dev/fd0u1680
mformat a:
ms-sys -w /dev/fd0
mcopy /dosc/io.sys a:
mcopy /dosc/msdos.sys a:
mcopy /dosc/command.com a:


Example 2, restoring a backup to a fresh hard disk:

Step 1, use GNU parted to create your FAT32 partition and file system:

parted (then create partition and file system)

Step 2, write the MBR:

ms-sys -w /dev/hda

Step 3, write the FAT32 partition boot record:

ms-sys -w /dev/hda1

Step 3b, write partition info and drive id to partition:

ms-sys -p /dev/hda1

This step might be needed depending on which program was used to format the
partition. If the program was formatted with gnu parted this step could be
skipped. It is also possible to combine this flag with the previous step
like this: ms-sys -wp /dev/hda1

Step 4, mount your new filesystem:

mount /dev/hda1 /mnt

Step 5, read your backup

cd /mnt; tar -xzvf /path/to/my_windows_backup_file.tgz


Example 3, creating a bootable 2.8 MB floppy image for use with an el-torito
bootable CD:

dd if=/dev/zero of=floppy288.img bs=1024 count=2880
/sbin/mkdosfs floppy288.img
ms-sys -1 -f floppy288.img
su
mount -o loop floppy288.img /mnt
cp msdos.sys /mnt/
cp io.sys /mnt/
cp command.com /mnt/
(it might also be a good idea to add a config.sys and autoexec.bat with
 CDROM support)
umount /mnt
exit
cp floppy288.img cd-files/eltorito.img
mkisofs -b eltorito.img -c eltorito.cat -o cdimage.iso cd-files
(burn the file cdimage.iso to a CD with cdrecord or another program)

4. Documentation
----------------

There is a man-page for ms-sys, and you will get some help by typing:

ms-sys --help

5. Known problems
-----------------

There have been reports about unbootable FAT32 partitions created with
"mformat -F c:". One workaround is to use gnu parted to create the
partition instead. Since version 1.1.3 ms-sys has the switch -p which
is supposed to fix this problem. The problem has also been reported on
partitions formatted with mkdosfs and mkfs.vfat.

There have been yet another problem reported about the -p switch and gnu
parted together with Linux kernel 2.6. The problem is that kernel 2.6 might
report a geometry incompatible with other operating systems. There is a
detailed description of the problem at
[http://groups-beta.google.com/group/linux.kernel/msg/404d8683ce302cf2](http://groups-beta.google.com/group/linux.kernel/msg/404d8683ce302cf2)
As a workaround for this ms-sys now has the switch -H to manually set the
number of heads. The next problem is to find out what value for number of
heads to give. If the system was booted by LILO this can be shown by
"lilo -T geom".

There have been reports about problems when compiling against uClibc. More
problem reports or suggestions of fixes are welcome!

---

### Post by nothingspecial on 2012-02-10
It says to type ```
make
```

Not ```
./configure
```

---

### Post by mistersnrub on 2012-02-10
> **nothingspecial said:**
> It says to type ```
make
```
 
Not ```
./configure
```
 
I've tried this, but I'm given error 127 which google says indicates missing files which would be pointed out by configure?

---

### Post by drmrgd on 2012-02-10
Are any of the previous steps throwing an error?  I found that the tar command they gave in the README didn't work, and wouldn't uncompress the archive.  Try this:

```
tar xvf ms-sys-2.2.1.tar.gz
```

If that completes successfully, you should see a stream of files as it uncompresses it into a new directory. Then go into the newly made directory:

```
cd ms-sys-2.2.1/
```

Then run:

```
make
```

which should start compiling the package, and you should see a stream of text.  

Please let us know if you get any errors and list those errors along with the exact commands that you typed with the code tags (the little hash mark) so that we can try to figure out what's going on.  I suspect the problem was that you were not successful in uncompressing the archive, and then couldn't get into it to run make properly.

---

### Post by WorMzy on 2012-02-10
You'll need to have build-essential installed if you want to compile things.

---

### Post by Gremlinzzz on 2012-02-10
sudo apt-get install build-essential checkinstall

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
:popcorn:

---

