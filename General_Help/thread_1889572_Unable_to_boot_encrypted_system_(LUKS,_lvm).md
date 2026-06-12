---
title: "Unable to boot encrypted system (LUKS, lvm)"
date: 2011-12-01
forum: General Help
---

### Post by #stanislaw on 2011-12-01
Hello,

i closed my laptop and it went into sleeping mode. After i opened it up it asks for the luks password. i entered it an a massage occured:

```

    Reading all physical volumes. This may take a while...
    Found volume group "ubuntu" using metadata type lvm2 
    3 logical volume(s) in volume group "ubuntu" now active  
cryptsetup: unknown fstype, bad password or options? 
Device lvm_crypt is busy. 
Device lvm_crypt already exists.

```I entered the password two more times and it says:
```
Device lvm_crypt already exists.
```I ended up in initramfs.

in /dev/mapper/ i see the volumes ubuntu-swap, ubuntu-root and ubuntu-home

i can mount the volumes manually and the data is there (which indicates that the password is correct).

how can i get ubuntu back booting again?

My system runs Ubuntu 11.10, 64 bit with kernel 3.0.0.-13-generic

thanx

---

### Post by #stanislaw on 2011-12-02
Ok, here is an update.

if i press enter 3 times when the luks password field appears and then enter the password it says:

```
lvm_crypt set up successfull.
```

 the system tries to boot but new error messages appear on the screen:

```

...
Begin: Running /scripts/local-premount ... done
mount: mounting /dev/mapper/ubuntu-root on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ... done.
done.
mount: mounting /dev on /root/dev failed: No such file or directory
done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn have requested /sbin/init.
No init found. Try passing init=bootarg.

```

i ended up in initramfs again.

Please help me im stuck.

---

### Post by Herman on 2011-12-02
I know you said you can mount the file system and 'see' all your files, but generally in a situation like that a file system check won't do any harm, (other than possibly wasting a few minutes of your time), and if you're lucky it might even solve your problem.

I can help you with that if needed.

---

### Post by #stanislaw on 2011-12-02
Ok sounds good, do i need a live system or can i do a file system check with initramfs directly? i booted the ubuntu live system from a usb stick and was able to encrypt the disk with my password but i was not able to mount it, it says unknown filesystem type. An option to check the disk was not available.

---

### Post by Herman on 2011-12-02
It's shut down of course, not just hibernating or suspended. You use of the word 'boot' leads me to think you did shut it down completely since your problem began.

I don't know how to run a file system check with initramfs, that's too advanced for me.

If you haven't already done so you probably need to install lvm2 and cryptsetup and run sudo modprobe dm-crypt in your auxilliary Ubuntu installation before you'll be able to use for rescuing your laptop's LUKS Encrypted install,
```
sudo apt-get install lvm2 cryptsetup
``````
sudo modprobe dm-crypt
```

---

### Post by Herman on 2011-12-02
This command is for taking a look around and reporting back to you what logical volumes might be in your computer or in disks plugged in to your computer.
It will probably tell you it couldn't find your volume group but it will still tell you the name and uuid of it, so it did find it, but it will still say it didn't.
```
sudo lvdisplay
```Remember the <volume-name>, we'll need it again later on.

Decrypt the partition at the command line, for example: 
```
sudo cryptsetup luksOpen /dev/sdd1 crypt1
```Where: your partition editor shows you that your LVM partition begins in /dev/sdd1. 

Run e2fsck on the unlocked volume: 
```
sudo e2fsck -C0 -p -f -v /dev/mapper/amd64--ubuntu-root

```Where: the unlocked volume is now /dev/mapper/<volume-name>
and <volume name> = amd64--ubuntu-root

Optionally, you may also want to run,
```
sudo resize2fs -p /dev/mapper/amd64--ubuntu-root 
```

---

### Post by Herman on 2011-12-02
I was just running through those commands again myself to check and make  sure they still work the same. I'm reading them from old notes I saved.
About the  <volume-name>,
> herman@amd-quad-lynx:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/[COLOR=Red]**usb-crypt-lynx/root**[/COLOR]
  VG Name                usb-crypt-lynx
I'm not sure if there have been some software changes since last time, but the LV Name from the lvdisplay output '[COLOR=Red]**usb-crypt-lynx/root **[/COLOR]'becomes : **usb--crypt--lynx-root** and can also be found by using tab completion if you prefer.

