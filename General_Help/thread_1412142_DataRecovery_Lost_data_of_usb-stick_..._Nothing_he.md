---
title: "DataRecovery: Lost data of usb-stick ... Nothing helps&quot;"
date: 2010-02-20
forum: General Help
---

### Post by deadland on 2010-02-20
Hi ubuntu-friends,

I have a serious problem, because I can't read my usb-stick any more, where I stored my keepassx password file!!! I had another backup of this file, but I lost it also a few days ago, so there is nothing left, but restoring this usb stick.

When I plug-in the usb stick I get the following dmesg output:

```
sdb: unknown partition table
```

So I ran testdisk, and selected:

```
media: Disk /dev/sdb - 4022 MB / 3835 MiB - SanDisk U3 Titanium

partition table type: [Intel]
```

I selected [Analyse]

I receive the following message.

```
Disk /dev/sdb - 4022 MB / 3835 MiB - CHS 1021 124 62

Current partition structure:

     Partition                  Start        End    Size in sectors





Partition sector doesn't have the endmark 0xAA55
```


I selected [Quick Search]

```
I've got „Should TestDisk search for partition created under Vista ? [Y/N] (answer Yes if unsure)“
```

I said „Yes“

```
I've got “Structure: Ok.” 
```

But testdisk found no partition! 

I selected [Deeper Search]

Same output as before!


So I ran “gpart”

and receive the following output:

```
sudo gpart /dev/sdb



Begin scan...

End scan.



Checking partitions...

Ok.



Guessed primary partition table:

Primary partition(1)

   type: 000(0x00)(unused)

   size: 0mb #s(0) s(0-0)

   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r



Primary partition(2)

   type: 000(0x00)(unused)

   size: 0mb #s(0) s(0-0)

   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r



Primary partition(3)

   type: 000(0x00)(unused)

   size: 0mb #s(0) s(0-0)

   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r



Primary partition(4)

   type: 000(0x00)(unused)

   size: 0mb #s(0) s(0-0)

   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
```


Well this probably means, it found noting.

So I ran:

```
sudo ddrescue --direct --retrim --max-retries=3 /dev/sdb imagefile logfile 





Press Ctrl-C to interrupt

Initial status (read from logfile)

rescued:         0 B,  errsize:       0 B,  errors:       0

Current status

rescued:     4022 MB,  errsize:       0 B,  current rate:   20381 kB/s

   ipos:     4022 MB,   errors:       0,    average rate:   17155 kB/s

   opos:     4022 MB,     time from last successful read:       0 s

Finished                   


obertm@obertm-laptop:~$ sudo mmls imagefile -b

Cannot determine partition type

```

I also tried foremost, but it does't found anything.


Could anyone help me. PLEASE.

---

### Post by jenaniston on 2010-02-20
> **deadland said:**
> 

```
I've got “Structure: Ok.” 
```Could anyone help me. PLEASE.

testdisk Structure: OK . . . this is good.

try and run hexdump for the USB

```
hexdump -C /dev/sdb
```if it starts running fast then <**Ctrl-C> **to stop

Did it get anything . . . ?

---

### Post by deadland on 2010-02-20
Hi thanks for your reply!

This is the output:

```
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
efbffe00
```

Don't know if this are good news?

---

### Post by TopEnder on 2010-02-20
deadland,    You could try "testdisk" it is in Synaptic Package Manager also do a search on "testdisk" in the forum, it may help you with your problem.   TopEnder
PS I did not read your original post in toto but  still think "testdisk" will help.

---

### Post by jenaniston on 2010-02-21
> **deadland said:**
> 
This is the output:

```
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
efbffe00
```Don't know if this are good news?

Doesn't seem all that promising from my debugging skills . . .
hexdump with all 0's means - and any expert please correct me if wrong - that there's is **NO data** there . . .

As a comparison you can try the hexdump of some other partition or drive known to have data . . . 
and you will see what I mean -
  - the screen will scroll by with hexadecimal data output and you will *have* to use <ctrl-c> to quit the command.
