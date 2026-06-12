---
title: "Help with ubuntu log entries ??"
date: 2010-06-04
forum: General Help
---

### Post by burtonrhodes on 2010-06-04
I have logcheck running on my Ubuntu Server (64-bit) and can't figure out what this means.  Can anyone shed some light on this?
 
```

Jun 4 06:50:18 aframeonline kernel: [502612.581741] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Jun 4 06:50:18 aframeonline kernel: [502612.585555] SGI XFS Quota Management subsystem
Jun 4 06:50:18 aframeonline kernel: [502612.598903] JFS: nTxBlock = 8192, nTxLock = 65536
Jun 4 06:50:18 aframeonline kernel: [502612.638283] NTFS driver 2.1.29 [Flags: R/O MODULE].
Jun 4 06:50:18 aframeonline kernel: [502612.673923] QNX4 filesystem 0.2.3 registered.
Jun 4 06:50:19 aframeonline kernel: [502612.731134] Btrfs loaded
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda2
Jun 4 06:50:19 aframeonline 10freedos: debug: /dev/sda2 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda2
Jun 4 06:50:19 aframeonline 10qnx: debug: /dev/sda2 is not a QNX4 partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda2
Jun 4 06:50:19 aframeonline macosx-prober: debug: /dev/sda2 is not an HFS+ partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda2
Jun 4 06:50:19 aframeonline 20microsoft: debug: /dev/sda2 is not a MS partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda2
Jun 4 06:50:19 aframeonline 30utility: debug: /dev/sda2 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda2
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda2
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda2
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda2
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda2
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Jun 4 06:50:19 aframeonline 50mounted-tests: debug: /dev/sda3 is a swap partition; skipping
Jun 4 06:50:19 aframeonline os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda4
Jun 4 06:50:19 aframeonline 50mounted-tests: debug: /dev/sda4 type not recognised; skipping
Jun 4 06:50:19 aframeonline os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda5
Jun 4 06:50:19 aframeonline 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda5
Jun 4 06:50:19 aframeonline 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda5
Jun 4 06:50:19 aframeonline macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda5
Jun 4 06:50:19 aframeonline 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda5
Jun 4 06:50:19 aframeonline 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda6
Jun 4 06:50:19 aframeonline 10freedos: debug: /dev/sda6 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda6
Jun 4 06:50:19 aframeonline 10qnx: debug: /dev/sda6 is not a QNX4 partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda6
Jun 4 06:50:19 aframeonline macosx-prober: debug: /dev/sda6 is not an HFS+ partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda6
Jun 4 06:50:19 aframeonline 20microsoft: debug: /dev/sda6 is not a MS partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda6
Jun 4 06:50:19 aframeonline 30utility: debug: /dev/sda6 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda6
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda6
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda6
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda6
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda6
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline 20microsoft: debug: /dev/sdb1 is not a MS partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline 30utility: debug: /dev/sdb1 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sdb2
Jun 4 06:50:19 aframeonline 50mounted-tests: debug: /dev/sdb2 type not recognised; skipping
Jun 4 06:50:19 aframeonline os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline 10freedos: debug: /dev/sdb5 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline 10qnx: debug: /dev/sdb5 is not a QNX4 partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline macosx-prober: debug: /dev/sdb5 is not an HFS+ partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline 20microsoft: debug: /dev/sdb5 is not a MS partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline 30utility: debug: /dev/sdb5 is not a FAT partition: exiting
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb5
Jun 4 06:50:19 aframeonline os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb5

```

---

### Post by john newbuntu on 2010-06-04
Did you happen to run "sudo update-grub" or perhaps update your kernel?  This would have triggered the /etc/grub.d/30_os-prober script of grub2 to run, which in turn would have run the os-prober command.  The command checks for the existence of other operating systems on the various partitions on your disks.

---

### Post by dino99 on 2010-06-04
its saying that grub has been updated, maybe you need to read and learn a little, see links below

---

