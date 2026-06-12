---
title: "Is NTFS a good file system for a shared partition between Ubuntu and WinXP?"
date: 2010-05-30
forum: General Help
---

### Post by bttf on 2010-05-30
Someone on IRC had mentioned they had a shared partition in NTFS, and that Ubuntu could read from it just fine... I wanted to get a second opinion before I did anything. Right now I have a WinXP partition and an Ubuntu partition, and a large NTFS partition in the middle that I'd like to move my /home to. Good idea or no?

Thanks

---

### Post by plutoniumpenguin on 2010-05-30
I don't think you can move /home there, because NTFS does not have the required features of a linux filesystem.  At least, the installer wouldn't let me do it.  There's probably a way around that, but I haven't bothered with it.  I use an NTFS partition to share documents and files between Win7 and Ubuntu systems (I'm sure WinXP would work just the same),except that in my /home folder I just have links to folders in the shared NTFS partition.

---

### Post by srs5694 on 2010-05-30
You should *not* attempt to use an NTFS partition as a /home partition, since some programs may need to use Unix/Linux filesystem features within users' home directories. You can, however, mount an NTFS partition in Linux (even in your own home directory, such as /home/bttf/shared, if you use /home/bttf as your home directory) and share your data that way. Ubuntu uses NTFS-3g for NTFS support, and this works reasonably well for most people.

FAT has a few advantages over NTFS as a shared-data partition, but it's also got disadvantages. For instance, there are Linux-native FAT filesystem check utilities, so if your system crashes in Linux, you'll probably be able to access the FAT partition after you reboot in Linux. (If you use NTFS, you might need to boot Windows first to check the drive.) The biggest drawback to FAT is that it can't handle files larger than 4GB.

You can use the Linux-native ext2fs or ext3fs for shared data, too, but you'll need to install an appropriate Windows driver. I have little experience with these drivers, so I can't comment on them in detail. Overall, this option seems to be fairly unpopular.

Most people seem to prefer using NTFS for Linux/Windows file sharing. This is what I use most of the time these days, too, although I still favor FAT if I don't expect to have need to share files larger than 4GB.

---

### Post by WorMzy on 2010-05-30
Yes, NTFS is arguable the best filesystem for a Linux-Windows shared partition. However, instead of moving /home to an NTFS partition, it's better to mount --bind your Documents, Videos, Music, etc., folders to folders on the shared partition.

For example, I have my /home on an ext3 partition, and I have a Linux-Windows shared partition mounted at /media/Terastore. I've binded /media/Terastore/Downloads to /home/wormzy/Downloads, etc., by editing /etc/fstab.

This is what my fstab looks like:

```
proc                                      /proc                   proc nodev,noexec,nosuid                                          0 0
UUID=097bbeed-7751-448f-bfb5-01f9bc9d76ac /                       ext4 errors=remount-ro                                            0 1
UUID=81a74526-3735-439d-bdc4-529da6f53080 none                    swap sw                                                           0 0
UUID=8bc4257a-62af-47ae-8c69-5001f7ec7249 /home                   ext3 defaults                                                     0 2
UUID=7A5C94995C94522D                     /media/Terastore        ntfs user,uid=1000,gid=1000,umask=007,dmask=007,fmask=007,exec,rw 0 0
/media/Terastore/Collection/              /home/wormzy/Collection none bind                                                         0 0
/media/Terastore/Users/WorMzy/Pictures/   /home/wormzy/Pictures   none bind                                                         0 0
/media/Terastore/Users/WorMzy/Documents/  /home/wormzy/Documents  none bind                                                         0 0
/media/Terastore/Downloads/               /home/wormzy/Downloads  none bind                                                         0 0
/media/Terastore/Videos/                  /home/wormzy/Videos     none bind                                                         0 0
```

As you can see, all my major /home folders are actually stored in /media/Terastore, so I can save Documents (etc.) normally, and still have them accessible from Windows.

---

### Post by bakegoodz on 2010-05-30
I format my external drive to EXT2 that I move files between my XP computer at work and my Ubuntu system at home. You can get the Windows driver here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

A few thing you need to know
The drive can't be formatted with the Ubuntu default 256 byte inode size. Use command mkfs.ext2 -I 128 /dev/sdx to do 128 byte inodes

There is trick to make the drive work on Windows 7 until a newer driver comes out that officially works with it, otherwise it refuses to install.
You goto file properties on the driver installer and use Vista compatibility, UAC needs to be turned off too.

---

### Post by Nick_Jinn on 2010-05-30
How should you mount the NTFS shared partition? As what?

---

### Post by CharlesA on 2010-05-30
> **Nick_Jinn said:**
> How should you mount the NTFS shared partition? As what?

```
sudo mount -t NTFS /dev/sdxx /mountpoint
```

??

---

### Post by Nick_Jinn on 2010-05-30
I mean from inside the Ubuntu partitioner.

Or alternately, as I am doing a custom install of windows.

---

