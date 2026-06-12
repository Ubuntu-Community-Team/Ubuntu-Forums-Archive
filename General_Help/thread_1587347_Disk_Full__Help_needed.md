---
title: "Disk Full || Help needed"
date: 2010-10-03
forum: General Help
---

### Post by banditti on 2010-10-03
I show my disk as being full.  I don't know where though.  It happened when one of my NFS mounts went offline.  When it came back up, my local disk was at 100%

10.04 64bit server, no GUI


root@FlexBack:~# df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/FlexBack-root
              ext4     14G   14G     0 100% /
none      devtmpfs   1001M  172K 1000M   1% /dev
none         tmpfs   1005M     0 1005M   0% /dev/shm
none         tmpfs   1005M   56K 1005M   1% /var/run
none         tmpfs   1005M     0 1005M   0% /var/lock
none         tmpfs   1005M     0 1005M   0% /lib/init/rw
/dev/sda1     ext2    228M   36M  181M  17% /boot
192.168.100.71:/vol/ssb
               nfs    800G  736G   65G  92% /home
192.168.100.73:/mnt/flexstor/flexvol1/of01_nfs01/
               nfs    2.2T  3.8G  2.2T   1% /mnt/of01

Thank you in advance!

---

### Post by aphatak on 2010-10-03
The response to your df command shows -
      */dev/mapper/FlexBack-root    ext4 14G 14G 0 100% /*

Could you possibly boot up with a live CD and check what the dev/mapper/FlexBack-root contains?

---

### Post by banditti on 2010-10-03
That would be hard, it is a production system.

---

### Post by drs305 on 2010-10-03
If you had another partition unmounted and performed a backup that would normally go to that device the backup may have ended up in the / mountpoint.  The the contents of the mountpoint contents with the external unmounted.

You can also take a look at this thread for analysis tips:
[HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

---

