---
title: "Getting ownership of a drive?"
date: 2009-11-14
forum: General Help
---

### Post by TBBucs on 2009-11-14
I just installed Ubuntu 9.10 and have a FAT32 partition for my documents.  It's /dev/sda4 and has a mount point of /media/documents.

So, I don't have ownership of the drive apparently, as I can't write to it, unmount it, or anything like that.  I tried doing this:

```
chown -R root:root /media/documents
```

...but that just gave me the error "changing ownership of `/media/documents': Operation not permitted".

Here's my fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=7f3dbc22-990e-47f0-89cb-1d710022e923 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=75afe615-cfa0-4119-8b6f-960336afd149 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /media/documents vfat defaults 0 0
```

But I can only open fstab in read-only mode because I "don't have permission" to do otherwise.

Any ideas?

---

### Post by scouser73 on 2009-11-14
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by coffeecat on 2009-11-14
This is your problem:

> **TBBucs said:**
> 
```
/dev/sda4 /media/documents vfat defaults 0 0
```

You need more options than just 'defaults'. Have a look at this community document:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Scroll down a bit. There are a couple of sample fstab lines for vfat. Adapt them for your device and mountpoint and you should be OK.

**Y**ou do not need to change the ownership/permissions of /media/documents if you get the fstab line right.

---

### Post by TBBucs on 2009-11-14
Edit: The fstab line is what did it.  I am now the owner of the drive.  However, I've encountered another problem.  I imported some mp3 files from the drive into Banshee, but Banshee can't play them (I just get an X).  I checked the permissions of the file, and I here's what I found:

```
Owner: (my username)
Access: Read and Write
Groups: users (I tried changing this to my username, but I get an error saying I don't permission to do that)
Access: Read and Write
Others
Access: Read and Write
```

and here's what I did to my fstab:

```
/dev/sda4       /media/documents vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
```

---

### Post by coffeecat on 2009-11-14
Yes, that's a good line. The problem with both FAT32 and NTFS is that, being Microsoft filesystems, they don't support Unix/Linux ownership and permissions, which is why you can't change permissions/ownership with 'Properties' in Nautilus or chmod/chown from the terminal. You have to rely on the options you set up in fstab - or udev rules when automounting external drives. The latter is not a problem in Ubuntu because the udev rules are done for you.

In your fstab line, the uid has given you 'owner' ownership, the gid group ownership, and the umask very liberal read/write permissions for everyone.

So - have you solved the Banshee problem? It wasn't clear.

---

### Post by TBBucs on 2009-11-14
Thanks for the explanation coffeecat.  No, the Banshee problem has yet to be solved.

---

### Post by tommynz1975 on 2009-11-14
this information is pinched from.

[HTML]http://rutsum.com/how-to-get-the-ownership-of-your-own-usb-drive-back-on-linux[/HTML]  article June 10th 2008


[INDENT]```
 $	sudo chmod +t /media/ 
```
[/INDENT] And that was it. Now **all USB drives** will be mounted in write mode, irrespective of their filesystem.




I hope this adds to your ball of knowledge

---

### Post by TBBucs on 2009-11-14
^ Thanks for that tidbit :)

Interesting, Rhythmbox can import and play music files just fine, but Banshee can't.  Not sure what to think of that.  Also, I tried testing out other documents using other applications (like importing photos with fspot), and it worked just fine.  So far only Banshee is having trouble.

---

