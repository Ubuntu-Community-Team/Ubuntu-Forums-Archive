---
title: "Is my drive formatted in NTFS or ext4?"
date: 2009-09-19
forum: General Help
---

### Post by odinb on 2009-09-19
Weird question, I know, but have a look at this:

sudo fdisk -l gives:
Disk /dev/sdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074bc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       24792   199141708+  83  Linux


So, it is linux, but then blkid gives:

/dev/sdf1: UUID="36CB5E597E8AECA0" LABEL="Data1" TYPE="ntfs"

and finally starting gparted, it says it is ext4.

Have reformatted several times using gparted, and gparted clearly states it is ext4.

So what is my drive? NTFS or ext4?

I want it to be ext4...

---

### Post by oboedad55 on 2009-09-20
> **odinb said:**
> Weird question, I know, but have a look at this:

sudo fdisk -l gives:
Disk /dev/sdf: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074bc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       24792   199141708+  83  Linux


So, it is linux, but then blkid gives:

/dev/sdf1: UUID="36CB5E597E8AECA0" LABEL="Data1" TYPE="ntfs"

and finally starting gparted, it says it is ext4.

Have reformatted several times using gparted, and gparted clearly states it is ext4.

So what is my drive? NTFS or ext4?

I want it to be ext4...

Uh... very weird. I just ran those commands on my system and don't get anything weird like that. You're sure that you're formatting to ext4? I'm sure you are, still...

---

### Post by renkinjutsu on 2009-09-20
i think ubuntu has NTFS read compiled as a module and not part of the kernel, so i don't think you'd be able to boot at all if your partition were NTFS

also, you can check your /etc/fstab file and see what it mounts as
or type 'mount' into the terminal

i guess you can also read the messages displayed by GRUB before the linux kernel loads.. mine says something along the lines of 'hd(0,4) ext4 .. blah blah blahhh'
it just flashes on and off the screen though, so read fast when you reboot

---

### Post by odinb on 2009-09-20
Had this drive as an extra drive in my system using ext4. Borrowed it temporarily in another machine, and had Win 7 RTM installed and booting from it. Then I used gparted to delete the NTFS/Win 7 partition, and re-created it as ext4 before moving it back.

After moving it back, it would not mount with my old FSTAB using the old UUID. This was when I hit a blkid to get the new UUID, and was stunned when it was declare as NTFS.

Have deleted and re-created the partition in ext 4 on both machines several times, and even installed Ubuntu on it on the other machine.

Funny thing is that when I had Ubuntu installed on it, it came up as ext4 with blkid, but then I used gparted to get rid of all the files and the bootflag, and now it comes up as NTFS again!

A funny feeling I have is that the Win 7 install somehow messed up the disk info!?!?

In fstab I used to mount it using UUID, now I had to mount it like this:
# sdf1 
# old UUID=e23f961a-af9e-4fbb-941e-49e37bacb50e	/media/Data1	ext4	defaults				0	3
/dev/sdf1					/media/Data1	ext4	defaults				0	3

---

### Post by odinb on 2009-09-20
Also, checked the syslog, and it looks like it mounts it as ext4:

Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.632599] EXT4-fs: barriers enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645104] kjournald2 starting.  Commit interval 5 seconds
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645335] EXT4 FS on sdf1, internal journal on sdf1:8
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645337] EXT4-fs: delayed allocation enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645338] EXT4-fs: file extents enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.654561] EXT4-fs: mballoc enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.654564] EXT4-fs: mounted filesystem with ordered data mode.
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.689925] EXT4-fs: barriers enabled


So why is blkid still declaring it as TYPE="ntfs" as opposed to ext4?

---

### Post by oboedad55 on 2009-09-20
> **odinb said:**
> Also, checked the syslog, and it looks like it mounts it as ext4:

Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.632599] EXT4-fs: barriers enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645104] kjournald2 starting.  Commit interval 5 seconds
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645335] EXT4 FS on sdf1, internal journal on sdf1:8
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645337] EXT4-fs: delayed allocation enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.645338] EXT4-fs: file extents enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.654561] EXT4-fs: mballoc enabled
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.654564] EXT4-fs: mounted filesystem with ordered data mode.
Sep 19 22:14:27 GA-EP45-UD3R kernel: [   19.689925] EXT4-fs: barriers enabled


So why is blkid still declaring it as TYPE="ntfs" as opposed to ext4?

There's a program out there called "dban". It's a bootable disk that will let you completely wipe out a hard disk. Here it is:
[http://www.dban.org/](http://www.dban.org/)

---

### Post by odinb on 2009-09-20
Will try it and report back....thanks!

---