---

### Post by #stanislaw on 2011-12-02
Hmm... i just closed the laptop, normaly it went into a suspend mode. i havent changed the powermanagement so it should be the default configuration.

ok i have done this:

```
sudo apt-get install lvm2 cryptsetup
```and that

```
sudo modprobe dm-crypt
```no problems so far. but

```
sudo lvdisplay
```displays nothing.

The disk utility displays my drive as /dev/sda and the encrypted part as /dev/sda2 the boot part as /dev/sda1

than i did this
```
sudo cryptsetup luksOpen /dev/sda2 crypt1
```and some magic happens. my live ubuntu mounts my home from my disk automatically and it appears in the menu in "Places". All data is there. Looks good. 

```

df -hT
...
/dev/mapper/ubuntu-home ext4 277G 260G 3,1G 99% /media/8f49c242-d686-4a22-8391-0ece103c83e

```Now i want to do the file system check
```

sudo e2fsck -C0 -p -f -v /dev/mapper/ubuntu-root
e2fsck: Bad magic number in super-block while trying to open /dev/mapper/ubuntu-root
/dev/mapper/ubuntu-root:
SuperBlock is unreadable, no valid ext2 fileystem.
If it is a valid and an ext2 filesystem than the SuperBlock is broken. Try another Superblock

```(I translated the message from german to english)


Oh one last thing in "Places" there is an Entry for /dev/sda1 where glub lives, this volume can be mounted too without errors and the data looks godd too.

---

### Post by #stanislaw on 2011-12-02
Hmm... dont know what happend but

```
sudo lvdisplay
```no gives correct output.

```

  --- Logical volume ---
  LV Name                /dev/ubuntu/swap
  VG Name                ubuntu
  LV UUID                2NXRHC-38e1-fzc3-VS3j-xDy0-orxN-dQgimx
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                5,08 GiB
  Current LE             1300
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/ubuntu/root
  VG Name                ubuntu
  LV UUID                Sdb0Ac-LA84-cfxK-VDxR-5SUJ-UrSO-3KwHg3
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                12,00 GiB
  Current LE             3072
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

   --- Logical volume ---
  LV Name                /dev/ubuntu/home
  VG Name                ubuntu
  LV UUID                Ufeuad-XKLm-V5PR-IeOo-WWWk-4C0C-q7h8f9
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                280,81 GiB
  Current LE             71887
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   


```

---

### Post by Herman on 2011-12-02
Try just typing the first part of the command,
```
sudo e2fsck -C0 -p -f -v /dev/mapper/
```and press your TAB key twice, it should give you a list including the proper volume name that you need to complete the command.

For example, mine looks like this,
```
herman@amd-quad-lynx:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/
control                                                        udisks-luks-uuid-4dab2336-4026-4752-b049-b66bf7f6d9fd-uid1000
crypt1                                                        ** usb--crypt--lynx-root**
udisks-luks-uuid-420e7b00-ec55-4276-90ab-f5352fca2bfd-uid1000  usb--crypt--lynx-swap_1

```
So I typed:
```
herman@amd-quad-lynx:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/usb--crypt--lynx-root
```and that worked for me,
```
herman@amd-quad-lynx:~$ sudo e2fsck -C0 -p -f -v /dev/mapper/usb--crypt--lynx-root
                                                                               
  230713 inodes used (25.07%)
     247 non-contiguous files (0.1%)
     361 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 201243/104
 1633746 blocks used (44.45%)
       0 bad blocks
       1 large file

  165068 regular files
   28615 directories
      59 character device files
      26 block device files
       0 fifos
     538 links
   36930 symbolic links (29265 fast symbolic links)
       6 sockets
--------
  231242 files
```I'm not really still running Lucid Lynx, it's upgraded to Oneric but it still has the same operating system name.

---

### Post by #stanislaw on 2011-12-02
i tried

```

sudo e2fsck -C0 -p -f -v /dev/mapper/ubuntu-root

```

but again it says "bad superblock" so i tried another superblock

```

mke2fs -n /dev/mapper/ubuntu-root

```

gives me
```

Dateisystem-Label=
OS-Typ: Linux
Blockgröße=4096 (log=2)
Fragmentgröße=4096 (log=2)
Stride=0 Blöcke, Stripebreite=0 Blöcke
786432 Inodes, 3145728 Blöcke
157286 Blöcke (5.00%) reserviert für den Superuser
Erster Datenblock=0
Maximale Dateisystem-Blöcke=3221225472
96 Blockgruppen
32768 Blöcke pro Gruppe, 32768 Fragmente pro Gruppe
8192 Inodes pro Gruppe
Superblock-Sicherungskopien gespeichert in den Blöcken: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208

```

