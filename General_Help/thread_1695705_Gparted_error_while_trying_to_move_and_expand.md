---
title: "Gparted error while trying to move and expand"
date: 2011-02-26
forum: General Help
---

### Post by eidasadie on 2011-02-26
Yes an infamous gparted error. Here are the details from the error

Basically just moved data from /dev/sdc1 to /dev/sdc2 then deleted sdc1 and tried to move and expand sdc2 and got this error.  Thanks for any help in advance

GParted 0.3.8
   Libparted 1.8.9

   Move /dev/sdc2 to the left and grow it from 812.27 GiB to 1.82
   TiB  00:26:00    ( ERROR )

        calibrate /dev/sdc2  00:00:00    ( SUCCESS )

             path: /dev/sdc2
             start: 2203562048
             end: 3907024064
             size: 1703462017 (812.27 GiB)

        check filesystem on /dev/sdc2 for errors and (if possible) fix
        them  00:26:00    ( SUCCESS )

             e2fsck -f -y -v /dev/sdc2

                  Pass 1: Checking inodes, blocks, and sizes
                  Pass 2: Checking directory structure 
                  Pass 3: Checking directory connectivity
                  Pass 4: Checking reference counts
                  Pass 5: Checking group summary information
                  262801 inodes used (0.49%)
                  3113 non-contiguous inodes (1.2%)
                  # of inodes with ind/dind/tind blocks: 64260/12145/9
                  120115140 blocks used (56.41%)
                  0 bad blocks
                  18 large files
                  215657 regular files
                  47039 directories
                  0 character device files
                  0 block device files
                  0 fifos
                  0 links
                  96 symbolic links (57 fast symbolic links)
                  0 sockets
                  --------
                  262792 files

                  e2fsck 1.41.3 (12-Oct-2008)

        move partition to the left  00:00:00    ( ERROR )

             old start: 2203562048
             old end: 3907024064
             old size: 1703462017 (812.27 GiB)

        libparted messages    ( INFO )

             Unable to satisfy all constraints on the partition.

             Can`t have the end before the start!

   ========================================

---

### Post by eidasadie on 2011-02-26
Solved  I was attempting to make changes in gparted without rounding to cylinders.   Once I turned the round to cylinders option back on I was able to make the changes.

---

