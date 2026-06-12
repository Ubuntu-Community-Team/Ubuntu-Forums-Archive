---
title: "Bad Sector"
date: 2009-11-27
forum: General Help
---

### Post by Xog on 2009-11-27
First off, Why am i getting so many results from this:
```
logan@logan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   57G   46G  56% /
udev                  501M  252K  501M   1% /dev
none                  501M  100K  501M   1% /dev/shm
none                  501M  200K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
none                  108G   57G   46G  56% /var/lib/ureadahead/debugfs

```

Secondly,

```
logan@logan-laptop:~$ dmesg | grep sd
[    1.212887] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.212934] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.212997] sd 0:0:0:0: [sda] Write Protect is off
[    1.213001] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.213034] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.213196]  sda:
[    1.224955]  sda1 sda2 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.250928]  sda5 >
[    1.251246] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.644794] EXT4-fs (sda1): barriers enabled
[    2.672772] kjournald2 starting: pid 380, dev sda1:8, commit interval 5 seconds
[    2.672793] EXT4-fs (sda1): delayed allocation enabled
[    2.673091] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.064675] sd 0:0:0:0: [sda] Unhandled sense code
[    6.064678] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.064683] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[    6.064714] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
[    6.064722] end_request: I/O error, dev sda, sector 20972607
[    6.157059] type=1505 audit(1259306300.639:10): operation="profile_load" pid=407 name=/usr/sbin/cupsd
[    7.537130] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k 
[    8.105898] EXT4-fs (sda1): internal journal on sda1:8
[   11.725062] type=1505 audit(1259306306.207:20): operation="profile_replace" pid=706 name=/usr/sbin/cupsd
[   15.293124] sdhci: Secure Digital Host Controller Interface driver
[   15.293128] sdhci: Copyright(c) Pierre Ossman
[   15.328076] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[   15.328111] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   25.261050] sd 0:0:0:0: [sda] Unhandled sense code
[   25.261053] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   25.261058] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   25.261088] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[   25.261097] end_request: I/O error, dev sda, sector 20972583
[   59.316810] sd 0:0:0:0: [sda] Unhandled sense code
[   59.316813] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   59.316818] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[   59.316849] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
[   59.316856] end_request: I/O error, dev sda, sector 20972607
[  896.096661] sd 0:0:0:0: [sda] Unhandled sense code
[  896.096664] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  896.096669] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  896.096700] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  896.096708] end_request: I/O error, dev sda, sector 20972583
[  913.444669] sd 0:0:0:0: [sda] Unhandled sense code
[  913.444672] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  913.444677] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  913.444707] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  913.444715] end_request: I/O error, dev sda, sector 21308383
[  929.892670] sd 0:0:0:0: [sda] Unhandled sense code
[  929.892674] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  929.892679] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  929.892709] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  929.892717] end_request: I/O error, dev sda, sector 21308383
[  947.356655] sd 0:0:0:0: [sda] Unhandled sense code
[  947.356658] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  947.356663] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  947.356693] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  947.356702] end_request: I/O error, dev sda, sector 21308383
[  965.976671] sd 0:0:0:0: [sda] Unhandled sense code
[  965.976674] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  965.976679] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  965.976709] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  965.976718] end_request: I/O error, dev sda, sector 21308383
[  982.560650] sd 0:0:0:0: [sda] Unhandled sense code
[  982.560653] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  982.560658] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[  982.560688] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  982.560696] end_request: I/O error, dev sda, sector 21308383
[ 1000.464685] sd 0:0:0:0: [sda] Unhandled sense code
[ 1000.464688] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1000.464693] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1000.464724] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1000.464732] end_request: I/O error, dev sda, sector 21308383
[ 1017.885450] sd 0:0:0:0: [sda] Unhandled sense code
[ 1017.885454] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1017.885459] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1017.885490] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1017.885498] end_request: I/O error, dev sda, sector 21308383
[ 1040.764706] sd 0:0:0:0: [sda] Unhandled sense code
[ 1040.764709] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1040.764715] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1040.764745] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1040.764753] end_request: I/O error, dev sda, sector 21308383
[ 1057.568668] sd 0:0:0:0: [sda] Unhandled sense code
[ 1057.568672] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1057.568677] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1057.568708] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1057.568716] end_request: I/O error, dev sda, sector 21308383
[ 1115.033122] sd 0:0:0:0: [sda] Unhandled sense code
[ 1115.033125] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1115.033130] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1115.033161] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1115.033169] end_request: I/O error, dev sda, sector 21308383
[ 1131.732685] sd 0:0:0:0: [sda] Unhandled sense code
[ 1131.732688] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1131.732693] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1131.732724] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1131.732732] end_request: I/O error, dev sda, sector 21308383
[ 1163.120708] sd 0:0:0:0: [sda] Unhandled sense code
[ 1163.120711] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1163.120716] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1163.120747] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1163.120755] end_request: I/O error, dev sda, sector 21308383
[ 1179.804697] sd 0:0:0:0: [sda] Unhandled sense code
[ 1179.804700] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1179.804706] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1179.804736] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1179.804744] end_request: I/O error, dev sda, sector 21308383
[ 1210.160675] sd 0:0:0:0: [sda] Unhandled sense code
[ 1210.160678] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1210.160684] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1210.160714] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
[ 1210.160722] end_request: I/O error, dev sda, sector 20972583
[ 1297.580652] sd 0:0:0:0: [sda] Unhandled sense code
[ 1297.580655] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1297.580660] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1297.580691] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1297.580699] end_request: I/O error, dev sda, sector 21308383
[ 1314.852677] sd 0:0:0:0: [sda] Unhandled sense code
[ 1314.852680] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1314.852685] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1314.852716] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1314.852724] end_request: I/O error, dev sda, sector 21308383
[ 1332.272727] sd 0:0:0:0: [sda] Unhandled sense code
[ 1332.272730] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1332.272735] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1332.272772] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1332.272780] end_request: I/O error, dev sda, sector 21308383

```

