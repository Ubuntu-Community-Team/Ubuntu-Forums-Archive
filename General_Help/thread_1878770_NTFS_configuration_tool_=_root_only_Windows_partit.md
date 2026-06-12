---
title: "NTFS configuration tool = root only Windows partition?"
date: 2011-11-10
forum: General Help
---

### Post by Kitira on 2011-11-10
Okay, so here's the scoop. I've searched all over for different ways to handle this and have found very little help with the exact problem I'm dealing with. I started with a Windows Vista partition and an Ubuntu (10.04 Lucid) partition. I use Ubuntu almost exclusively, yet like to access files on the Windows partition frequently. I wanted to have the folder I access most frequently be an icon on my desktop for easier access. (No, at the time I didn't know this meant perma-mounting.) I downloaded the Ntfs config tool thinking it would help me. It did not do what I wanted it to. It made the partition mounted all the time and every time I tell NTFS config to not allow read or write access to that drive, it only has root permissions and they _cannot_ be changed. (ie. using root account, nautilus, etc.) I don't want to have it accessible only by root and wish to return to the status the partition had before I used NTFS config at all. I have attempted to comprehend how fstab works, only to find people asking for specific fstab results to be posted, so I'll include that here as well if that can help anyone. If anyone has any idea how I can just get the windows partition not to be root-only and immediately mount upon my trying to open it the way it did when I first loaded Ubuntu, I would truly be grateful. Heck, if anyone with a dual-boot system could just take a look at their fstab and compare notes, maybe I could figure out what's been changed and how to fix it.

Not sure what PQService is actually. It is getting the same treatment as the Windows partition. Book Of Secrets is the Windows drive.
Fstab contents are as follows:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda3 :
UUID=70ae90b5-8f2a-435a-b1e4-3de55ae26488    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
UUID=B224B6AE24B67547    /media/Book\040Of\040Secrets    ntfs    defaults,nls=utf8,umask=0000,user    0    0
#Entry for /dev/sda1 :
UUID=F09EE55D9EE51CBA    /media/PQSERVICE    ntfs    defaults,nls=utf8,umask=0000    0    0
#Entry for /dev/sda5 :
UUID=a33f03f0-75ab-4241-97c9-eb3bb50a820b    none    swap    sw    0    0



---

### Post by pastalavista on 2011-11-10
I think the easiest way to edit hard-disk mounting rules is with a python application called "Storage Device Manager" ( pysdm ) available in the software center. It's just a matter of checking the right boxes.

The geeky way is to manually edit /etc/fstab ( [link]("https://help.ubuntu.com/community/Fstab") ) Change "ntfs defaults" to "ntfs-3g" and that should do it.

---

### Post by satanselbow on 2011-11-10
> **Kitira said:**
> 
Not sure what PQService is actually.

It is the recovery partition to restore your vista back to factory defaults.

---

### Post by Kitira on 2011-11-10
> **pastalavista said:**
> 
The geeky way is to manually edit /etc/fstab ( [link]("https://help.ubuntu.com/community/Fstab") ) Change "ntfs defaults" to "ntfs-3g" and that should do it. This didn't work. :( Even after reboot, it's all still root-only. I'd much prefer to edit fstab into submission if there's a way to. I don't really like the idea of downloading another program to fix the first program's changes. I'd prefer to get my hands dirty and know exactly what's been changed.

> **satanselbow said:**
> It is the recovery partition to restore your vista back to factory defaults. Oooooohhh...Cool! Thank you for that! :)

---

### Post by ajgreeny on 2011-11-10
Check that ntfs-3g is installed as I have come across one or two cases in 11.10 where it seems not to have been, causing big problems with permissions in ntfs partitions.

---

### Post by Kitira on 2011-11-10
> **ajgreeny said:**
> Check that ntfs-3g is installed as I have come across one or two cases in 11.10 where it seems not to have been, causing big problems with permissions in ntfs partitions.

It is...libntfs-3g-dev isn't, though. Is it necessary?

---

### Post by pastalavista on 2011-11-10
> **Kitira said:**
> It is...libntfs-3g-dev isn't, though. Is it necessary?
I don't have libntfs-3g-dev, but I do have libntfs-3g79. I'm still on 11.04 though.

---

### Post by Mark Phelps on 2011-11-10
Didn't see you mention this, but have you tried modifying fstab so it mounts the partition read-only?  

That is really the safest way to mount a Window OS partition, as mounting it read-write, and then making changes to it from inside Ubuntu runs the risk of corrupting the filesystem.

