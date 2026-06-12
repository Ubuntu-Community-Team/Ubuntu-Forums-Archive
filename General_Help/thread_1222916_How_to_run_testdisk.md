---
title: "How to run testdisk"
date: 2009-07-25
forum: General Help
---

### Post by mooksh on 2009-07-25
I have installed using command 'sudo apt-get install testdisk' it was installed successfully.But I couldn't find the program anywhere to execute the program. I am using Ubuntu 9.04,updated.Kindly suggest what to do to run the program.

Thanks in advance.

---

### Post by Bigtime_Scrub on 2009-07-25
Try opening up a terminal and type "testdisk" in it and hit enter. See if that runs the program. I am not sure but I think it has no GUI and is a terminal only program.

---

### Post by mooksh on 2009-07-26
Thanks dude!! :idea:

---

### Post by Wazz72 on 2012-05-29
I ran testdisk on the drive and it seems to have found some of the drive info, would I be able to recover the array using any of the following info:

Disk /dev/md0 - 3000 GB / 2794 GiB - CHS 732571872 2 4

     Partition                  Start        End    Size in sectors

  ext4                     0   0  1 732571871   1  4 5860574976 [STORAGE]
superblock 0, blocksize=4096 [STORAGE]
superblock 32768, blocksize=4096 [STORAGE]
superblock 98304, blocksize=4096 [STORAGE]
superblock 163840, blocksize=4096 [STORAGE]
superblock 229376, blocksize=4096 [STORAGE]
superblock 294912, blocksize=4096 [STORAGE]
superblock 819200, blocksize=4096 [STORAGE]
superblock 884736, blocksize=4096 [STORAGE]
superblock 1605632, blocksize=4096 [STORAGE]
superblock 2654208, blocksize=4096 [STORAGE]

To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device

---

### Post by nothingspecial on 2012-05-29
Rather than bumping a 3 year old thread to the top, please start a new one.

Closed.

---