and then i tried:
```

sudo e2fsck -b 32768 -C0 -p -f -v /dev/mapper/ubuntu-root

```

the output is
```

/dev/mapper/ubuntu-root: ext3 Recovery-Flag sauber, aber das Journal enthält Daten.
/dev/mapper/ubuntu-root: Recovery-Kennzeichen in Backup SuperBlock nicht gesetzt, Journal wird trotzdem gestartet.
/dev/mapper/ubuntu-root: stelle das Journal wieder her
Lesefehler - Block 1624278 (Attempt to read block from filesystem resulted in short read). 

/dev/mapper/ubuntu-root: UNERWARTETE INKONSISTENZ; fsck MANUELL AUSFÜHREN
    (d.h. ohne -a oder -p Option)

```
so i tried it without "-p"
```

sudo e2fsck -b 32768 -C0 -f -v /dev/mapper/ubuntu-root 
e2fsck 1.41.12 (17-May-2010)
ext3 Recovery-Flag sauber, aber das Journal enthält Daten.
Recovery-Kennzeichen in Backup SuperBlock nicht gesetzt, Journal wird trotzdem gestartet.
/dev/mapper/ubuntu-root: stelle das Journal wieder her
Lesefehler - Block 1624278 (Attempt to read block from filesystem resulted in short read). Ignoriere Fehler<j>?

```

i can try to translate the messages in engish if needed. Basically it says Read error on block 1624278 and asks me if i want to ignore the error or not.

---

### Post by #stanislaw on 2011-12-02
Ok, i found out that the real devices are located under /dev/dm-1, /dev/dm-2 and /dev/dm-3

```

 ls -al /dev/ubuntu/
total 0
drwxr-xr-x  2 root root  100 2011-12-02 09:47 .
drwxr-xr-x 20 root root 3620 2011-12-02 09:46 ..
lrwxrwxrwx  1 root root    7 2011-12-02 09:47 home -> ../dm-3
lrwxrwxrwx  1 root root    7 2011-12-02 11:59 root -> ../dm-2
lrwxrwxrwx  1 root root    7 2011-12-02 11:30 swap -> ../dm-1
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/dm-2
/dev/dm-2: stelle das Journal wieder her
/dev/dm-2: Bereinige verwaist Inode 131679 (uid=1000, gid=1000, mode=0100600, size=2048)
/dev/dm-2: Bereinige verwaist Inode 131334 (uid=1000, gid=1000, mode=0100600, size=1544)
/dev/dm-2: Bereinige verwaist Inode 273 (uid=119, gid=131, mode=0100600, size=0)
/dev/dm-2: Bereinige verwaist Inode 83 (uid=119, gid=131, mode=0100600, size=0)
/dev/dm-2: Bereinige verwaist Inode 79 (uid=119, gid=131, mode=0100600, size=0)
/dev/dm-2: Bereinige verwaist Inode 68 (uid=119, gid=131, mode=0100600, size=0)
/dev/dm-2: Bereinige verwaist Inode 66 (uid=119, gid=131, mode=0100600, size=0)
                                                                               
  431058 inodes used (54.81%)
     592 non-contiguous files (0.1%)
     794 non-contiguous directories (0.2%)
         # von Inodes mit ind/dind/tind Blöcken: 0/0/0
         Erweiterungstiefe Histogramm: 383753/294
 2136365 blocks used (67.91%)
       0 bad blocks
       1 large file

  305270 regular files
   53492 directories
      57 character device files
      25 block device files
       0 fifos
     169 links
   72193 symbolic links (46907 fast symbolic links)
      12 sockets
--------
  431218 files

```

Now my ubuntu live has mounted the root partition automaticaly, the data is there and is looking good. I will try to boot from disk.

---

### Post by #stanislaw on 2011-12-02
Yes it works! thanks for your help! im not so familiar with lvm and stuff because it just  worked. Plus I didnt know how to do a filesystem check on an encrypted hard drive. Now i know :)

---

### Post by Herman on 2011-12-02
:) Very good! I'm happy you were successful! Well done!   :)

---

