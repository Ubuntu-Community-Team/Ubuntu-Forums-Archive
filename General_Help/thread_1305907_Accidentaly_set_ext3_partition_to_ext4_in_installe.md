---
title: "Accidentaly set ext3 partition to ext4 in installer - data gone?"
date: 2009-10-30
forum: General Help
---

### Post by Blue Rose on 2009-10-30
Hey all,

I just installed kubuntu 9.10 (I upgraded from 9.04 earlier, but something in the beta karmic broke the sound, it got distorted and nothing helped to fix that, so therefore I just reinstalled karmic from a fresh iso)

I have a ext4 root partition and a ext3 data partition.. unfortunately I set my data partition to ext4 in the installer, where it says use as..
I did not check the format partition box.

Now kubuntu is all set up and ready to go, except that my data partition (now ext4) only shows the lost+found folder... is my data retrievable? or is it gone forgood?
There are a few things that I would really like to get back is it is possible..

Any tips and help are very welcome!!

Thanks in advance
Kind Regards,
Linda

---

### Post by mechro on 2009-10-30
You may be able to restore and fix the partition using Testdisk (available via Synaptic).

---

### Post by philinux on 2009-10-30
Dont use the partition and use testdisks utility photorec. You might be lucky.

Make sure you read the documents first.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Haiyadragon on 2009-10-30
If you didn't format it your data should still be there. Though I don't know enough about EXT4 to be sure.

You can edit your /etc/fstab and replace ext4 with ext3 for that drive. Also add ro (read-only) to the option list for now, so you can't overwrite any data. Then reboot and see if it works. If the ext3 thing works, remove the ro.

If you know how you can unmount and mount as ext3 manually of course.

---

### Post by Blue Rose on 2009-10-30
Thanks for the replies guys, I have not used the disk yet other than mount and browse in dolphin. I will try to remount in etx3 and otherwise testdisk..

I'll let you know :-)

Kind Regards,
Linda

---

### Post by phillw on 2009-10-30
There's some more background stuff here ....

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Regards,

Phill.

---

### Post by Blue Rose on 2009-10-30
Hey all,

I tried the photorec / testdisk software somewhat. It did find a lot of files, but unfortunately the broken partition is over 400GB and my / partition is only 40 GB or so. So my system completely froze when the disk was full, plasma crashed etc. went into a tty to remove the recovered data.

However, I don't mind losing the mp3 and movies on there, just pictures and pdf's if possible. I can't find it in the documents on testdisk, is it possible to retrieve only certain file types?

Oh well, otherwise I will take this as a chance to edit my partition table, and remind myself again why backups are useful :P

Question though, if this had happened with ext2 ext3 would this problem have happened as well? Or is it something new in ext4?

---

### Post by mechro on 2009-10-30
Photorec is for recovering some types of files and data: copying involved.

Testdisk is for recovering partitions i.e. if it works it will restore the ext3 file system and rewrite the partition table so that your drive would be in a similar state as before: no copying of massive amounts of data involved.

---

### Post by mechro on 2009-10-30
> **Blue Rose said:**
> 
Question though, if this had happened with ext2 ext3 would this problem have happened as well? Or is it something new in ext4?

If you're sure you didn't ask to format the partition then it sounds like a problem with the Kubuntu installer.

---

### Post by Blue Rose on 2009-10-31
Ok I will try testdisk tomorrow then (bedtime for me now, it's way past midnight already)

I am 100% sure that I chose "Use partition as" ext4 and set mount point, but I did not check "format partition", thinking everything would be ok then.

I will keep my fingers crossed that I get the testdisk tool working tomorrow, and otherwise just a sour lesson in backups for me :P

Thanks again :)

---

### Post by electronic spark on 2009-11-06
Ubuntu I had ext3 changed to ext4 during upgrade from 9.04 to 9.10.  I can't mount/read hd after upgrade.
But I also have Mint 7 on my system and I ***can read*** ext4 partition.  Funny thing is that Mint7 doesn't list ext4 as option, Ubuntu 9.10 does.
How do I make Ubuntu to be able to read this partition? When I try to mount ext4 partition it comes uo with error can't mount because ext4??

Am I safe to do a Fdisk -A in Mint7 or Ubuntu?

---

