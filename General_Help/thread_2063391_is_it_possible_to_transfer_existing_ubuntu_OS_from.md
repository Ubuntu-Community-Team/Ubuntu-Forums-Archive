---
title: "is it possible to transfer existing ubuntu OS from one hard disk to another?"
date: 2012-09-27
forum: General Help
---

### Post by fuzzylogic25 on 2012-09-27
Hello,

I currently have the older version of ubuntu 10.04, and wish to upgrade my hard disk that it is on. Its currently on a 300GB Sata drive. But I wish to now transfer the OS onto a 120GB SSD hard disk, as its much faster!

The ubuntu partition is only 100GB so it shouldnt be a problem.

But how would I go about doing this? Is there some utility i can use? I am assuming its not a simple copy all files to the other hard disk task.

---

### Post by mdurham on 2012-09-27
> **fuzzylogic25 said:**
> Hello,

I currently have the older version of ubuntu 10.04, and wish to upgrade my hard disk that it is on. Its currently on a 300GB Sata drive. But I wish to now transfer the OS onto a 120GB SSD hard disk, as its much faster!

The ubuntu partition is only 100GB so it shouldnt be a problem.

But how would I go about doing this? Is there some utility i can use? I am assuming its not a simple copy all files to the other hard disk task.

I think "partimage" might do what you want, have a look at it.

---

### Post by HiImTye on 2012-09-27
it should be fairly simple to do it, so long as you mark the drive bootable and you make sure to install grub correctly. you can follow the instructions on how to install grub here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
the only caveat, is if you are going to change from ATI to nVidia, or vice-versa. that will make the whole process more complex, but still quite doable.

---

### Post by mdurham on 2012-09-27
> **HiImTye said:**
> it should be fairly simple to do it, so long as you mark the drive bootable and you make sure to install grub correctly. you can follow the instructions on how to install grub here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
the only caveat, is if you are going to change from ATI to nVidia, or vice-versa. that will make the whole process more complex, but still quite doable.
Why mark the drive 'bootable'? Linux doesn't use that.

---

### Post by dcstar on 2012-09-27
> **fuzzylogic25 said:**
> Hello,

I currently have the older version of ubuntu 10.04, and wish to upgrade my hard disk that it is on. Its currently on a 300GB Sata drive. But I wish to now transfer the OS onto a 120GB SSD hard disk, as its much faster!

The ubuntu partition is only 100GB so it shouldnt be a problem.

But how would I go about doing this? Is there some utility i can use? I am assuming its not a simple copy all files to the other hard disk task.

**gparted** - copy and paste.

---

### Post by mikewhatever on 2012-09-27
> **mdurham said:**
> I think "partimage" might do what you want, have a look at it.

Partimage doesn't support ext4 file systems.

---

### Post by HiImTye on 2012-09-27
> **mdurham said:**
> Why mark the drive 'bootable'? Linux doesn't use that.
you're right, I'm used to using USB drives, which require the boot flag.

---

### Post by jingaling on 2012-09-27
If you have room to have both drives connected at the same time then I would boot from a live CD and use Gparted to clone all the paritions from one drive to the other.

Failing that you could use something like Clonezilla or Acronis to backup and restore the drive. Clonezilla will only clone partitions of the same size or larger though, so if your actuall partition(s) are bigger than 120GB it total then I'd go for Acronis (providing you have a license of course).

Jing

---

### Post by asmoore82 on 2012-09-27
Clonezilla [SIZE="3"]+1[/SIZE]
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2012-09-27
Are you keeping old drive? If so an image copy will have issues with duplicate UUIDs. You have to manually update fstab, reinstall grub and some other settings. You also have to manually change UUIDs on the partitions as you cannot have duplicate UUIDs.

Actually you can reinstall or do a full new clean install just about as easy and it is more straight forward. All your user settings & data is in /home and that is the main thing you need to copy.

With an SSD you may also want to modify some system settings and even change partitioning from MBR to gpt as suggested by this Arch site. You do have to use AHCI (BIOS setting) for SSD to work well,  if you are not already using AHCI.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

With SSD, many of us just put operating system on SSD and have our data on the rotating drive. So I split my /home into the hidden settings and leave that part in my / (root) and on rotating drive mount data partition(s) and link the data back into my /home.

---

### Post by HiImTye on 2012-09-27
> **oldfred said:**
> So I split my /home into the hidden settings and leave that part in my / (root) and on rotating drive mount data partition(s) and link the data back into my /home.
I keep my Ubuntu install on its' own partition, and use a data partition at /storage/ and just make links to the appropriate folders on the storage partition, replacing my stock home folders. this way I can keep some important settings that I spend time making changes to (such as mpd's settings, or LuaKit's), and my 'storage' folders (such as 'Videos' and 'Music') without having to worry about compatibility issues of settings files with a clean install of a new version. also, this works as a great way to consolidate data folders accross accounts (sharing music, etc)

---

