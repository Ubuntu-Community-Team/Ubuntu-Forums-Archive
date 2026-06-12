---
title: "Recover files from encrypted home folder"
date: 2011-05-16
forum: General Help
---

### Post by Iqbal_ on 2011-05-16
Hi,
I upgraded from ubuntu 9.10 to 11.04. During installation (Natty) I chosen the option to encrypt the home folder. After a day the system crashed. It was showing that disk is having health problems. If I boot from live cd then i cant access the home folder. When I tried to mount the home folder, it says "Reading directory: input/output error"

Because I used Karmic without problem I reinstalled the Karmic, then I can mount the home folder, but cant access it as it was encrypted.

Now Karmic is installed. I tried to boot from Live CD of Natty and tried to mount /home folder, it says some super-block issues.

How to access the files in the home folder?

---

### Post by WthIteh on 2011-05-16
I hope it helps (replace /dev/sdax with your encrypted partition like /dev/sda3, etc.):
```

apt-get update
apt-get install hashalot lvm2
cryptsetup luksOpen /dev/sdax pvcrypt
mount /dev/mapper/pvcrypt /mnt

```
If it uses lvm over encrypted drive, then else of last line you should mount the lvm logical volume from mapper.

---

### Post by Megaptera on 2011-05-16
Is this any help?
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

It says "The utility will do a deep find of the system's hard disk, looking for folders named ".Private", and will interactively ask you if it's the folder you'd like to recover.  If you answer "yes", you will then be prompted for the login passphrase that's used to decrypt your wrapped, mount passphrase.  Assuming you have the correct credentials, it will mount your Encrypted Home or Private directory in read-only mode, and point you at the temporary directory where it's mounted."

---

### Post by Iqbal_ on 2011-05-20
Hi,

Following are the details of Live CD session of 11.04 (Natty):

My home folder (the encrypted home folder) is /dev/sda7. I was trying to mount this partition. I got Input/Output error. I could not mount this partition. I have 4 partitions as follows
1-/boot
2-/
3-/home
4-swap
In addition to above four partitions (500 GB HDD), there are three NTFS partitions also. Windows vista is installed on /dev/sda1.

When I used fdisk -l command it does not list any of the partitons. Earlier, fdisk -l used to list all partitions.  I used GParted it also did not show any partition.

I tied to copy /dev/sda7 to backup the image using dd command (dd if=/dev/sda7 /mnt/backup_sda7), it showed zero bytes copied. I was trying to save this file on external hard drive,mounted on /mnt.

I tried to run fsck -f /dev/sda7, it did not run. It was saying that there is some problem with super-block. I tried to restore super-block by using e2fsck -b block-number /dev/sda7 - no success. I got the error "Could this be a zero length partition.".
Following is the part of dmesg command output:

