---
title: "Regularly Occuring Ext4 Filesystem Corruption"
date: 2010-09-07
forum: General Help
---

### Post by chienpo on 2010-09-07
Hi all, I've got a very frustrating problem.

I've got an *Ubuntu Server 10.04.1* system running as a mail server. The system is running as a KVM/libvirt-based virtual machine, hosted on another Ubuntu Server 10.04.1 virtual host system. 

The mail system's main "drive" is a VM image file in QCOW2 format. The physical host machine also has a 1.5 TB drive (_/dev/sdc_ on the virtual host) that is passed through to the mail virtual machine as _/dev/vda_ using the *virtio *driver (from libvirt machine definition XML):
```

...
  <disk type='block' device='disk'>
    <source dev='/dev/sdc'/>
    <target dev='vda' bus='virtio'/>
  </disk>

```The mail server has partitioned the 1.5 TB drive (_/dev/vda_) into two partitions, each with an ext4 filesystem:
```

/dev/vda1 mounted as: _/var/mail_ (label=*mailboxes*)
/dev/vda2 mounted as: _/var/mail/archive_ (label=*archive*)

```The *mailboxes* partition (/var/mail) is slightly under 1 TB while the *archive* partition (/var/mail/archive) is about 0.5 TB. The mailboxes partition holds all active users' *Maildir* folders. The archive partition holds an archived copy of every email message that is received/sent (well, actually a queue for a custom archiving daemon that ultimately stores it on another system).

