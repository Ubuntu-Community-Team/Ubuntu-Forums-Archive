---
title: "Reformatting an NTFS Drive"
date: 2006-06-10
forum: General Help
---

### Post by Zikes on 2006-06-10
I have some removable hard drives I'd like to use in Ubuntu, but they're currently formatted in NTFS.  I'm not worried about any of the old data, I just can't seem to reformat the drives at all.  I've tried using gparted and reformatted them to ext3 & fat32, but I keep getting an error and the format doesn't take.

Anyone know what I might be doing wrong?

---

### Post by aysiu on 2006-06-10
What's the error?

Did you unmount the partition before trying to reformat it?

---

### Post by Zikes on 2006-06-10
"**Error while formattting (sic) filesystem of /dev/sda1**
Be aware that the failure to apply this operation could affect other operations on the list."

I unmounted, deleted the partition, right-clicked on the now unallocated partition and clicked New, then chose to create as primary partition with a filesystem of fat32.

Is there a way to do it from the command line?  I might get a more informative error message that way.

---

### Post by Zikes on 2006-06-10
I tried again and got a slightly different error message:

"**Error while creating /dev/sda1**

Be aware that the failure to apply this operation could affect other operations on the list."

---

### Post by aysiu on 2006-06-10
[QUOTE=Zikes]
Is there a way to do it from the command line?  I might get a more informative error message that way.[/QUOTE] If you can make sense of this: ```
PARTED(8)                      GNU Parted Manual                     PARTED(8)

/

NAME
       GNU Parted - a partition manipulation program

SYNOPSIS
       parted [options] [device [command [options...]...]]

DESCRIPTION
       This  manual page documents briefly the parted command.  Complete docu&#8208;
       mentation is distributed with the parted-doc Debian package in GNU Info
       format; see below.

       parted  is  a  disk  partitioning  and  partition resizing program.  It
       allows you to create, destroy, resize, move and copy ext2, ext3, linux-
       swap,  FAT,  FAT32, and reiserfs partitions.  It can create, resize and
       move Macintosh HFS partitions, as well as detect jfs,  ntfs,  ufs,  and
       xfs partitions.  It is useful for creating space for new operating sys&#8208;
       tems, reorganising disk usage, and copying data to new hard disks.

OPTIONS
       -h, --help
              displays a help message.

       -i, --interactive
              prompt the user where necessary.

       -s, --script
              never prompt the user.

       -v, --version
              displays the version.

COMMANDS
       [device]
              The block device to partition.

       [command [options]]
              Specifies a command to parted. If no command  is  given,  parted
              will give you a command prompt. Commands are:

              check partition
                     does a simple check on partition.

              cp [source-device] source dest
                     copies the source partition&#8217;s filesystem on source-device
                     (or the current device if no other device was  specified)
                     to the dest partition on the current device.

              help [command]
                     prints general help, or help on command if specified.
              mkfs partition fs-type
                     make  a  filesystem  fs-type on partition. fs-type can be
                     one of "fat16", "fat32", "ext2", "linux-swap"  or  "reis&#8208;
                     erfs".

              mklabel label-type
                     Creates  a new disklabel (partition table) of label-type.
                     label-type should be one of "bsd", "dvh", "gpt",  "loop",
                     "mac", "msdos", "pc98" or "sun".

              mkpart part-type [fs-type] start end
                     make  a  part-type  partition with filesystem fs-type (if
                     specified), beginning at start  and  ending  at  end  (in
                     megabytes).   fs-type  can  be  one  of "fat16", "fat32",
                     "ext2", "HFS", "linux-swap", "NTFS", "reiserfs" or "ufs".
                     part-type  should  be  one  of  "primary",  "logical"  or
                     "extended"

              mkpartfs part-type fs-type start end
                     make a part-type partition with filesystem fs-type begin&#8208;
                     ning at start and ending at end (in megabytes)

              move partition start end
                     move  partition  to  start at start and end at end. Note:
                     move never changes the minor number

              name partition name
                     set the name of partition to name. This option works only
                     on  Mac  and  PC98  disklabels. The name can be placed in
                     quotes, if necessary

              print  displays the partition table

              quit   exits parted

              resize partition start end
                     resize the filesystem on partition to start at start  and
                     end at end megabytes

              rm partition
                     deletes partition

              select device
                     choose  device  as  the  current  device  to edit. device
                     should usually be a Linux hard disk device, but it can be
                     a partition, software raid device or a LVM logical volume
                     if that is necessary

              set partition flag state
                     change the state of the flag on partition to state. Flags
                     supported  are: "boot", "root", "swap", "hidden", "raid",
                     "lvm", "lba" and "palo".  state should be either "on"  or
                     "off"

REPORTING BUGS
       Report bugs to <bug-parted@gnu.org>

SEE ALSO
       fdisk(8),  mkfs(8),  The  parted  program  is  fully  documented in the
       info(1) format GNU partitioning software manual.

AUTHOR
       This manual page was written by Timshel Knoll <timshel@debian.org>, for
       the Debian GNU/Linux system (but may be used by others).

parted                           18 Mar, 2002                        PARTED(8)
``` Maybe you should try it with a live CD? I know it's unmounted already, but the live CD may make a difference for whatever reason.

By the way, do you have the *ntfsprogs* package installed?

---

### Post by Zikes on 2006-06-10
I think I got it figured out.  I found that gparted is using the mkdosfs command to make fat32 filesystems, so I did a man and found that there's an -I switch that forces it to work where it otherwise wouldn't.

>        -I     Normally  you  are  not  allowed  to  use  any &#8217;full&#8217; fixed disk
              devices.  mkdosfs will complain and tell you that it refuses  to
              work.   This  is  different  when  usind  MO disks.  One doesn&#8217;t
              always need partitions  on  MO  disks.   The  filesytem  can  go
              directly  to  the whole disk.  Under other OSes this is known as
              the &#8217;superfloppy&#8217; format.

              This switch will force mkdosfs to work properly.

I don't know what a MO disk is, or "'full' fixed disk", but it ended up working when I did it manually with that switch.

I don't have ntfsprogs installed, but I heard there was a project underway to bring full ntfs support to linux.  I get the impression the support's a bit shaky at the moment, so I'm hesitant to rely on it.  Have you had any experience with it?

---

### Post by aysiu on 2006-06-10
The only thing shaky about NTFS support right now is modifying and deleting and creating files on an NTFS partition from Linux.

Everything else is peachy-keen. You can shrink NTFS partitions. You can delete them. You can read off them.

---

### Post by Zikes on 2006-06-10
Ahh I'll have to pass, then.  I'm intending to use them as storage drives for Windows and Linux, and will be doing a lot of reading & writing from both.  Thanks for the info, though :)

---

### Post by aysiu on 2006-06-10
FAT32 can be read/write from both.
And Ext3 can be read/write from both with [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by Fred Doolie on 2006-06-10
[QUOTE=aysiu]And Ext3 can be read/write from both with [http://www.fs-driver.org](http://www.fs-driver.org)[/QUOTE]

That's the way I have mine set up. With that installed Winblows can read/write Ext3 as if it were FAT32 or NTFS. One problem though and I hope somebody out there can explain. 

I can copy my "My Documents" onto a NTFS partiton just fine but when copying onto an ext3 I get errors about too-long filenames and bad characters and such. My guess is Windows doesn't follow standard rules concerning filenames.

---