What does this exactly mean?

---

### Post by Xog on 2009-11-27
what's going on?
```

logan@logan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   57G   45G  56% /
udev                  501M  252K  501M   1% /dev
none                  501M  112K  501M   1% /dev/shm
none                  501M  200K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
logan@logan-laptop:~$ sudo fdisk -l
[sudo] password for logan: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
logan@logan-laptop:~$ 

```


I don't have any partitions set up, this is specifically an ubuntu only laptop with only 1 HD.

---

### Post by Sentience on 2009-11-27
Karmic has been destroying hard drives. I lost 2 hard drives since installing it, 1 laptop and one external. The laptop was not under warranty.

I heard the problem was fixed. How was it fixed? Is Ubuntu overriding the default bios on the disk? I guess it was a problem with the power saving mode being too low and causing too many rotations in too little time. I didnt have this problem with Jaunty though. With Karmic, the damage was instant. I heard previous releases were also hard on the HD, but Ive never seen damage like this happen so fast. It seems to only happen on laptops.

---

### Post by Xog on 2009-11-27
I read somewhere that Palimsest Disk Utility has a  bug in which it thinks there are multiple bad sectors using S.M.A.R.T. Data. If that's true then I'm happy but there's gotta be a way to fix this, my laptop keeps freezing up for a little bit and then it continues.

Also I've been running the Extended self-test over night.. it's been 10 hours and it's still not done. I'm not even sure if it's continuing. This  drive is only 120GB. It's certainly not frozen because the animated progress bar is still animated, but the progress of it isn't continuing any further.

:O

---

### Post by Xog on 2009-11-27
well this isn't the bug, my hard drive is now making squeaking & clicking noises.

Will it eventually just stop working and the computer shut down or will it wind up spinning and exploding out of my computer?


edit:
nvm, that was just clicking/squeaking noises from a webpage [www.brooklynbrewery.com](www.brooklynbrewery.com)