(it just "dumps" the hexadecimal output to the screen btw . . . doesn't change anything or remove it)

---

### Post by jenaniston on 2010-02-21
> **deadland said:**
> 

```
media: Disk /dev/sdb - 4022 MB / 3835 MiB - SanDisk U3 Titanium


```Could anyone help me. PLEASE.

Wait . . . I too also just noticed more of your original post . . .
you have the notorious and pia "SanDisk U3" still  blocking access to everything . . . ?

Is that all this really is ?  . . . run

```
df -h
```

---

### Post by deadland on 2010-02-21
Hi jenaniston,

this is the output:

```
df -h
Dateisystem            Größe Benut  Verf Ben% Eingehängt auf
/dev/sda1              88G   77G  7,3G  92% /
udev                 1007M  292K 1006M   1% /dev
none                 1007M  436K 1006M   1% /dev/shm
tmpfs                1007M   20K 1006M   1% /tmp
none                 1007M  296K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
tmpfs                1007M     0 1007M   0% /var/tmp
tmpfs                1007M  676K 1006M   1% /var/log
```

I also added the dmesg output, when I plug-in the usb-stick:

```
[ 7105.756126] usb 1-5: new high speed USB device using ehci_hcd and address 6
[ 7105.889278] usb 1-5: configuration #1 chosen from 1 choice
[ 7105.958835] Initializing USB Mass Storage driver...
[ 7105.968069] scsi2 : SCSI emulation for USB Mass Storage devices
[ 7105.968261] usbcore: registered new interface driver usb-storage
[ 7105.968270] USB Mass Storage support registered.
[ 7105.973223] usb-storage: device found at 6
[ 7105.973227] usb-storage: waiting for device to settle before scanning
[ 7110.973341] usb-storage: device scan complete
[ 7110.973938] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Titanium      7.01 PQ: 0 ANSI: 0 CCS
[ 7110.974556] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Titanium      7.01 PQ: 0 ANSI: 0
[ 7110.975590] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 7110.988220] sd 2:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[ 7110.989458] sd 2:0:0:0: [sdb] Write Protect is off
[ 7110.989466] sd 2:0:0:0: [sdb] Mode Sense: 45 00 00 08
[ 7110.989471] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 7110.994799] sr1: scsi3-mmc drive: 48x/48x tray
[ 7110.995039] sr 2:0:0:1: Attached scsi CD-ROM sr1
[ 7110.995180] sr 2:0:0:1: Attached scsi generic sg3 type 5
[ 7110.996705] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 7110.996714]  sdb: unknown partition table
[ 7111.023465] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 7111.023475] sd 2:0:0:0: [sdb] Attached SCSI removable disk

```

> you have the notorious and pia "SanDisk U3" still blocking access to everything . . . ?

Yes it doesn't even add the "U3 CD-Rom Drive".

---

### Post by jenaniston on 2010-02-21
This looks like the U3 is still there . . .
```
. . .
[ 7110.973938] scsi 2:0:0:0: Direct-Access     SanDisk  U3 Titanium      7.01 PQ: 0 ANSI: 0 CCS
[ 7110.974556] scsi 2:0:0:1: CD-ROM            SanDisk  U3 Titanium      7.01 PQ: 0 ANSI: 0
. . .
```can you mount the USB, then run df -h and see if the U3 partition then shows up  . . .

"U3 is an ISO9660 partition (shows up as CD-ROM), around 14 Mbyte. That is the U3 System partition, it mounts to /dev/sr1 as a read-only device . . ."

---

### Post by deadland on 2010-02-22
Hi jenaniston,

I will try that, when I'm back home tonight.

Thanks

---

### Post by deadland on 2010-02-22
Okay, when I ran:
```

sudo mount /dev/sr1 /media/cdrom0/
```

The u3-cdrom does not show up.

Thats the dmesg output:

```
[ 1974.221711] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.221720] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.221728] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.221738] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.221748] end_request: I/O error, dev sr1, sector 196352
[ 1974.221757] __ratelimit: 3 callbacks suppressed
[ 1974.221763] Buffer I/O error on device sr1, logical block 49088
[ 1974.221770] Buffer I/O error on device sr1, logical block 49089
[ 1974.227704] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.227710] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.227717] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.227725] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.227735] end_request: I/O error, dev sr1, sector 196352
[ 1974.227741] Buffer I/O error on device sr1, logical block 49088
[ 1974.227748] Buffer I/O error on device sr1, logical block 49089
[ 1974.232834] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.232841] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.232848] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.232857] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.232868] end_request: I/O error, dev sr1, sector 196584
[ 1974.232877] Buffer I/O error on device sr1, logical block 49146
[ 1974.232884] Buffer I/O error on device sr1, logical block 49147
[ 1974.237999] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.238004] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.238012] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.238020] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.238030] end_request: I/O error, dev sr1, sector 196584
[ 1974.238036] Buffer I/O error on device sr1, logical block 49146
[ 1974.238042] Buffer I/O error on device sr1, logical block 49147
[ 1974.243081] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.243086] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.243093] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.243102] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.243111] end_request: I/O error, dev sr1, sector 196600
[ 1974.243118] Buffer I/O error on device sr1, logical block 49150
[ 1974.247956] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.247962] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.247969] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.247978] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.247987] end_request: I/O error, dev sr1, sector 196600
[ 1974.247994] Buffer I/O error on device sr1, logical block 49150
[ 1974.251597] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.251603] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.251610] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.251619] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.251629] end_request: I/O error, dev sr1, sector 196600
[ 1974.256471] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.256477] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.256484] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.256492] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.256502] end_request: I/O error, dev sr1, sector 196600
[ 1974.261346] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.261351] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.261358] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.261366] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.261376] end_request: I/O error, dev sr1, sector 196600
[ 1974.264966] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.264971] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.264978] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.264987] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.264996] end_request: I/O error, dev sr1, sector 196600
[ 1974.270971] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.270977] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.270984] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.270992] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.271001] end_request: I/O error, dev sr1, sector 196600
[ 1974.275841] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.275846] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.275853] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.275862] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.275871] end_request: I/O error, dev sr1, sector 196536
[ 1974.279589] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.279597] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.279605] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.279615] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.279625] end_request: I/O error, dev sr1, sector 196592
[ 1974.284597] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.284605] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.284613] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.284622] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.284633] end_request: I/O error, dev sr1, sector 196600
[ 1974.289577] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.289582] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.289589] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.289598] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.289607] end_request: I/O error, dev sr1, sector 196600
[ 1974.328477] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.328485] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.328493] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.328503] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.328513] end_request: I/O error, dev sr1, sector 196352
[ 1974.333181] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.333187] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.333194] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.333204] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.333213] end_request: I/O error, dev sr1, sector 196352
[ 1974.337968] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.337974] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.337981] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.337990] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.337999] end_request: I/O error, dev sr1, sector 196584
[ 1974.342722] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.342728] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.342736] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.342745] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.342754] end_request: I/O error, dev sr1, sector 196584
[ 1974.347472] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.347481] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.347489] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.347499] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.347510] end_request: I/O error, dev sr1, sector 196600
[ 1974.352212] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.352219] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.352226] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.352235] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.352245] end_request: I/O error, dev sr1, sector 196600
[ 1974.355835] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.355841] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.355848] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.355857] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.355866] end_request: I/O error, dev sr1, sector 196600
[ 1974.361599] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.361607] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.361614] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.361624] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.361634] end_request: I/O error, dev sr1, sector 196600
[ 1974.366345] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.366350] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.366358] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.366366] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.366375] end_request: I/O error, dev sr1, sector 196600
[ 1974.371097] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.371104] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.371111] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.371120] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.371130] end_request: I/O error, dev sr1, sector 196600
[ 1974.375850] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.375858] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.375865] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.375875] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.375885] end_request: I/O error, dev sr1, sector 196600
[ 1974.380595] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.380601] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.380609] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.380617] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.380626] end_request: I/O error, dev sr1, sector 196536
[ 1974.385212] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.385218] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.385225] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.385234] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.385243] end_request: I/O error, dev sr1, sector 196592
[ 1974.389964] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.389969] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.389977] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.389985] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.389994] end_request: I/O error, dev sr1, sector 196600
[ 1974.394590] sr 2:0:0:1: [sr1] Unhandled sense code
[ 1974.394596] sr 2:0:0:1: [sr1] Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[ 1974.394603] sr 2:0:0:1: [sr1] Sense Key : Hardware Error [current] 
[ 1974.394611] sr 2:0:0:1: [sr1] Add. Sense: No additional sense information
[ 1974.394621] end_request: I/O error, dev sr1, sector 196600

```

So that means, there are a lot of sectors damaged?

---

### Post by deadland on 2010-02-28
Hi jenaniston,

should I wait for another tip or there is nothing else to do?


Thanks in advanced!

---

### Post by theonhighgod on 2010-05-17
have you tried running "photorec" against the imagefile you extracted with ddrescue? could be worth a try

---

### Post by theonhighgod on 2010-05-17
deleted as double posted by mistake, sorry

---

### Post by deadland on 2010-05-17
Thanks for your tip, but I gave up one week ago and deleted the image file. :(

---

