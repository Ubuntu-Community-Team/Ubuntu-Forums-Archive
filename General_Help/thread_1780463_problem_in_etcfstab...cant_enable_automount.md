---
title: "problem in /etc/fstab...cant enable automount"
date: 2011-06-12
forum: General Help
---

### Post by apoorvmunshi on 2011-06-12
i tried to enable auto mounting by editing the /etc/fstab file but the file's entries arent normal....there should be a 'default' value  under the options column which i will relace by auto but its not there.i have taken a screenshot...plz help...its doesnt show other partitions even after mounting them manually. plz help.

---

### Post by karthick87 on 2011-06-12
Could you post the output of,

```
mount -a
```

---

### Post by apoorvmunshi on 2011-06-12
here it is...no o/p .....??

---

### Post by WorMzy on 2011-06-12
I'm not on Linux at the moment, but I believe that proc should have "defaults" as it's option, and not "auto". I'm not even sure if "auto" is a valid option.

As for why your manually mounted partitions aren't showing up in there, they're not supposed to. They show up in /proc/self/mounts and /etc/mtab. You'll need to manually add the entries to fstab if you want those partitions to be automatically mounted at boot time.

---

### Post by apoorvmunshi on 2011-06-12
ok first i will try to manually add entries to fstab...then i will post replies

---

### Post by apoorvmunshi on 2011-06-12
see these images

---

### Post by WorMzy on 2011-06-12
What's the situation? Have you added entries for sda3 and sda6 in your fstab, or have you just manually mounted them? It looks like they're both NTFS partitions, so I think that I should make sure you're aware of the risks involved with automounting your Windows OS partition. Linux doesn't know (and doesn't care) which files Windows *needs* to be able to boot, which means that you (or anyone else) can make your Windows OS unusable with absolutely no effort at all. If you can avoid automounting your Windows OS, do so.

That said, here's what fstab entries would look like for both of these partitions.

```
/dev/sda3 /media/OS ntfs-3g auto,uid=1000,gid=1000,umask=002 0 0
/dev/sda6 /media/apoorv ntfs-3g auto,uid=1000,gid=1000,umask=002 0 0
```

You'll need to manually create the mount points before the partitions will mount at boot time, so make sure that the partitions are unmounted, then run:
```
sudo mkdir /media/OS /media/apoorv
```

Then run ```
sudo mount -a
``` to test that the partitions mount correctly.

---

### Post by apoorvmunshi on 2011-06-13
thanks for the solution but how automounting windows partition will cause some problems? could you please elaborate on this

---

### Post by WorMzy on 2011-06-13
It doesn't cause problems per se, but it exposes all of your Windows' system files. If you select an important file and press delete, Ubuntu won't warn you that deleting that file will break Windows, and there's no way to protect specific files or folders since NTFS (and FAT) don't support Unix file permissions.

It's better to have a shared data partition if you want to have files accessible on both OSs. That way you can mount the shared partition without putting your Windows' system files in danger.

---

### Post by apoorvmunshi on 2011-06-14
thanks a lot. i will try this. actually i read about /etc/fstab from the book 'linux: the complete reference' and there was no mention about that UUID part. thats y i got confused. the book has given an example of /etc/fstab as shown in image..i guess i will hav to read more about mounting...:D

---

### Post by apoorvmunshi on 2011-06-14
one more question , if i want to enable automounting by modifying /etc/mtab (or /etc/self/mounts,whichever is applicable) then waht should i do?

---

### Post by WorMzy on 2011-06-14
/etc/mtab and /proc/self/mounts just keep track of what you already have mounted, nothing more. Editing either of them won't have any effect, they'll be regenerated the next time you mount something, or reboot.

I don't think you mentioned anything about UUIDs; but they are the preferred way of identifying partitions. If you want to find out what your partition's UUIDs are, run
```
sudo blkid
```

Also, be careful with typos. That last image you posted has "dafaults" listed as the mount options for three of the entries. Not sure if that would cause the mounts to fail, but take care when writing your own.

---

### Post by apoorvmunshi on 2011-06-15
sure sure!! thanks a lot for help . hope to see your replies on my threads...

---

### Post by apoorvmunshi on 2011-06-15
thanks a lot!! now /media/apoorv is mounted automatically . .could you explain me the significance of '-3g auto,uid=1000,gid=1000,umask=002' in the fstab entry? what does these fields indicate ??

---

### Post by WorMzy on 2011-06-15
There is no -3g, it's "ntfs-3g". That's the filesystem type. If it was an ext4 filesystem, you'd put "ext4" there instead.

"auto,uid=1000,gid=1000,umask=002" are the options that you want the filesystem to be mounted with.

auto = automatically mount. That's pretty self explanatory.
uid=1000 = the user ID that takes ownership of the mounted filesystem. On Ubuntu, 1000 is the user ID for the first user you create.
gid=1000 = the group ID that takes ownership of the mounted filesystem. On Ubuntu, 1000 is the default group for the first user you create.
umask=002 = the "mask" you put over the permissions to get them to be what you want. 002 is a generally a good value to use. It means that the user and group will be able to read, write and execute files on the filesystem, but everyone else will only be able to read and execute. [Read up on permissions and umask to understand it better.]("http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html")

---

### Post by apoorvmunshi on 2011-06-15
this part wasnt  in the book. u seem to hav gr8 knowledge abt linux...nice to meet you and thanks again!!:popcorn:

---

### Post by WorMzy on 2011-06-15
No problem. :)

---