### Post by alphaniner on 2009-11-06
You should start a new thread.  But either way, more information is necessary.  When the partition is mounted in Mint, what is the output of the **mount** command (in a terminal)?

---

### Post by HiImTye on 2009-11-06
try running an fsck on the disk. ext3 and ext4 are fully backwards/upwards compatible, unless you enabled extents

---

### Post by electronic spark on 2009-11-06
> **alphaniner said:**
> You should start a new thread.  But either way, more information is necessary.  When the partition is mounted in Mint, what is the output of the **mount** command (in a terminal)?

paul@paul-desktop ~ $ mount
/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb5 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)
/dev/sda1 on /media/320gb type ext4 (rw,nosuid,nodev,uhelper=hal)

---

### Post by electronic spark on 2009-11-06
> **HiImTye said:**
> try running an fsck on the disk. ext3 and ext4 are fully backwards/upwards compatible, unless you enabled extents

paul@paul-desktop ~ $ mount
/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb5 on /home type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/paul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=paul)
/dev/sda1 on /media/320gb type ext4 (rw,nosuid,nodev,uhelper=hal)

---

### Post by shon__ on 2010-05-12
Hi Blue Rose,

I became one more victim of same ext3 -> ext4 thing. I am very sure that I have not checked format but yet by mistake have chosen ext4 for /home. Trying with testdisk no luck so far. PhotoRec is doing the work however files loses name and I suspect many are partial.

Just wanted to know if you/anybody knows a better solution.

Thanks.

---

### Post by Blue Rose on 2010-05-13
Hi Shon_

unfortunately I couldn't get my files back after trying, so I just reinstalled and saw it as a partition cleanup :P
So sorry I can't really help you..

---

### Post by fragos on 2010-05-13
Converting from ext3 to ext4 looses no data nor dose it need to rewrite your data. Make sure that /etc/fstab speicifys ext4.

---

### Post by Endless_Nameless on 2010-11-06
One more victim here. As the others, I just installed without asking to format, but changed from ext3 to ext4 by mistake.

Just tried photorec and testdisk (this one with no results at all). Photorec could save some files, but not near all of them.

Now I am trying to just change the way Ubuntu see the partition.

This happened in 10.10 install. The problem is that in all the other versions, at the end of the installation setup, it would show me what it would do with the partitions, for a manual setup. But in 10.10, it just went to install, with no confirmation screen.

I lost some really important files, that I forgot to make copies.

---

### Post by fragos on 2010-11-06
Here's the instructions I followed a while back to convert my ext3 partitions to ext4 before doing an Ubuntu version upgrade. Perhaps it can help you.

Let's say that you have decided to move your /home partition to ext4, how do you do that? First, you should backup your data. It's always a good idea to have a spare copy of your important files, doubly so when you're changing the characteristics of your hard drive. The next step is to find out which device houses your /home partition. You can do this by running the mount command:

     mount

The mount command will provide a list of partitions, their mount points and file system types. For example:

     /dev/sda1 on / type ext4
     /dev/sda2 on /home type ext3

The above output tells us that the / folder is mounted as ext4 and lives on the sda1 device. The /home folder is formatted as ext3 and lives on the sda2 partition. Now that we know which partition we're dealing with, we can begin work on it. The next step is to unmount the partition so it'll be safe to use. It's a bad idea to change a car's tires while it's moving and it's a bad idea to alter a mounted partition. I recommend logging out of your regular account and logging into a command line session as root for these next steps. Following our above example, we use the commands

     cd /
     umount /dev/sda2

The partition is now ready to be adjusted. Next, run the command

     tune2fs -O extents,uninit_bg,dir_index /dev/sda2

In the above line, that's a "dash oh", not a zero. This is the point of no return. Once you run the tune2fs command, you're committed to ext4. Next we run a check on the new file system:

     fsck -pf /dev/sda2

Once the fsck command is finished, the partition can be remounted using

     mount -t ext4 /dev/sda2 /home

To make sure your computer knows to mount the /home directory as ext4 in the future, open the /etc/fstab file and find the line which mounts "/home". Change the file system type (which is probably the third column in the line) from "ext3" to "ext4".

---

### Post by biltong on 2010-11-28
Hi everyone,

I am another "victim" of the "set ext3 partition to ext4". ](*,)
Has anyone managaned to find a good solution... or are we left to dig out files with photorec / data carver??  [-o<

---