[    5.177670]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
[    5.178151] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.199054] [drm] Initialized drm 1.1.0 20060810
[    5.410044] usb 3-4: new full speed USB device using ohci_hcd and address 2
[ 3214.120048] ata1.00: device reported invalid CHS sector 0
[ 3214.120057] ata1.00: device reported invalid CHS sector 0
[ 3214.120064] ata1.00: device reported invalid CHS sector 0
[ 3214.120071] ata1.00: device reported invalid CHS sector 0
[ 3214.120093] ata1: EH complete
[ 3334.190215] end_request: I/O error, dev sda, sector 740997120
[ 3334.190220] Buffer I/O error on device sda7, logical block 28344320
[ 3334.190222] lost page write due to I/O error on sda7
[ 3334.190261] JBD2: I/O error detected when updating journal superblock for sda7-8.
[ 3334.190313] sd 0:0:0:0: [sda] Unhandled error code
[ 3334.190315] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3334.190319] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 2c 2a b8 08 00 00 08 00
[ 3334.190329] end_request: I/O error, dev sda, sector 740997128
[ 3334.190343] Aborting journal on device sda7-8.
[ 3334.190367] sd 0:0:0:0: [sda] Unhandled error code
[ 3334.190370] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3334.190375] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 2c 2a b8 00
[ 3334.190382] sd 0:0:0:0: [sda] READ CAPACITY(16) failed
[ 3334.190385] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3334.190389] sd 0:0:0:0: [sda] Sense not available.
[ 3334.190391]  00 00 08 00
[ 3334.190396] end_request: I/O error, dev sda, sector 740997120
[ 3334.190400] Buffer I/O error on device sda7, logical block 28344320
[ 3334.190402] lost page write due to I/O error on sda7
[ 3334.190419] JBD2: I/O error detected when updating journal superblock for sda7-8.
[ 3334.190435] sd 0:0:0:0: [sda] READ CAPACITY failed
[ 3334.190438] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 3334.190442] sd 0:0:0:0: [sda] Sense not available.
[ 3334.190515] sd 0:0:0:0: [sda] Got wrong page
[ 3334.190518] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 3334.190523] sda: detected capacity change from 500107862016 to 0
[ 3377.817723] EXT4-fs error (device sda7): ext4_journal_start_sb:260: Detected aborted journal
[ 3377.817730] EXT4-fs (sda7): Remounting filesystem read-only
[ 3377.817732] EXT4-fs (sda7): previous I/O error to superblock detected
[ 3523.476083] SQUASHFS error: squashfs_read_data failed to read block 0x957b0bd
[ 3523.476087] SQUASHFS error: Unable to read fragment cache entry [957b0bd]
[ 3523.476090] SQUASHFS error: Unable to read page, block 957b0bd, size 43ae
[ 3523.476249] SQUASHFS error: Unable to read fragment cache entry [957b0bd]
[ 3523.476251] SQUASHFS error: Unable to read page, block 957b0bd, size 43ae
[ 3523.476300] SQUASHFS error: Unable to read fragment cache entry [957b0bd]
[ 3523.476303] SQUASHFS error: Unable to read page, block 957b0bd, size 43ae
[ 3528.803912] sr 1:0:0:0: [sr0] Unhandled sense code
[ 3528.803917] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3528.803924] sr 1:0:0:0: [sr0]  Sense Key : Medium Error [current] 
[ 3528.803932] sr 1:0:0:0: [sr0]  Add. Sense: L-EC uncorrectable error
[ 3528.803939] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 6d 58 00 00 01 00
[ 3528.803953] end_request: I/O error, dev sr0, sector 374112
[ 3528.803958] Buffer I/O error on device sr0, logical block 93528
[ 3534.147110] sr 1:0:0:0: [sr0] Unhandled sense code
[ 3534.147116] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3534.147123] sr 1:0:0:0: [sr0]  Sense Key : Medium Error [current] 
[ 3534.147130] sr 1:0:0:0: [sr0]  Add. Sense: L-EC uncorrectable error
[ 3534.147137] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 6d 58 00 00 01 00
[ 3534.147151] end_request: I/O error, dev sr0, sector 374112
[ 3534.147156] Buffer I/O error on device sr0, logical block 93528
[ 3853.822413] EXT4-fs (sda7): previous I/O error to superblock detected
[ 3853.822432] EXT4-fs error (device sda7): ext4_find_entry:933: inode #2: comm nautilus: reading directory lblock 0
[ 4138.654710] EXT4-fs (sda7): previous I/O error to superblock detected
[ 4138.654742] EXT4-fs error (device sda7): ext4_find_entry:933: inode #2: comm ecryptfs-recove: reading directory lblock 0
[ 4302.328139] SQUASHFS error: squashfs_read_data failed to read block 0x957b0bd
[ 4302.328145] SQUASHFS error: Unable to read fragment cache entry [957b0bd]
[ 4302.328148] SQUASHFS error: Unable to read page, block 957b0bd, size 43ae
[ 4302.328277] SQUASHFS error: Unable to read fragment cache entry [957b0bd]
[ 4302.328281] SQUASHFS error: Unable to read page, block 957b0bd, size 43ae
[ 4302.328333] SQUASHFS error: Unable to read fragment cache entry [957b0bd]
[ 4302.328336] SQUASHFS error: Unable to read page, block 957b0bd, size 43ae
[ 4307.693189] sr 1:0:0:0: [sr0] Unhandled sense code
[ 4307.693195] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4307.693201] sr 1:0:0:0: [sr0]  Sense Key : Medium Error [current] 
[ 4307.693208] sr 1:0:0:0: [sr0]  Add. Sense: L-EC uncorrectable error
[ 4307.693215] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 6d 58 00 00 01 00
[ 4307.693230] end_request: I/O error, dev sr0, sector 374112
[ 4307.693236] Buffer I/O error on device sr0, logical block 93528
[ 4313.033654] sr 1:0:0:0: [sr0] Unhandled sense code
[ 4313.033659] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4313.033666] sr 1:0:0:0: [sr0]  Sense Key : Medium Error [current] 
[ 4313.033673] sr 1:0:0:0: [sr0]  Add. Sense: L-EC uncorrectable error
[ 4313.033680] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 01 6d 58 00 00 01 00
[ 4313.033694] end_request: I/O error, dev sr0, sector 374112
[ 4313.033700] Buffer I/O error on device sr0, logical block 93528
[ 4330.997942] SQUASHFS error: squashfs_read_data failed to read block 0x9a77ebc
[ 4330.997949] SQUASHFS error: Unable to read fragment cache entry [9a77ebc]
[ 4330.997953] SQUASHFS error: Unable to read page, block 9a77ebc, size a2c5
[ 4428.815370] EXT4-fs (sda7): previous I/O error to superblock detected
[ 4428.815460] EXT4-fs error (device sda7): ext4_put_super:737: Couldn't clean up the journal
[ 5507.863440] EXT4-fs (sda7): unable to read superblock

How to solve this problem?

---

### Post by linuxinstalledfromhdd on 2011-05-20
You should have made a backup of everything and put it aside first. 

I would reinstall Ubuntu 11.04 at this point if I were you.

---

