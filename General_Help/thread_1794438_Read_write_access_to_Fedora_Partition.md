---
title: "Read write access to Fedora Partition"
date: 2011-07-01
forum: General Help
---

### Post by satish_j on 2011-07-01
On opening nautilus,it shows the XP ad Fedora partitions.Clicking on them mounts the partition.However,XP partitions are mounted in Read/write mode,whereas Fedora partition is mounted only in Read mode.
What changes should i need to make in /etc/fstab to enable Read/Write access to Fedora partition as well?
Thanks..

---

### Post by Rubi1200 on 2011-07-01
Hi,
it would be helpful if you posted your fstab:

```
cat /etc/fstab
```

This link also provides useful information:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by satish_j on 2011-07-11
> **Rubi1200 said:**
> Hi,
it would be helpful if you posted your fstab:

```
cat /etc/fstab
```

This link also provides useful information:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Sorry, i was stuck up with some imp tasks..
I had a look at /etc/fstab and saw this fedora partition details with 'ro' text somewhere at the end of line.i assumed it to be 'Read-Only',so i modified it to 'rw' (Read-Write).After saving it and rebooting,Ubuntu would not drop to the Login window at all..just the splash screen..so,i had to revert it back to 'ro' to get it working..
I will post the fstab file later today as iam at office now..

---

### Post by satish_j on 2011-07-13
Ok,here is the fstab file:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=3b3a0f99-fb76-4d16-970c-5a514fcd22b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a8713bc-be38-436a-8ffa-4c2d1401dcdb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
By the way,i do not want to mount FEdora partition at boot(i guess fstab is for that only)
All i want is to fedora partition to get mounted in RW mode from Nautilus..
Anyone??

---

### Post by oldfred on 2011-07-13
See post by Morbius1 on the issues:

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by nothingspecial on 2011-07-13
Fedora, by default uses uid and gid 500

Ubuntu uses 1000

The way I would dual boot (if I was to set up an entirely new system), would be - Install Fedora first. Their installer allows you to specify your own uid and gid, so set it to 1000.

Then install Ubuntu (with exactly the same username and password. Ubuntu's installer (with grub2) will automagically add Fedora to the boot options.)

As long as you have the same uid and gid you can share stuff without a problem :D

---

### Post by satish_j on 2011-07-19
> **nothingspecial said:**
> 
As long as you have the same uid and gid you can share stuff without a problem :D

If i change UID on fedora from 500 to 1000(i.e same as Ubuntu),then would _Nautilus_ mount Fedora partition in Read/write mode??

---

### Post by nothingspecial on 2011-07-19
Yes. I'd have the same username and password also, but am not sure if that is necessary.

---

### Post by satish_j on 2011-07-25
does changing the userid and groupid affects the permission settings  of files and directories?
if i change userid and groupid on fedora for a particular user,then all the files and directories owned by that user will have same permissions/ownership or will i have to manually change it?

---

### Post by satish_j on 2011-07-27
I just changed the uid and gid on fedora to 1000 for my userid,rebooted into Ubuntu,opened fedora partition in Nautilus and tried to create a folder/file in it.It still is not allowing me to write to fedora partition..
so,i guess having same uid and gid does not have any effect..3
any other ideas?

---

### Post by satish_j on 2011-08-02
edited fstab file to add foll
```

UUID=145cfrr... /home/satish/Fedora  ext4  0  0

```
Fedora Partition is getting mounted at mentioned path at boot,but again,with only Read rights for user 'satish'.
checked and found root as owner of Partition.
Is there anyway to mount it with Read/Write access to my Ubuntu ID?

---

### Post by Topsiho on 2011-08-02
My guess, and it is only a guess, but it would be strange if it is otherwise: probably you should set the permissions in Fedora, so that the world gets the necessary permissions ...
This way you should also be able to finetune these permissions.

Topsiho

---

### Post by oldfred on 2011-08-02
It looks like you left off the parameters.

Since Hardy (or Intrepid), Ubuntu adds the relatime option by default.
relatime = relatime + defaults = relatime, rw, suid, dev, exec, auto, nouser and async

So, I would replace defaults with relatime:
```
UUID=26c15cxx-YourUUID   /home/satish/Fedora   ext4  relatime    0    1

```
If you do this after any edits:

sudo mount -a

IF no errors then fstab is ok.

---

### Post by satish_j on 2011-08-04
:mad::mad:
changed /home/satish/Fedora to /mnt/Fedora,still it was getting mounted in Read-only
so i did foll:
```

sudo chown -R satish /mnt/Fedora

```
And,now i cannot boot into Fedora.It gives error as 'could not update ICEauthority file /var/lib/gdm' followed by 'There is a problem with the configuration server (/usr/libexec/gconf-sanity-check-2 exited with status 256)
I tried reverting back using
```

sudo chown -R root /mnt/Fedora

```
Googled and found some solutions,tried changing owner of /mnt/Fedora/home/ to user(me),also tried changing 777 chmod /mnt/Fedora/tmp/
but problem remains.
Any ideas how to solve this?Very Urgent..

---

