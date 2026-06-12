---
title: "Force mounting on a failed ubuntu drive, help please?"
date: 2010-07-12
forum: General Help
---

### Post by ztoundas on 2010-07-12
Ok so i was trying to install a second version of Ubuntu i think, its been a while since it originally failed so i forget exactly what caused it, but now when i try to boot, the bootloader fails.

I am useing a live usb to try to recover my data before i do a complete reformat, but it wont let me mount the drive

it gives the following error:

  "Unable to mount volume"
  "mount: wrong fs type, bad option, bad superblock on /dev/sda5,     missing codepage or helper program, or other error     In some cases useful info is found in syslog - try    dmesg | tail or so"

And when I try to re-size the partition to install a new version of Ubuntu next to it, it gives this error:

[SIZE=2]check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR ) [/SIZE]            [SIZE=2]***e2fsck -f -y -v /dev/sda5***[/SIZE]             [SIZE=2][I]The filesystem size (according to the superblock) is 29216194 blocks
The physical size of the device is 26775296 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes[/I][/SIZE]
How should I go about recovering my data?

All help is immensely appreciated guys! thanks!

---

### Post by ztoundas on 2010-07-12
Still doing research, found a possible way to fix it via a filesystem check thanks to some info found [here]("http://members.iinet.net.au/%7Eherman546/p10.html#filesystem_check_on_an_ext3_filesystem"). But its now giving me an option that, according to the site, I should attempt to backup before I attempt, and I really cant lose some of the data on the drive

"jolicloud@jolicloud:~$ sudo e2fsck -C0 -p -f -v /dev/sda5
/dev/sda5: The filesystem size (according to the superblock) is 29216194 blocks
The physical size of the device is 26775296 blocks
Either the superblock or the partition table is likely to be corrupt!


./dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

jolicloud@jolicloud:~$ sudo e2fsck -C0 -f -v /dev/sda5
e2fsck 1.41.4 (27-Jan-2009)
The filesystem size (according to the superblock) is 29216194 blocks
The physical size of the device is 26775296 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? "

  I think I need to Force mount it, how do I do this properly?

---

