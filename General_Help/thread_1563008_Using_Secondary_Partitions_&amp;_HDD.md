---
title: "Using Secondary Partitions &amp; HDD"
date: 2010-08-28
forum: General Help
---

### Post by charlie_delta on 2010-08-28
Hello.  I'm brand new to Linux & Ubuntu, so please forgive what  seems like some obvious questions.  I've read the Pocket Guide and  searched on the web for answers, but it's still not at all clear to me.

I'm  running Ubuntu 10.04 LTS on an old HP Pavilion 710 PC, dual-booting  with WinXP.  I followed instructions and successfully partitioned my  primary hard drive, and installed Ubuntu just fine (I think--everything  seems to work, anyway).  Here's my partition setup:

```
Primary Disk (/dev/sda) 74.53 GiB
Partition   File System  Mount Point  Label               Size        Flags
/dev/sda1   fat32                     Windows Recovery     4.93 GiB    ---
unallocated unallocated                                   20.16 MiB    ---
/dev/sda2   ntfs                      Windows XP          20.14 GiB    boot
unallocated unallocated                                   21.00 MiB    ---
/dev/sda3   ext3         /boot        GRUBpart             1.95 GiB    ---
unallocated unallocated                                   12.84 MiB    ---
/dev/sda4   extended                                      42.57 GiB    ---
>unallocated unallocated                                    4.16 MiB    ---
>/dev/sda5   linux-swap                [swap]               1.95 GiB    ---
>unallocated unallocated                                    1 MiB       ---
>/dev/sda6   ext4         /            [Ubuntu]            19.53 GiB    ---
>unallocated unallocated                                    1 MiB       ---
>/dev/sda7   ext4         /server      [MySQL]             21.08 GiB    ---
>unallocated unallocated                                    4.87 GiB    ---

```
(> indicates a logical partition under an extended partition.)

```
Secondary Disk (/dev/sdb) 114.49 GiB

Partition   File System  Mount Point  Label               Size        Flags
/dev/sdb1   ntfs                      POLL                37.48 GiB   ---
unallocated unallocated                                  153.93 MiB   ---
/dev/sdb2   extended                                      76.86 GiB   ---
>/dev/sdb5   ntfs                     BETTS                7.30 GiB   ---
>/dev/sdb6   ntfs                     MUTSMAG             29.83 GiB   ---
```The  secondary disk is strangely set up for unrelated reasons, and I haven't  done anything to it since moving to Ubuntu.  My plan is to keep most of  my data on that disk, and use the primary disk for system files and  applications, but I don't yet understand how Ubuntu decides where to  keep things, so I haven't done anything with that disk yet.

Here are my questions:

1.   I want to run a MySQL database locally, to test a php/MySQL web site  I'm developing.  I thought it would be a good idea to set aside a  partition just for the database, which is what /dev/sda7 is supposed to  be; but I have no idea how to make Ubuntu or MySQL use that partition.   (I'm also brand spanking new to MySQL, or I'd probably know.)  How do I  do that?

2.  It occurs to me now that I ought to put the database  on my secondary hard drive, which is much bigger and faster than the  primary.  If the answer to #1 doesn't tell me, how do I do that?

3.   My home directory is on /dev/sda right now.  Can I move my data files  to /dev/sdb without moving the whole home directory?  Or must I move  everything and keep it all together in one directory?

Thanks in advance for any help, and for not telling me to RTFM (I've been reading it, just not getting it.  If you'll tell me what to read, I'll do it!). ;0)

Regards,

Charlie Delta

---

### Post by oldfred on 2010-08-28
I am not familiar with MySQL. So someone else will have to suggest how to change its defaults.

You will need to mount your partitions in fstab. First you create a mount point, and set ownership and permissions (mySQL may need special settings). And then add to fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Some are now recommending mountmanager also in synaptic:

I am a fan of data partitions as I have several system partitions and do not share /home but share all my data.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)


If you cannot read and write then change the permissions. Not for NTFS

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

If you want to manually edit fstab:
# modify fstab to mount directory
sudo cp -a /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
# remount from updated fstab
sudo mount -a
If it just returns it is ok, or it will give you error messages

---

### Post by charlie_delta on 2010-08-28
Thanks for the quick help, Oldfred!  I'll try your advice.

---