sigh.

---

### Post by Sentience on 2010-02-26
Did your hard drive eventually break like all 3 of mine have?

---

### Post by Xog on 2010-02-26
yeah, i can't even load ubuntu from its hard drive. i have to use the liveCD on my laptop.

still don't have enough money for a new hd :(

---

### Post by Zogg on 2010-03-21
I wouldn't write a post if this was a coincidence, but for the sake of record, this has to be investigated.

Today i turned on my HP Pavilion dv2000 lappy and was thrown into GRUB Recovery console. I have WinXP and Ubuntu 9.10 dual boot (ubuntu being in LVM partition) system. After booting up liveusb, I am presented with error messages, resembling the ones mention above, while trying to mount windows or ubuntu partitions (I'll try to recover those later). 
Then i load up winxp recovery console and hit chkdsk /p /r on windows partitions. At around 42% it fails because of 'unrecoverable errors'. I get back onto liveusb and attempt to copy the /home into external hdd. The /home is the only lvm partition that did actually mount. And the copy, even tho some files fail because of 'Input/Output error', does continue to copy. Very slowly and spitting hundreds of error messages into logs, like these:

Mar 21 22:32:18 bt kernel: ata1:EH complete
Mar 21 22:32:18 bt kernel: ata1.00: configured for UDMA/66
Mar 21 22:32:18 bt kernel: ata1:EH complete
Mar 21 22:32:18 bt kernel: ata1.00: configured for UDMA/66
Mar 21 22:32:18 bt kernel: sd 2:0:0:0: [sda] Unhandled sense code
Mar 21 22:32:18 bt kernel: sd 2:0:0:0: [sda] Result: hostbyte=0x00 drivebyte=0x08
Mar 21 22:32:18 bt kernel: sd 2:0:0:0: [sda] Sense Key : 0x3 [current] [descriptor]
Mar 21 22:32:18 bt kernel: Descriptor sense data with sense descriptors (in hex)
Mar 21 22:32:18 bt kernel: 72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00
Mar 21 22:32:18 bt kernel: 05 c0 db 6a
Mar 21 22:32:18 bt kernel: sd 2:0:0:0: [sda] ASC=0x11 ASCQ=0x4
Mar 21 22:32:18 bt kernel: ata1: EH complete
Mar 21 22:32:18 bt kernel: ata1: link is slow to respond, please be patient (ready=0)
Mar 21 22:32:18 bt kernel: ata1: device not ready (errno=-16), forcing hardreset
Mar 21 22:32:18 bt kernel: ata1: soft resetting link
Mar 21 22:32:18 bt kernel: ata1.00: configured for UDMA/66
Mar 21 22:32:18 bt kernel: ata1: EH complete

... (the time stamp here is just for visuals)

I have never had any warnings of bad sectors before (smartmontools are into karmic by default?).
I have latest updates installed yesterday.

And guess what happened next? **My friend calls me and tells me he has _exactly_ same problem**!

[SIZE="4"][COLOR="Red"]**I request guidance into debugging and clearing out of what may be the roots of failing hard drives!!**[/COLOR][/SIZE]

---

### Post by soltanis on 2010-03-21
Ubuntu (and other Linux distributions in general) used to have a problem in laptops. The problem stemmed from some BIOS's (seemingly intentionally) having overly aggressive power management that would park their read-write heads often (once every minute) shortening the life of the drive considerably. It is my understanding that this should have been fixed.

If it isn't, you can tell Ubuntu to set advanced power management to conservative or off, which will shorten battery life and increase heat, but when you're on AC power, isn't really much of a problem:

```

sudo apt-get install smartmontools
sudo hdparm -B 254 /dev/sda

```

Hard resets on SATA links tend to happen frequently, I see them on my server and they haven't really impacted performance or caused boot errors (yet).

If you go into Live CD or USB, can you mount any of your partitions? If not, what are the errors you get?

---

