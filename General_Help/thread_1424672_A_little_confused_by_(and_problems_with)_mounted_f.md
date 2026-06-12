---
title: "A little confused by (and problems with) mounted filesystem"
date: 2010-03-08
forum: General Help
---

### Post by Donny Bahama on 2010-03-08
I have an ntfs partition set up to function as a shared filestore between Ubuntu and Windows 7. 

I don't remember where I read the procedure, but I previously had this mounted as /media/store, and if I browsed to computer:///  it showed up as a filesystem (called "FileVault") right next to "Filesystem" and "CD-RW/DVD±RW Drive".

Then I found out that /media is for transient mounts and permanently mounted filesystems should be under /mnt. I was having trouble with it anyway, so I unmounted it, edited /etc/fstab and rebooted. Now it no longer shows up as its own filesystem under computer:/// and I have no idea how to get that back.

As for the troubles I was (and still am) having,  there's a lot I can't seem to do with this filesystem - even as root. I seem to be able to read and execute anything, but I can't delete or rename directories - even after doing```
chmod -R 777 /mnt/vault
```Please help a noob understand this weirdness! :)

Thanks for your time and consideration.

---

### Post by ad_267 on 2010-03-08
> **Donny Bahama said:**
> Now it no longer shows up as its own filesystem under computer:/// and I have no idea how to get that back.

The only mounted partitions that show up in computer:/// are the one's in /media so you could just put it back there, it won't hurt. Partitions are mounted "invisibly" so you don't have to know you're even accessing a separate hard drive.

> As for the troubles I was (and still am) having,  there's a lot I can't seem to do with this filesystem - even as root. I seem to be able to read and execute anything, but I can't delete or rename directories - even after doing```
chmod -R 777 /mnt/vault
```Please help a noob understand this weirdness! :)

I don't think you can apply Linux permissions to an NTFS partition. The file permisions depend on how it's mounted in /etc/fstab.

Quoted from the [how to fstab]("http://ubuntuforums.org/showthread.php?t=283131") post:
> 
Ownership and permissios of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or GID #.

umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

Best is to set directories with executable permissions and file with read write. To do this, use fmask and dmask (rather then umask):
dmask=027
fmask=137

With these options files are not executable (all colored green in a terminal w/ ls)

So if you've got one user on your computer the easiest thing to do would be to add uid=1000

---

### Post by Donny Bahama on 2010-03-08
Thanks so much for the very helpful and informative response!
> **ad_267 said:**
> The only mounted partitions that show up in computer:/// are the one's in /media so you could just put it back there, it won't hurt. Partitions are mounted "invisibly" so you don't have to know you're even accessing a separate hard drive.Cool. Did that and it worked.
> I don't think you can apply Linux permissions to an NTFS partition. The file permisions depend on how it's mounted in /etc/fstab.That makes sense.
> Quoted from the [how to fstab]("http://ubuntuforums.org/showthread.php?t=283131") post:Thanks for the link to that post!
> So if you've got one user on your computer the easiest thing to do would be to add uid=1000OK, so (per the recommendation in the 'how to fstab' post), I downloaded pysdm and ran it. My fstab now reads
```
/dev/sda3   /media/vault   ntfs-3g   nls=iso8859-1,users,umask=000,user,owner,uid=donny      0  0  
```I also tried setting umask to '1000' per your instructions as well as setting uid=root. After unmounting and remounting, I continue to be unable to delete an empty directory (error says the directory isn't empty but it is -- 'sudo ls -al' shows it to be empty) nor can I rename directories (returns input/output error.) 

What in the heck is going on here?!

---

### Post by ad_267 on 2010-03-09
Hmm that's pretty weird. Your fstab line looks ok, thought the owner, user and users options are usually for removable drives I think, but that shouldn't be a problem.

Do you use this drive on Windows and does it work properly? Do you have any problems reading or writing to other directories on the drive or is it just this one directory?

You could try checking the drive for errors, it's probably best to use the Windows file system check tool, but you could also try fsck in linux too. To do that you would need to unmount the drive first.
```
sudo umount /dev/sda3
sudo fsck -r /dev/sda3
```

---

### Post by Donny Bahama on 2010-03-10
> **ad_267 said:**
> Do you use this drive on Windows and does it work properly?I have used it in Windows in the past, but now it just stays connected to my server.> Do you have any problems reading or writing to other directories on the drive or is it just this one directory?Seems to be all of them.
> You could try checking the drive for errors, it's probably best to use the Windows file system check toolOK, I did that and it seemed to help. Thanks very much for the helpful response! :)

---

### Post by Donny Bahama on 2010-03-13
> **Donny Bahama said:**
> OK, I did that and it seemed to help. Thanks very much for the helpful response! :)Update: it didn't actually help. That's OK. With the help of GParted and rsync, I'm in the process of exorcising the ntfs demons from my server. I won't rest until all MS filesystems have been eradicated and replaced!

---