As to the "dev" package, from my experience, you only need those if you're going to compile source -- which doesn't sound like what you're doing.

---

### Post by Kitira on 2011-11-10
> **Mark Phelps said:**
> Didn't see you mention this, but have you tried modifying fstab so it mounts the partition read-only?  

That is really the safest way to mount a Window OS partition, as mounting it read-write, and then making changes to it from inside Ubuntu runs the risk of corrupting the filesystem.

As to the "dev" package, from my experience, you only need those if you're going to compile source -- which doesn't sound like what you're doing.

As I don't tend to mess with any files in Windows except for non-essentials, I was hoping to maintain the read-write ability. I'm also the only user, considering I'm using a laptop to do this on. And no, I'm not compiling any source just yet, at least. lol Maybe after a bit more study...

---

### Post by Kitira on 2011-11-10
Is there any part of the fstab that doesn't look right to anyone? Any part that I'm missing or could try to change, aside from ntfs-3g? Or perhaps this permissions issue could be changed elsewhere?

---

### Post by Kitira on 2011-11-10
SOLVED! I figured this puppy out! Actually found my answer on a Linux Mint forum with someone with the same problem. Answer is to throw # in front of each partition that's not behaving. Fstab now looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda3 :
UUID=70ae90b5-8f2a-435a-b1e4-3de55ae26488    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda2 :
#UUID=B224B6AE24B67547    /media/Book\040Of\040Secrets    ntfs-3g,nls=utf8,umask=0000,user    0    0
#Entry for /dev/sda1 :
#UUID=F09EE55D9EE51CBA    /media/PQSERVICE    ntfs-3g,nls=utf8,umask=0000,user    0    0
#Entry for /dev/sda5 :
UUID=a33f03f0-75ab-4241-97c9-eb3bb50a820b    none    swap    sw    0    0

If there are any negative effects anyone knows of this causing, please let me know, but this really seems to have done the trick perfectly!

---

### Post by Morbius1 on 2011-11-10
1st: ntfs-config hasn't been maintained since Jimmy Carter was President. ( pysdm - not since Regan ) . These might be slight exaggerations  :)

2nd: The reason you have read / write access to that partition is because you or something set umask to 0000. Umask represents the permissions you want to take away from the default ntfs mount which is 777 btw. So as it stands every folder and every file is read/write/executable to everyone.

If you want it read only then set umask to 0222.

3rd: Your rewrite of that line in fstab made things worse:
> UUID=B224B6AE24B67547    /media/Book\040Of\040Secrets    ntfs-3g,nls=utf8,umask=0000,user    0    0
Get rid of the comma between "ntfs-3g" and "nls=utf8" - it should be a space.

4th: Get rid of the "user" option. The only user at the time fstab is executed is root which owns the partition anyway so it's redundant.

---

### Post by Kitira on 2011-11-10
Interestingly enough, umask was set to 0000 from the time I installed Ubuntu forward. I've always had read/write/execute as the standard for all partitions. Don't understand why, but I don't have any problems with it being that way for now. I have done #3 and #4, though it doesn't seem to have made any changes. I read that putting the # in front of the UUID line actually turns it into a comment. Does this mean that basically the entire line is rendered invalid?

---

### Post by Morbius1 on 2011-11-11
> Interestingly enough, umask was set to 0000 from the time I installed Ubuntu forward.Ubuntu doesn't set umask to 000 explicitly in fstab by default for ntfs partitions. If you had the installer mount these non system disks it will mount the partition with:
owner = root
group = plugdev
permissions = 770
If you mount them from Places or Nautilus it will mount with owner=group=you and permissions of 700.
> I've always had read/write/execute as the standard for all partitions.That's not the way Linux works. At a directory level Linux will mount all partitions ( except those with Windows filesystems ) with read/write/execute to the owner ( which will be root for everything other that your home directory ) and read/execute for everyone else. 
> I have done #3 and #4, though it doesn't seem to have made any changes.If you set the line in fstab to look like this:
>                               UUID=B224B6AE24B67547    /media/Book\040Of\040Secrets    ntfs-3g defaults,umask=0222,nls=utf8    0    0                      And you still have write access then post the output of the following command:
```
ls -dl "/media/Book Of Secrets"
```> I read that putting the # in front of the UUID line actually turns it  into a comment. Does this mean that basically the entire line is  rendered invalid? Yes

I'm beginning to think that you never created the mount point.

---

