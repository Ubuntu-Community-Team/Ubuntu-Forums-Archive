---
title: "Mounting with tmpfs"
date: 2010-01-30
forum: General Help
---

### Post by dethredic on 2010-01-30
I am doing: 

sudo mount -t tmpfs -o size=850M,nr_inodes=10k,mode=0777 tmpfs '/home/phil/test/'

When checking the available space of the folder it says 850mb, but when I copy a movie there, my ram usage doesn't budge.

I also tried this:
sudo mount -t tmpfs -o nr_inodes=10k,mode=0777 tmpfs '/home/phil/test/'

I have a feeling that the files are just going to swap, but I want to mount them to only ram. What am I doing wrong?

---

### Post by john newbuntu on 2010-01-30
Create a ram device.  Something like this ought to do it:
   # dd if=/dev/zero of=/dev/ram0 count=850000 bs=1024
   # mke2fs /dev/ram0
   # mkdir ~/mnt
   # mount /dev/ram0 ~/mnt
Tweak the count and bs parameters.

---

### Post by dethredic on 2010-01-30
> **john newbuntu said:**
> Create a ram device.  Something like this ought to do it:
   # dd if=/dev/zero of=/dev/ram0 count=850000 bs=1024
   # mke2fs /dev/ram0
   # mkdir ~/mnt
   # mount /dev/ram0 ~/mnt
Tweak the count and bs parameters.

I need to mount it in a specific location though.

---

### Post by john newbuntu on 2010-01-30
Well, as I understand it, ramdisk/ramfs uses the ram, although tmpfs might use swap on some implementations.  You may want to just check this on your system using the "df -Th" and the "free" commands.  Since you mentioned RAM not budging, try using ramfs instead.

---

### Post by dethredic on 2010-01-30
Alright, here is what I tried:

[phil@fml ~]$ sudo mount -t ramfs -o size=850M,nr_inodes=10k,mode=0777 ramfs '/home/phil/test/'
[phil@fml ~]$ cp ~/videos/american.pie.book.of.love.avi ~/test/
[phil@fml ~]$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4     12G  8.5G  2.5G  78% /
none         tmpfs   1013M  244K 1013M   1% /dev
none         tmpfs   1013M     0 1013M   0% /dev/shm
/dev/sda3     ext4    564G  193G  343G  37% /home
/dev/sda1     ext4     99M   26M   68M  28% /boot
tmpfs        tmpfs   1013M   20K 1013M   1% /tmp

hrmmm....

[phil@fml ~]$ sudo mount -t tmpfs -o size=850M,nr_inodes=10k,mode=0777 tmpfs '/home/phil/test/'
[phil@fml ~]$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4     12G  8.5G  2.5G  78% /
none         tmpfs   1013M  244K 1013M   1% /dev
none         tmpfs   1013M     0 1013M   0% /dev/shm
/dev/sda3     ext4    564G  194G  342G  37% /home
/dev/sda1     ext4     99M   26M   68M  28% /boot
tmpfs        tmpfs   1013M   20K 1013M   1% /tmp
tmpfs        tmpfs    850M     0  850M   0% /home/phil/test
[phil@fml ~]$ cp LYTS09.part* ~/test
[phil@fml ~]$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext4     12G  8.5G  2.5G  78% /
none         tmpfs   1013M  244K 1013M   1% /dev
none         tmpfs   1013M     0 1013M   0% /dev/shm
/dev/sda3     ext4    564G  194G  342G  37% /home
/dev/sda1     ext4     99M   26M   68M  28% /boot
tmpfs        tmpfs   1013M   20K 1013M   1% /tmp
tmpfs        tmpfs    850M  720M  131M  85% /home/phil/test
[phil@fml ~]$ 

still the ram usage didn't go up so it must be using my swap

---

### Post by john newbuntu on 2010-01-31
The line:
tmpfs        tmpfs    850M  720M  131M  85% /home/phil/test
says you have used up 85% of your tmpfs file system.  If you had run the "free" command before and after the copy, we could have seen where the content was written to (ram or swap).

---

### Post by dethredic on 2010-01-31
> **john newbuntu said:**
> The line:
tmpfs        tmpfs    850M  720M  131M  85% /home/phil/test
says you have used up 85% of your tmpfs file system.  If you had run the "free" command before and after the copy, we could have seen where the content was written to (ram or swap).

Ok, it actually does look like it is going to ram (my conky script just must not measure tmpfs mounts):

[phil@fml ~]$ sudo mount -t tmpfs -o size=850M,nr_inodes=10k,mode=0777 tmpfs '/home/phil/test/
[phil@fml ~]$ cp -R ~/music/Red\ Hot\ Chili\ Peppers/ ~/test/
[phil@fml ~]$ cp -R ~/music/Red\ Hot\ Chili\ Peppers/ ~/test/test
[phil@fml ~]$ cp -R ~/music/Red\ Hot\ Chili\ Peppers/ ~/test/test2
[phil@fml ~]$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb2     ext4     12G  8.5G  2.5G  78% /
none         tmpfs   1013M  244K 1013M   1% /dev
none         tmpfs   1013M     0 1013M   0% /dev/shm
/dev/sdb3     ext4    564G  196G  340G  37% /home
/dev/sdb1     ext4     99M   26M   68M  28% /boot
tmpfs        tmpfs   1013M   16K 1013M   1% /tmp
tmpfs        tmpfs    850M  824M   27M  97% /home/phil/test
[phil@fml ~]$ free -om
             total       used       free     shared    buffers     cached
Mem:          2024       1974         50          0         12       1727
Swap:         6000          0       6000
[phil@fml ~]$ rm -R  ~/test/*
[phil@fml ~]$ sudo umount /home/phil/test/
[phil@fml ~]$ free -om
             total       used       free     shared    buffers     cached
Mem:          2024       1379        645          0         14       1132
Swap:         6000          0       6000


So my conky script must just not update the ram usage on tmpfs mounts. Also it doesn't look like I got all my ram back. I was just hoping for more of a performance increase, but ohh well.

edit: after a semi fresh boot here is my ram usage:
[phil@fml ~]$ free -om
             total       used       free     shared    buffers     cached
Mem:          2024        818       1206          0         57        495
Swap:         6000          0       6000

---