When first setup, the mailboxes and archive partitions were stored together on one big 1.5 TB partition. However, I experienced regular filesystem corruption that appeared to be the result of this bug: [COLOR=Red][https://bugs.launchpad.net/ubuntu/lucid/+source/qemu-kvm/+bug/574665](https://bugs.launchpad.net/ubuntu/lucid/+source/qemu-kvm/+bug/574665)[/COLOR]

So, I worked around this bug by having my largest partition (my mailboxes partition) approx. 1023 GB (916 GB usable space once formatted). The archive partition is half that size. I used the following parameters when formatting:
```
sudo mke2fs -b 4096 -i 4096 -I 256 -m 1 -vt ext4 -L label /dev/vdaX
```(note that I wanted more inodes as I expect the average file size to be smaller)

The system has now worked without any filesystem-corruption issues for several weeks now. Then, this morning I got an email from a backup process that rsyncs everything in _/var/mail_ to a backup server. It contained several lines of these error messages:
```

rsync: readlink_stat("/archive/queue/email-2010-08-30-15:52:33-1563.eml" (in mail)) failed: Input/output error (5)
...

```There were also be messages like the following in my /var/log/kern.log file:
```

Sep  7 08:42:03 mail kernel: [1084993.457374] EXT4-fs error (device vda2): ext4_ext_check_inode: bad header/extent in inode #43515936: invalid extent entries - magic f30a, entries 1, max 4(4), depth 0(0)

```Attempts to delete or even list the corrupt files fail:
```

# ls /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml
ls: cannot access /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml: Input/output error
# rm /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml
rm: cannot remove `/var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml': Input/output error

```So, anyone experience similar errors or have any ideas? The virtual host machine is a Dell PowerEdge R710 that has been in use for a few months and the drive is likewise only months old. My prior experience with the bug (linked to above) using large filesystems with virtio makes me wonder if this is still the same bug (or a similar bug) that is merely triggered less frequently now or not.

I'm starting to think I should "downgrade" everything (ext3 filesystems, more mature version of Ubuntu or use Debian, etc.) for stability's sake as I've been fighting one 10.04-server glitch after another (though kudos to devs for getting so many fixed so quickly).

Anyone have any ideas, including what other info I could provide to debug this issue?

---

### Post by bab1 on 2010-09-07
> **chienpo said:**
> Hi all, I've got a very frustrating problem.

I've got an *Ubuntu Server 10.04.1* system running as a mail server. The system is running as a KVM/libvirt-based virtual machine, hosted on another Ubuntu Server 10.04.1 virtual host system. 

The mail system's main "drive" is a VM image file in QCOW2 format. The physical host machine also has a 1.5 TB drive (_/dev/sdc_ on the virtual host) that is passed through to the mail virtual machine as _/dev/vda_ using the *virtio *driver (from libvirt machine definition XML):
```

...
  <disk type='block' device='disk'>
    <source dev='/dev/sdc'/>
    <target dev='vda' bus='virtio'/>
  </disk>

```The mail server has partitioned the 1.5 TB drive (_/dev/vda_) into two partitions, each with an ext4 filesystem:
```

/dev/vda1 mounted as: _/var/mail_ (label=*mailboxes*)
/dev/vda2 mounted as: _/var/mail/archive_ (label=*archive*)

```The *mailboxes* partition (/var/mail) is slightly under 1 TB while the *archive* partition (/var/mail/archive) is about 0.5 TB. The mailboxes partition holds all active users' *Maildir* folders. The archive partition holds an archived copy of every email message that is received/sent (well, actually a queue for a custom archiving daemon that ultimately stores it on another system).

When first setup, the mailboxes and archive partitions were stored together on one big 1.5 TB partition. However, I experienced regular filesystem corruption that appeared to be the result of this bug: [COLOR=Red][https://bugs.launchpad.net/ubuntu/lucid/+source/qemu-kvm/+bug/574665](https://bugs.launchpad.net/ubuntu/lucid/+source/qemu-kvm/+bug/574665)[/COLOR]

So, I worked around this bug by having my largest partition (my mailboxes partition) approx. 1023 GB (916 GB usable space once formatted). The archive partition is half that size. I used the following parameters when formatting:
```
sudo mke2fs -b 4096 -i 4096 -I 256 -m 1 -vt ext4 -L label /dev/vdaX
```(note that I wanted more inodes as I expect the average file size to be smaller)

The system has now worked without any filesystem-corruption issues for several weeks now. Then, this morning I got an email from a backup process that rsyncs everything in _/var/mail_ to a backup server. It contained several lines of these error messages:
```

rsync: readlink_stat("/archive/queue/email-2010-08-30-15:52:33-1563.eml" (in mail)) failed: Input/output error (5)
...

```There were also be messages like the following in my /var/log/kern.log file:
```

Sep  7 08:42:03 mail kernel: [1084993.457374] EXT4-fs error (device vda2): ext4_ext_check_inode: bad header/extent in inode #43515936: invalid extent entries - magic f30a, entries 1, max 4(4), depth 0(0)

```Attempts to delete or even list the corrupt files fail:
```

# ls /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml
ls: cannot access /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml: Input/output error
# rm /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml
rm: cannot remove `/var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml': Input/output error

```So, anyone experience similar errors or have any ideas? The virtual host machine is a Dell PowerEdge R710 that has been in use for a few months and the drive is likewise only months old. My prior experience with the bug (linked to above) using large filesystems with virtio makes me wonder if this is still the same bug (or a similar bug) that is merely triggered less frequently now or not.

I'm starting to think I should "downgrade" everything (ext3 filesystems, more mature version of Ubuntu or use Debian, etc.) for stability's sake as I've been fighting one 10.04-server glitch after another (though kudos to devs for getting so many fixed so quickly).

Anyone have any ideas, including what other info I could provide to debug this issue?

I would ask Ted Tso.  He is the developer/maintainer  of EXT4.  You can contact him at: tytso_at_thunk.org.  His blog is: [http://thunk.org/tytso/blog/]("http://thunk.org/tytso/blog/")

---

### Post by melendro on 2010-11-02
> **chienpo said:**
> There were also be messages like the following in my /var/log/kern.log file:
```

Sep  7 08:42:03 mail kernel: [1084993.457374] EXT4-fs error (device vda2): ext4_ext_check_inode: bad header/extent in inode #43515936: invalid extent entries - magic f30a, entries 1, max 4(4), depth 0(0)

```Attempts to delete or even list the corrupt files fail:
```

# ls /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml
ls: cannot access /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml: Input/output error
# rm /var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml
rm: cannot remove `/var/mail/archive/queue/email-2010-08-30-15:52:33-1563.eml': Input/output error

```

Hi chienpo,

I've got exactly the same problem as you: EXT4-fs error (device sda1): ext4_ext_check_inode: bad header/extent in inode #90116: invalid extent entries - magic f30a, entries 2, max 4(4), depth 0(0)

I cannot delete the file and, every time the system tries to access it, the filesystem is marked as corrupted and Ubuntu cannot boot. I have to boot from the installation CD and run a fsck on the device. The fsck doesn't report any error, but it marks the filesystem as clean and I can boot again from the hard disk.

Did you contact the EXt4 developer or solve our problem in any way? I don't want to contact the developer if you already did it.

Thanks in advance.

---

### Post by melendro on 2010-11-02
Solution found!

The following command removed the corrupted file (it was really a dir):

# debugfs -w -R 'rmdir /lost+found/#90116' /dev/sda1

If it is not a dir but a file, then try using rm or kill_file instead of rmdir (I didn't test it because mine was a dir).

Not sure if the filesystem needs to be unmounted first, I did it unmounted.

---

### Post by Fastolfe on 2010-12-11
> **chienpo said:**
> 
When first setup, the mailboxes and archive partitions were stored together on one big 1.5 TB partition. However, I experienced regular filesystem corruption that appeared to be the result of this bug: [COLOR=Red][https://bugs.launchpad.net/ubuntu/lucid/+source/qemu-kvm/+bug/574665](https://bugs.launchpad.net/ubuntu/lucid/+source/qemu-kvm/+bug/574665)[/COLOR]

So, I worked around this bug by having my largest partition (my mailboxes partition) approx. 1023 GB (916 GB usable space once formatted). 

I don't think this is sufficient to avoid the bug you're referencing.  The problem is with the mapping of writes to the block device on the host.  It's the guest that's interpreting the partition table on that device and interpreting those partitions as an ext4 filesystem, not the host.  From the host's perspective you're doing IO against the same 1.5T block device that you were before you repartitioned.  Since the bug occurs with ordering writes to sectors on that block device, it seems logical to me that you're going to be exposed to the same bug.

Try splitting the block device on the host (keeping each one below 1T) and expose the new devices as separate block devices on your guest.  In theory, it seems like you could even use LVM in the guest to concatenate the two block devices together again to give you your 1.5T filesystem if you wanted to.

David

---

### Post by ivotrivella on 2011-02-15
I'm through the same problem here...


Fastolfe,

I didn't get exactly how to split the block device on the host... Doesn't KVM exports the whole device, even if the disk is partitioned?
(see 'source dev' in my .xml)

In my .xml i have this:

```

[...]
    <disk type='block' device='disk'>
      <driver name='qemu' type='raw'/>
      <source dev='/dev/sdc'/>
      <target dev='vda' bus='virtio'/>
    </disk>
[...]

```

---

