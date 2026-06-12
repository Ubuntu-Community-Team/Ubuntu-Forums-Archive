---
title: "Hot Imaging An Ubuntu System"
date: 2009-09-18
forum: General Help
---

### Post by jameskinds on 2009-09-18
Greetings,

Does anyone know of any hot imaging system backup solutions for Ubuntu i.e. software that creates a disc image of the system while the operating system is running.

In Windows there is an application (DriveImage XML - [http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)) which allows for this functionality (but only for Windows).

Thanks in advance.

James

PS: This is one of the last applications I need to find in order to complete my switch from Windows.

---

### Post by falconindy on 2009-09-18
```
sudo dd if=/dev/sdxy of=/path/to/file/name
```No need for extra software. Ubuntu doesn't have the issues that Windows does with files being in use and being locked for reading by anyone else. However, there are programs such as Clonezilla out there that will image your drive for you probably with some more options.

If you need more info about dd, you can do `man dd`. I just used this utility 2 days ago to recover data from an unmountable (crashed) hard drive.

---

### Post by Aearenda on 2009-09-18
Be aware that 'dd' will copy all the unused space in your partition. I don't think I'd want to do it this way, but I can't think of anything that meets this particular need for hot partition imaging. I have successfully used 'rsync' to clone the filesystem in a partition to another partition while that system is running, but I still don't think its a good idea. Something like:
```
rsync -ax --exclude "/backup/*" --exclude "/proc/*" --exclude "/lost+found/*" --exclude "/tmp/*" --exclude "/media/*" --exclude "/sys/*" --delete / /backup/
```Here /backup is the mount point of my alternate partition, so it's excluded from the copying.

However, I really suggest you test this thoroughly before relying on it. There are probably better ways using LVM snapshots, but I haven't looked at that.

---

### Post by falconindy on 2009-09-18
> **Aearenda said:**
> Be aware that 'dd' will copy all the unused space in your partition.
True, I did neglect to mention that. However, maybe that's just more encouragement to take the time to properly partition your disk! ;)

---

### Post by jameskinds on 2009-09-20
Hi All,

Thanks for the replies.

Both "dd" and "rsync" offer helpful pointers.

Based one the research that I have done, there appears to be almost universal guidance not to use "dd" on a live/running system. The consensus seems to be that the image produced may have produce a file system that is in an inconsistent state.

"rsync" seems to be a better option in this regard, however it is still not exactly what I am looking for i.e. it operates at a file based level as opposed to a disc based level.

The program "partimage" seems to be ideal for my purposes, bar the fact that it too needs to be run on an unmounted system.

Ideally I am looking for a program like partimage but that can be run from on a live/hot system.

Any more ideas?

Thanks again for all your help so far.

Kind regards,

James

---

### Post by Aearenda on 2009-09-20
I still think you should look at [LVM snapshots]("http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html"). The drawback is you have to set this up at partition creation time. This is the way good Windows backup systems work.

See also [http://www.howtoforge.com/linux_lvm_snapshots](http://www.howtoforge.com/linux_lvm_snapshots) and [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm).

---

### Post by jameskinds on 2009-09-20
> **Aearenda said:**
> I still think you should look at [LVM snapshots]("http://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html"). The drawback is you have to set this up at partition creation time. This is the way good Windows backup systems work.

See also [http://www.howtoforge.com/linux_lvm_snapshots](http://www.howtoforge.com/linux_lvm_snapshots) and [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm).


Thank you for the links. I've had a quick scan over the intros and LVM's look very promising. I will research this in detail.

Thanks again for all your help!

Regards,

James

---

