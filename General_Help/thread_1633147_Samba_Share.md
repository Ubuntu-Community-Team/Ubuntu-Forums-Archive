---
title: "Samba Share"
date: 2010-11-28
forum: General Help
---

### Post by soulstealer1984 on 2010-11-28
I have just installed Ubuntu desktop and I am using this pc as a file server.  I have already installed Samba and have it operational and viewable by my windows computers.  Now the problem is that I have 2 hard drives and the way that I have Samba set up it is sharing my home directory which is wonderful but my windows computers do not have access to the second hard drive.  I search for several hours this morning trying to figure out how to do this but cannot figure it out.   Any suggestions would be greatly appreciated.

As a side note i am very new to Ubuntu so please make your suggestions Noob friendly.

---

### Post by CharlesA on 2010-11-28
You would have to mount the second drive somewhere and create a share in smb.conf to point to it.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

[https://help.ubuntu.com/community/Samba/SambaServerGuide#File%20Sharing%20%28Basics%29](https://help.ubuntu.com/community/Samba/SambaServerGuide#File%20Sharing%20%28Basics%29)

---

### Post by soulstealer1984 on 2010-12-01
Ok i am having a little trouble with the mounting process.  I am running 2 SCSI hard drives.  Both drives are visible under computer, does this mean it is mounted?  If it not mounted how to i find out what the drive code is to mount it.  I ran the mount command and got the following
  

megaplex@megaplex-ProLiant-DL380-G3:~$ mount
/dev/cciss/c0d1p1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/megaplex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=megaplex)

from what i was reading running the mount command should tell me what drives are already mounted.  But this output does not make any sense to me.  Not sure where to go from here any help would be much appreciated.  Thanx in advance

---

### Post by VCoolio on 2010-12-01
Your 'mount' output (which indeed shows already mounted devices only) suggests the second disk hasn't been mounted yet. The fact that it shows up in the 'places' menu suggests there is a line for it in fstab, but I'm not sure about that. But it needs a line in that file: /etc/fstab. Do 'sudo fdisk -l' or 'sudo blkid' to find out where in /dev your harddisk is (or use gparted to make a label for it and use LABEL=whatever to identify your second disk). Then create a line for your disk in /etc/fstab (fstab howto [here](http://ubuntuforums.org/showthread.php?t=283131)). Make sure it is mounted automatically. Then share it using nautilus (your file manager); just right click the folder in /media where it is mounted to and share it (that requires the package nautilus-share to be installed).

---

### Post by soulstealer1984 on 2010-12-01
ok giving that a try

---

### Post by soulstealer1984 on 2010-12-01
Im still working on what you have told me to do i think i am making progress.  But i had one quick question and that was will nautilus actually share files with a windows computer or is something only Samba can do?

---

### Post by CharlesA on 2010-12-01
They are two different ways of sharing and conflict with each other.

You can use either, but not a mix of the two.

---

### Post by peyre on 2010-12-01
Nautilus can definitely share files and folders with Windows machines.  I'm doing that at home myself.  But, you have to install nautilus-share in Synaptic, then reboot.  The first time you go to share a folder, you'll be prompted to install the Sharing service.  Go ahead and install it, and you should be good to go.

---

