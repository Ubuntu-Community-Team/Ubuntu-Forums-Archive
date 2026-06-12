---
title: "Filesysten type - truble mounting external drive through shell"
date: 2009-10-09
forum: General Help
---

### Post by Gosport on 2009-10-09
I am trying to mount my external hard drive through the shell (my graphic environment is kput)  

I get a message that I must specify the file system type.  The drive is an old MAXTOR.  Over 100GB I think.

Any Ideas?

---

### Post by Boondoklife on 2009-10-09
Are you doing as it asks? You need to feed it the -t option with the correct selection so it knows how to mount it.

> -t vfstype
              The  argument following the -t is used to indicate the file sys&#8208;
              tem type.  The file system types which are  currently  supported
              include:  adfs,  affs,  autofs,  cifs,  coda,  coherent, cramfs,
              debugfs, devpts, efs, ext, ext2, ext3, ext4, hfs, hfsplus, hpfs,
              iso9660,  jfs, minix, msdos, ncpfs, nfs, nfs4, ntfs, proc, qnx4,
              ramfs, reiserfs, romfs, smbfs, sysv, tmpfs,  udf,  ufs,  umsdos,
              usbfs,  vfat,  xenix,  xfs, xiafs.  Note that coherent, sysv and
              xenix are equivalent and that xenix and coherent will be removed
              at  some  point  in  the future &#8212; use sysv instead. Since kernel
              version 2.1.21 the types ext and xiafs  do  not  exist  anymore.
              Earlier,  usbfs  was  known as usbdevfs.  Note, the real list of
              all supported filesystems depends on your kernel.


---

