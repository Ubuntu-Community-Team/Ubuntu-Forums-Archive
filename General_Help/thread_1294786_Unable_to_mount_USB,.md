---
title: "Unable to mount USB,"
date: 2009-10-18
forum: General Help
---

### Post by Calixte on 2009-10-18
A USB pen I have (named Bob) refuses to mount. I've tried reformatting it but nothing changed

Here's the error message I receive:
> Unable to mount Bob
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is the result for fsck (if it can be useful):
```
calixte@Lucy:~$ sudo fsck -n /dev/sdb1
fsck from util-linux-ng 2.16
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
/dev/sdb1: 1 files, 1/978042 clusters

```

Thanks
-Calixte

---

### Post by P4man on 2009-10-19
try running gparted and delete and recreate the partition?

---

### Post by Baelus on 2009-10-19
> Unable to mount Bob
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so 

Can paste the output of ```
dmesg |tail -20
```

That usually gives some indication of what's wrong.

---

### Post by Calixte on 2009-10-19
Yeah, I did that, but it just gives me the same old error :-s

---

### Post by Calixte on 2009-10-19
> **Baelus said:**
> Can paste the output of ```
dmesg |tail -20
```

That usually gives some indication of what's wrong.

```
calixte@Lucy:~$ dmesg |tail -20
[ 2258.238419] wlan0: associated
[ 2601.620100] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 2601.754902] usb 1-1: configuration #1 chosen from 1 choice
[ 2601.884274] Initializing USB Mass Storage driver...
[ 2601.884829] scsi6 : SCSI emulation for USB Mass Storage devices
[ 2601.887997] usbcore: registered new interface driver usb-storage
[ 2601.889184] USB Mass Storage support registered.
[ 2601.891698] usb-storage: device found at 3
[ 2601.891712] usb-storage: waiting for device to settle before scanning
[ 2606.888484] usb-storage: device scan complete
[ 2606.889431] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 4GB    8.07 PQ: 0 ANSI: 2
[ 2606.893296] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 2606.907030] sd 6:0:0:0: [sdb] 7843840 512-byte logical blocks: (4.01 GB/3.74 GiB)
[ 2606.909647] sd 6:0:0:0: [sdb] Write Protect is off
[ 2606.909660] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2606.909667] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2606.914957] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2606.914976]  sdb: sdb1
[ 2607.222722] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2607.222744] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

---

### Post by Baelus on 2009-10-19
That looks like everything's fine.

I take it you're trying to mount it from the terminal. Did you use the "-t vfat" option when mounting it?

---

### Post by Calixte on 2009-10-19
Ok, I managed to mount it with ```
calixte@Lucy:~$ sudo mount -t vfat /dev/sdb1 /media/cdrom0
```

Thanks a lot for the tip. I've got another question however. How can I ask the system to mount the device in a more orthodox way (i.e. not as cdrom0)
If I specify any other location, it won't mount. It's not horribly problematic (The computer is a netbook, so I don't have an optical CD-ROM drive anyway), but kind of annoying nonetheless.

---

### Post by Baelus on 2009-10-19
Glad you got it working.

You should be able to create a folder and use it as a mount point. You can make a folder in /media called "jetflash" and mount it like this:

```
sudo mount -t vfat /dev/sdb1 /media/jetflash
```

Give that a try.

The mount command needs to know the filesystem of the partition being mounted. The -t option is used for that using vfat for FAT32/16, ext3 for ext3, ntfs-3g for NTFS etc. Otherwise the mount command is kinda stupid and gives an error. :)

---

### Post by rgnr on 2009-11-14
Hello. Since Karmic I cannot automount any USB device ( I can mount it terminal, but I'd like to get the automount feature back. 

dmesg | tail -20
[44273.300655] usb 1-8: configuration #1 chosen from 1 choice
[44273.305729] scsi8 : SCSI emulation for USB Mass Storage devices
[44273.305855] usb-storage: device found at 5
[44273.305857] usb-storage: waiting for device to settle before scanning
[44278.305918] usb-storage: device scan complete
[44278.311011] scsi scan: INQUIRY result too short (5), using 36
[44278.311018] scsi 8:0:0:0: Direct-Access     USB 2.0  (HS) Flash Disk  1.00 PQ: 0 ANSI: 0 CCS
[44278.311356] sd 8:0:0:0: Attached scsi generic sg3 type 0
[44278.315141] sd 8:0:0:0: [sdc] 4008881 512-byte logical blocks: (2.05 GB/1.91 GiB)
[44278.316025] sd 8:0:0:0: [sdc] Write Protect is off
[44278.316028] sd 8:0:0:0: [sdc] Mode Sense: 00 c0 00 00
[44278.316031] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[44278.321985] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[44278.321992]  sdc: sdc1
[44278.340067] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[44278.340073] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[44321.464588] FAT: IO charset ANSI_X3.4-1968 not found
[44321.517477] FAT: IO charset ANSI_X3.4-1968 not found
[44647.362745] FAT: invalid media value (0x06)
[44647.362753] VFS: Can't find a valid FAT filesystem on dev sdc.

---

### Post by Baelus on 2009-11-14
I'm not using Karmic, but try this thread:

[http://wwww.ubuntuforums.org/showthread.php?t=1309239]("http://wwww.ubuntuforums.org/showthread.php?t=1309239")

---

### Post by tranpd15 on 2010-11-23
This is the message i got when I did dmesg
[98820.750082] JBD: IO error -5 recovering block 17872 in log
[98820.750085] JBD: Failed to read block at offset 17873
[98820.750087] JBD: IO error -5 recovering block 17873 in log
[98820.750090] JBD: Failed to read block at offset 17874
[98820.750092] JBD: IO error -5 recovering block 17874 in log
[98820.750095] JBD: Failed to read block at offset 17875
[98820.750097] JBD: IO error -5 recovering block 17875 in log
[98820.750100] JBD: Failed to read block at offset 17876
[98820.750103] JBD: IO error -5 recovering block 17876 in log
[98820.750105] JBD: Failed to read block at offset 17877
[98820.750108] JBD: IO error -5 recovering block 17877 in log
[98820.750110] JBD: Failed to read block at offset 17878
[98820.750113] JBD: IO error -5 recovering block 17878 in log
[98820.750115] JBD: Failed to read block at offset 17879
[98820.750118] JBD: IO error -5 recovering block 17879 in log
[98820.750120] JBD: Failed to read block at offset 17880
[98820.750123] JBD: IO error -5 recovering block 17880 in log
[98820.750125] JBD: Failed to read block at offset 17881
[98820.750128] JBD: IO error -5 recovering block 17881 in log
[98820.750130] JBD: Failed to read block at offset 17882
[98820.750133] JBD: IO error -5 recovering block 17882 in log
[98820.750136] JBD: Failed to read block at offset 17883
[98820.750138] JBD: IO error -5 recovering block 17883 in log
[98820.750141] JBD: Failed to read block at offset 17884
[98820.750143] JBD: IO error -5 recovering block 17884 in log
[98820.750146] JBD: Failed to read block at offset 17885
[98820.750148] JBD: IO error -5 recovering block 17885 in log
[98820.750151] JBD: Failed to read block at offset 17886
[98820.750153] JBD: IO error -5 recovering block 17886 in log
[98820.750255] JBD: Failed to read block at offset 17887
[98820.750258] JBD: IO error -5 recovering block 17887 in log
[98820.750261] JBD: Failed to read block at offset 17888
[98820.750263] JBD: IO error -5 recovering block 17888 in log
[98820.750266] JBD: Failed to read block at offset 17889
[98820.750269] JBD: IO error -5 recovering block 17889 in log
[98820.750271] JBD: Failed to read block at offset 17890
[98820.750274] JBD: IO error -5 recovering block 17890 in log
[98820.750277] JBD: Failed to read block at offset 17891
[98820.750279] JBD: IO error -5 recovering block 17891 in log
[98820.750282] JBD: Failed to read block at offset 17892
[98820.750284] JBD: IO error -5 recovering block 17892 in log
[98820.750287] JBD: Failed to read block at offset 17893
[98820.750289] JBD: IO error -5 recovering block 17893 in log
[98820.750292] JBD: Failed to read block at offset 17894
[98820.750294] JBD: IO error -5 recovering block 17894 in log
[98820.750297] JBD: Failed to read block at offset 17895
[98820.750299] JBD: IO error -5 recovering block 17895 in log
[98820.750302] JBD: Failed to read block at offset 17896
[98820.750305] JBD: IO error -5 recovering block 17896 in log
[98820.750308] JBD: Failed to read block at offset 17897
[98820.750310] JBD: IO error -5 recovering block 17897 in log
[98820.750313] JBD: Failed to read block at offset 17898
[98820.750315] JBD: IO error -5 recovering block 17898 in log
[98820.750318] JBD: Failed to read block at offset 17899
[98820.750320] JBD: IO error -5 recovering block 17899 in log
[98820.750323] JBD: Failed to read block at offset 17900
[98820.750325] JBD: IO error -5 recovering block 17900 in log
[98820.750328] JBD: Failed to read block at offset 17901
[98820.750331] JBD: IO error -5 recovering block 17901 in log
[98820.750333] JBD: Failed to read block at offset 17902
[98820.750336] JBD: IO error -5 recovering block 17902 in log
[98820.750339] JBD: Failed to read block at offset 17903
[98820.750341] JBD: IO error -5 recovering block 17903 in log
[98820.750344] JBD: Failed to read block at offset 17904
[98820.750346] JBD: IO error -5 recovering block 17904 in log
[98820.750349] JBD: Failed to read block at offset 17905
[98820.750351] JBD: IO error -5 recovering block 17905 in log
[98820.750354] JBD: Failed to read block at offset 17906
[98820.750356] JBD: IO error -5 recovering block 17906 in log
[98820.750359] JBD: Failed to read block at offset 17907
[98820.750362] JBD: IO error -5 recovering block 17907 in log
[98820.750364] JBD: Failed to read block at offset 17908
[98820.750367] JBD: IO error -5 recovering block 17908 in log
[98820.750370] JBD: Failed to read block at offset 17909
[98820.750372] JBD: IO error -5 recovering block 17909 in log
[98820.750375] JBD: Failed to read block at offset 17910
[98820.750377] JBD: IO error -5 recovering block 17910 in log
[98820.750380] JBD: Failed to read block at offset 17911
[98820.750382] JBD: IO error -5 recovering block 17911 in log
[98820.750385] JBD: Failed to read block at offset 17912
[98820.750387] JBD: IO error -5 recovering block 17912 in log
[98820.750390] JBD: Failed to read block at offset 17913
[98820.750393] JBD: IO error -5 recovering block 17913 in log
[98820.750395] JBD: Failed to read block at offset 17914
[98820.750398] JBD: IO error -5 recovering block 17914 in log
[98820.750401] JBD: Failed to read block at offset 17915
[98820.750403] JBD: IO error -5 recovering block 17915 in log
[98820.750406] JBD: Failed to read block at offset 17916
[98820.750408] JBD: IO error -5 recovering block 17916 in log
[98820.750411] JBD: Failed to read block at offset 17917
[98820.750413] JBD: IO error -5 recovering block 17917 in log
[98820.750416] JBD: Failed to read block at offset 17918
[98820.750418] JBD: IO error -5 recovering block 17918 in log
[98820.750502] JBD: Failed to read block at offset 17919
[98820.750505] JBD: IO error -5 recovering block 17919 in log
[98820.750508] JBD: Failed to read block at offset 17920
[98820.750510] JBD: IO error -5 recovering block 17920 in log
[98820.750513] JBD: Failed to read block at offset 17921
[98820.750515] JBD: IO error -5 recovering block 17921 in log
[98820.750518] JBD: Failed to read block at offset 17922
[98820.750521] JBD: IO error -5 recovering block 17922 in log
[98820.750523] JBD: Failed to read block at offset 17923
[98820.750526] JBD: IO error -5 recovering block 17923 in log
[98820.750529] JBD: Failed to read block at offset 17924
[98820.750531] JBD: IO error -5 recovering block 17924 in log
[98820.750534] JBD: Failed to read block at offset 17925
[98820.750536] JBD: IO error -5 recovering block 17925 in log
[98820.750539] JBD: Failed to read block at offset 17926
[98820.750541] JBD: IO error -5 recovering block 17926 in log
[98820.750544] JBD: Failed to read block at offset 17927
[98820.750547] JBD: IO error -5 recovering block 17927 in log
[98820.750549] JBD: Failed to read block at offset 17928
[98820.750552] JBD: IO error -5 recovering block 17928 in log
[98820.750555] JBD: Failed to read block at offset 17929
[98820.750557] JBD: IO error -5 recovering block 17929 in log
[98820.750560] JBD: Failed to read block at offset 17930
[98820.750562] JBD: IO error -5 recovering block 17930 in log
[98820.750565] JBD: Failed to read block at offset 17931
[98820.750567] JBD: IO error -5 recovering block 17931 in log
[98820.750570] JBD: Failed to read block at offset 17932
[98820.750572] JBD: IO error -5 recovering block 17932 in log
[98820.750575] JBD: Failed to read block at offset 17933
[98820.750577] JBD: IO error -5 recovering block 17933 in log
[98820.750580] JBD: Failed to read block at offset 17934
[98820.750582] JBD: IO error -5 recovering block 17934 in log
[98820.750585] JBD: Failed to read block at offset 17935
[98820.750587] JBD: IO error -5 recovering block 17935 in log
[98820.750590] JBD: Failed to read block at offset 17936
[98820.750592] JBD: IO error -5 recovering block 17936 in log
[98820.750595] JBD: Failed to read block at offset 17937
[98820.750597] JBD: IO error -5 recovering block 17937 in log
[98820.750600] JBD: Failed to read block at offset 17938
[98820.750602] JBD: IO error -5 recovering block 17938 in log
[98820.750605] JBD: Failed to read block at offset 17939
[98820.750607] JBD: IO error -5 recovering block 17939 in log
[98820.769495] JBD: recovery failed
[98820.769501] EXT3-fs: error loading journal.
[98820.929926] usb 1-3: new high speed USB device using ehci_hcd and address 6
[98836.052054] usb 1-3: device descriptor read/64, error -110
[98851.268046] usb 1-3: device descriptor read/64, error -110
[98851.484059] usb 1-3: new high speed USB device using ehci_hcd and address 7
[98866.596053] usb 1-3: device descriptor read/64, error -110
[98881.812064] usb 1-3: device descriptor read/64, error -110
[98882.028060] usb 1-3: new high speed USB device using ehci_hcd and address 8
[98882.062626] usb 1-3: device descriptor read/8, error -71
[98882.192251] usb 1-3: device descriptor read/8, error -71
[98882.408043] usb 1-3: new high speed USB device using ehci_hcd and address 9
[98882.440236] usb 1-3: device descriptor read/8, error -71
[98882.574762] usb 1-3: device descriptor read/8, error -71
[98882.676183] hub 1-0:1.0: unable to enumerate USB device on port 3
[98882.944055] usb 3-1: new full speed USB device using uhci_hcd and address 3
[98898.116497] usb 3-1: device descriptor read/64, error -110
[98913.336063] usb 3-1: device descriptor read/64, error -110
[98913.552042] usb 3-1: new full speed USB device using uhci_hcd and address 4
[98928.664446] usb 3-1: device descriptor read/64, error -110
[98943.880077] usb 3-1: device descriptor read/64, error -110
[98944.096858] usb 3-1: new full speed USB device using uhci_hcd and address 5
[98944.128089] usb 3-1: device descriptor read/8, error -71
[98944.267070] usb 3-1: device descriptor read/8, error -71
[98944.480078] usb 3-1: new full speed USB device using uhci_hcd and address 6
[98944.511080] usb 3-1: device descriptor read/8, error -71
[98944.640415] usb 3-1: device descriptor read/8, error -71
[98944.744068] hub 3-0:1.0: unable to enumerate USB device on port 1
[99082.224607] type=1503 audit(1290567096.824:76): operation="open" pid=19061 parent=19059 profile="/usr/sbin/mysqld-akonadi" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
[99092.910219] type=1503 audit(1290567107.508:77): operation="open" pid=19069 parent=19054 profile="/usr/sbin/mysqld-akonadi" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
[99092.978723] type=1503 audit(1290567107.577:78): operation="open" pid=19069 parent=19054 profile="/usr/sbin/mysqld-akonadi" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/mysql/my.cnf"
[99195.980066] usb 1-3: new high speed USB device using ehci_hcd and address 10
[99196.113079] usb 1-3: configuration #1 chosen from 1 choice
[99196.119986] scsi5 : SCSI emulation for USB Mass Storage devices
[99196.120228] usb-storage: device found at 10
[99196.120233] usb-storage: waiting for device to settle before scanning
[99201.120220] usb-storage: device scan complete
[99201.120710] scsi 5:0:0:0: Direct-Access     OCZ      SOLID_SSD         Dev PQ: 0 ANSI: 0 CCS
[99201.121647] sd 5:0:0:0: Attached scsi generic sg2 type 0
[99201.139085] sd 5:0:0:0: [sdb] 125045424 512-byte logical blocks: (64.0 GB/59.6 GiB)
[99201.140708] sd 5:0:0:0: [sdb] Write Protect is off
[99201.140712] sd 5:0:0:0: [sdb] Mode Sense: 00 38 00 00
[99201.140715] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[99201.144489] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[99201.144495]  sdb: sdb1 sdb2 < sdb5 >
[99201.154399] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[99201.154406] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[99262.112071] usb 1-3: reset high speed USB device using ehci_hcd and address 10
[99262.256422] usb 1-3: device descriptor read/all, error -71
[99262.372068] usb 1-3: reset high speed USB device using ehci_hcd and address 10
[99277.484068] usb 1-3: device descriptor read/64, error -110
[99292.700069] usb 1-3: device descriptor read/64, error -110
[99292.916058] usb 1-3: reset high speed USB device using ehci_hcd and address 10
[99292.949065] usb 1-3: device descriptor read/8, error -71
[99293.080349] usb 1-3: device descriptor read/8, error -71
[99293.296066] usb 1-3: reset high speed USB device using ehci_hcd and address 10
[99293.328671] usb 1-3: device descriptor read/8, error -71
[99293.461176] usb 1-3: device descriptor read/8, error -71
[99293.564105] sd 5:0:0:0: Device offlined - not ready after error recovery
[99293.564127] sd 5:0:0:0: [sdb] Unhandled error code
[99293.564133] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[99293.564142] end_request: I/O error, dev sdb, sector 63
[99293.564153] Buffer I/O error on device sdb1, logical block 0
[99293.564159] lost page write due to I/O error on sdb1
[99293.564172] Buffer I/O error on device sdb1, logical block 1
[99293.564177] lost page write due to I/O error on sdb1
[99293.564185] Buffer I/O error on device sdb1, logical block 2
[99293.564190] lost page write due to I/O error on sdb1
[99293.564197] Buffer I/O error on device sdb1, logical block 3
[99293.564203] lost page write due to I/O error on sdb1
[99293.564210] Buffer I/O error on device sdb1, logical block 4
[99293.564216] lost page write due to I/O error on sdb1
[99293.564237] sd 5:0:0:0: rejecting I/O to offline device
[99293.564263] sd 5:0:0:0: rejecting I/O to offline device
[99293.564275] sd 5:0:0:0: rejecting I/O to offline device
[99293.564312] sd 5:0:0:0: rejecting I/O to offline device
[99293.564372] sd 5:0:0:0: rejecting I/O to offline device
[99293.564389] sd 5:0:0:0: rejecting I/O to offline device
[99293.564406] sd 5:0:0:0: rejecting I/O to offline device
[99293.564415] sd 5:0:0:0: rejecting I/O to offline device
[99293.564426] sd 5:0:0:0: rejecting I/O to offline device
[99293.564437] sd 5:0:0:0: rejecting I/O to offline device
[99293.564446] sd 5:0:0:0: rejecting I/O to offline device
[99293.564455] sd 5:0:0:0: rejecting I/O to offline device
[99293.564464] sd 5:0:0:0: rejecting I/O to offline device
[99293.564477] sd 5:0:0:0: rejecting I/O to offline device
[99293.564487] sd 5:0:0:0: rejecting I/O to offline device
[99293.564498] sd 5:0:0:0: rejecting I/O to offline device
[99293.564506] sd 5:0:0:0: rejecting I/O to offline device
[99293.564516] sd 5:0:0:0: rejecting I/O to offline device
[99293.564525] sd 5:0:0:0: rejecting I/O to offline device
[99293.564537] sd 5:0:0:0: rejecting I/O to offline device
[99293.564546] sd 5:0:0:0: rejecting I/O to offline device
[99293.564557] sd 5:0:0:0: rejecting I/O to offline device
[99293.564568] sd 5:0:0:0: rejecting I/O to offline device
[99293.564597] sd 5:0:0:0: rejecting I/O to offline device
[99293.564608] sd 5:0:0:0: rejecting I/O to offline device
[99293.564620] sd 5:0:0:0: rejecting I/O to offline device
[99293.564629] sd 5:0:0:0: rejecting I/O to offline device
[99293.564638] sd 5:0:0:0: rejecting I/O to offline device
[99293.564660] sd 5:0:0:0: rejecting I/O to offline device
[99293.564681] sd 5:0:0:0: rejecting I/O to offline device
[99293.564696] sd 5:0:0:0: rejecting I/O to offline device
[99293.564724] sd 5:0:0:0: rejecting I/O to offline device
[99293.564758] sd 5:0:0:0: rejecting I/O to offline device
[99293.564781] sd 5:0:0:0: rejecting I/O to offline device
[99293.564789] sd 5:0:0:0: rejecting I/O to offline device
[99293.564798] sd 5:0:0:0: rejecting I/O to offline device
[99293.564808] sd 5:0:0:0: rejecting I/O to offline device
[99293.564821] sd 5:0:0:0: rejecting I/O to offline device
[99293.564832] sd 5:0:0:0: rejecting I/O to offline device
[99293.564843] sd 5:0:0:0: rejecting I/O to offline device
[99293.564853] sd 5:0:0:0: rejecting I/O to offline device
[99293.564862] sd 5:0:0:0: rejecting I/O to offline device
[99293.564871] sd 5:0:0:0: rejecting I/O to offline device
[99293.564880] sd 5:0:0:0: rejecting I/O to offline device
[99293.564891] sd 5:0:0:0: rejecting I/O to offline device
[99293.564900] sd 5:0:0:0: rejecting I/O to offline device
[99293.564910] sd 5:0:0:0: rejecting I/O to offline device
[99293.564920] sd 5:0:0:0: rejecting I/O to offline device
[99293.564929] sd 5:0:0:0: rejecting I/O to offline device
[99293.564939] sd 5:0:0:0: rejecting I/O to offline device
[99293.564948] sd 5:0:0:0: rejecting I/O to offline device
[99293.564957] sd 5:0:0:0: rejecting I/O to offline device
[99293.564966] sd 5:0:0:0: rejecting I/O to offline device
[99293.564976] sd 5:0:0:0: rejecting I/O to offline device
[99293.564984] sd 5:0:0:0: rejecting I/O to offline device
[99293.564993] sd 5:0:0:0: rejecting I/O to offline device
[99293.565002] sd 5:0:0:0: rejecting I/O to offline device
[99293.565012] sd 5:0:0:0: rejecting I/O to offline device
[99293.565021] sd 5:0:0:0: rejecting I/O to offline device
[99293.565030] sd 5:0:0:0: rejecting I/O to offline device
[99293.565039] sd 5:0:0:0: rejecting I/O to offline device
[99293.565049] sd 5:0:0:0: rejecting I/O to offline device
[99293.565060] sd 5:0:0:0: rejecting I/O to offline device
[99293.565070] sd 5:0:0:0: rejecting I/O to offline device
[99293.565079] sd 5:0:0:0: rejecting I/O to offline device
[99293.565089] sd 5:0:0:0: rejecting I/O to offline device
[99293.565098] sd 5:0:0:0: rejecting I/O to offline device
[99293.565107] sd 5:0:0:0: rejecting I/O to offline device
[99293.565117] sd 5:0:0:0: rejecting I/O to offline device
[99293.565127] sd 5:0:0:0: rejecting I/O to offline device
[99293.565137] sd 5:0:0:0: rejecting I/O to offline device
[99293.565147] sd 5:0:0:0: rejecting I/O to offline device
[99293.565156] sd 5:0:0:0: rejecting I/O to offline device
[99293.565167] sd 5:0:0:0: rejecting I/O to offline device
[99293.565176] sd 5:0:0:0: rejecting I/O to offline device
[99293.565185] sd 5:0:0:0: rejecting I/O to offline device
[99293.565196] sd 5:0:0:0: rejecting I/O to offline device
[99293.565205] sd 5:0:0:0: rejecting I/O to offline device
[99293.565214] sd 5:0:0:0: rejecting I/O to offline device
[99293.565223] sd 5:0:0:0: rejecting I/O to offline device
[99293.565234] sd 5:0:0:0: rejecting I/O to offline device
[99293.565243] sd 5:0:0:0: rejecting I/O to offline device
[99293.565252] sd 5:0:0:0: rejecting I/O to offline device
[99293.565263] sd 5:0:0:0: rejecting I/O to offline device
[99293.565272] sd 5:0:0:0: rejecting I/O to offline device
[99293.565281] sd 5:0:0:0: rejecting I/O to offline device
[99293.565290] sd 5:0:0:0: rejecting I/O to offline device
[99293.565300] sd 5:0:0:0: rejecting I/O to offline device
[99293.565309] sd 5:0:0:0: rejecting I/O to offline device
[99293.565320] sd 5:0:0:0: rejecting I/O to offline device
[99293.565329] sd 5:0:0:0: rejecting I/O to offline device
[99293.565338] sd 5:0:0:0: rejecting I/O to offline device
[99293.565347] sd 5:0:0:0: rejecting I/O to offline device
[99293.565356] sd 5:0:0:0: rejecting I/O to offline device
[99293.565365] sd 5:0:0:0: rejecting I/O to offline device
[99293.565374] sd 5:0:0:0: rejecting I/O to offline device
[99293.565384] sd 5:0:0:0: rejecting I/O to offline device
[99293.565393] sd 5:0:0:0: rejecting I/O to offline device
[99293.565402] sd 5:0:0:0: rejecting I/O to offline device
[99293.565413] sd 5:0:0:0: rejecting I/O to offline device
[99293.565422] sd 5:0:0:0: rejecting I/O to offline device
[99293.565433] sd 5:0:0:0: rejecting I/O to offline device
[99293.565443] sd 5:0:0:0: rejecting I/O to offline device
[99293.565454] sd 5:0:0:0: rejecting I/O to offline device
[99293.565464] sd 5:0:0:0: rejecting I/O to offline device
[99293.565475] sd 5:0:0:0: rejecting I/O to offline device
[99293.565484] sd 5:0:0:0: rejecting I/O to offline device
[99293.565494] sd 5:0:0:0: rejecting I/O to offline device
[99293.565525] sd 5:0:0:0: rejecting I/O to offline device
[99293.565543] sd 5:0:0:0: rejecting I/O to offline device
[99293.565594] sd 5:0:0:0: rejecting I/O to offline device
[99293.565603] sd 5:0:0:0: rejecting I/O to offline device
[99293.565612] sd 5:0:0:0: rejecting I/O to offline device
[99293.565622] sd 5:0:0:0: rejecting I/O to offline device
[99293.565636] sd 5:0:0:0: [sdb] Unhandled error code
[99293.565641] sd 5:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[99293.565650] end_request: I/O error, dev sdb, sector 8263
[99293.565657] Buffer I/O error on device sdb1, logical block 1025
[99293.565662] lost page write due to I/O error on sdb1
[99293.565670] Buffer I/O error on device sdb1, logical block 1026
[99293.565675] lost page write due to I/O error on sdb1
[99293.565682] Buffer I/O error on device sdb1, logical block 1027
[99293.565688] lost page write due to I/O error on sdb1
[99293.565764] sd 5:0:0:0: rejecting I/O to offline device
[99293.565780] sd 5:0:0:0: rejecting I/O to offline device
[99293.565789] sd 5:0:0:0: rejecting I/O to offline device
[99293.565814] sd 5:0:0:0: rejecting I/O to offline device
[99293.565824] sd 5:0:0:0: rejecting I/O to offline device
[99293.565832] sd 5:0:0:0: rejecting I/O to offline device
[99293.565856] sd 5:0:0:0: rejecting I/O to offline device
[99293.565866] sd 5:0:0:0: rejecting I/O to offline device
[99293.565874] sd 5:0:0:0: rejecting I/O to offline device
[99293.565897] sd 5:0:0:0: rejecting I/O to offline device
[99293.565907] sd 5:0:0:0: rejecting I/O to offline device
[99293.565916] sd 5:0:0:0: rejecting I/O to offline device
[99293.566086] sd 5:0:0:0: rejecting I/O to offline device
[99293.566097] sd 5:0:0:0: rejecting I/O to offline device
[99293.566106] sd 5:0:0:0: rejecting I/O to offline device
[99293.566130] sd 5:0:0:0: rejecting I/O to offline device
[99293.566139] sd 5:0:0:0: rejecting I/O to offline device
[99293.566148] sd 5:0:0:0: rejecting I/O to offline device
[99293.566171] sd 5:0:0:0: rejecting I/O to offline device
[99293.566181] sd 5:0:0:0: rejecting I/O to offline device
[99293.566189] sd 5:0:0:0: rejecting I/O to offline device
[99293.566297] sd 5:0:0:0: rejecting I/O to offline device
[99293.566334] sd 5:0:0:0: rejecting I/O to offline device
[99293.566350] sd 5:0:0:0: rejecting I/O to offline device
[99293.566462] sd 5:0:0:0: rejecting I/O to offline device
[99293.566504] sd 5:0:0:0: rejecting I/O to offline device
[99293.566519] sd 5:0:0:0: rejecting I/O to offline device
[99293.566695] sd 5:0:0:0: rejecting I/O to offline device
[99293.566737] sd 5:0:0:0: rejecting I/O to offline device
[99293.566778] sd 5:0:0:0: rejecting I/O to offline device
[99293.566904] sd 5:0:0:0: rejecting I/O to offline device
[99293.566945] sd 5:0:0:0: rejecting I/O to offline device
[99293.566961] sd 5:0:0:0: rejecting I/O to offline device
[99293.566985] sd 5:0:0:0: rejecting I/O to offline device
[99293.566995] sd 5:0:0:0: rejecting I/O to offline device
[99293.567003] sd 5:0:0:0: rejecting I/O to offline device
[99293.567047] sd 5:0:0:0: rejecting I/O to offline device
[99293.567058] sd 5:0:0:0: rejecting I/O to offline device
[99293.567067] sd 5:0:0:0: rejecting I/O to offline device
[99293.567090] sd 5:0:0:0: rejecting I/O to offline device
[99293.567099] sd 5:0:0:0: rejecting I/O to offline device
[99293.567108] sd 5:0:0:0: rejecting I/O to offline device
[99293.567131] sd 5:0:0:0: rejecting I/O to offline device
[99293.567140] sd 5:0:0:0: rejecting I/O to offline device
[99293.567149] sd 5:0:0:0: rejecting I/O to offline device
[99293.567172] sd 5:0:0:0: rejecting I/O to offline device
[99293.567182] sd 5:0:0:0: rejecting I/O to offline device
[99293.567190] sd 5:0:0:0: rejecting I/O to offline device
[99293.567213] sd 5:0:0:0: rejecting I/O to offline device
[99293.567223] sd 5:0:0:0: rejecting I/O to offline device
[99293.567232] sd 5:0:0:0: rejecting I/O to offline device
[99293.567268] sd 5:0:0:0: rejecting I/O to offline device
[99293.567278] sd 5:0:0:0: rejecting I/O to offline device
[99293.567287] sd 5:0:0:0: rejecting I/O to offline device
[99293.567310] sd 5:0:0:0: rejecting I/O to offline device
[99293.567320] sd 5:0:0:0: rejecting I/O to offline device
[99293.567328] sd 5:0:0:0: rejecting I/O to offline device
[99293.567351] sd 5:0:0:0: rejecting I/O to offline device
[99293.567361] sd 5:0:0:0: rejecting I/O to offline device
[99293.567370] sd 5:0:0:0: rejecting I/O to offline device
[99293.567393] sd 5:0:0:0: rejecting I/O to offline device
[99293.567402] sd 5:0:0:0: rejecting I/O to offline device
[99293.567411] sd 5:0:0:0: rejecting I/O to offline device
[99293.567449] sd 5:0:0:0: rejecting I/O to offline device
[99293.567460] sd 5:0:0:0: rejecting I/O to offline device
[99293.567473] sd 5:0:0:0: rejecting I/O to offline device
[99293.567588] sd 5:0:0:0: rejecting I/O to offline device
[99293.567622] sd 5:0:0:0: rejecting I/O to offline device
[99293.567644] sd 5:0:0:0: rejecting I/O to offline device
[99293.567680] sd 5:0:0:0: rejecting I/O to offline device
[99293.567695] sd 5:0:0:0: rejecting I/O to offline device
[99293.567703] sd 5:0:0:0: rejecting I/O to offline device
[99293.567785] sd 5:0:0:0: rejecting I/O to offline device
[99293.567798] sd 5:0:0:0: rejecting I/O to offline device
[99293.567819] sd 5:0:0:0: rejecting I/O to offline device
[99293.567845] sd 5:0:0:0: rejecting I/O to offline device
[99293.567856] sd 5:0:0:0: rejecting I/O to offline device
[99293.567865] sd 5:0:0:0: rejecting I/O to offline device
[99293.567888] sd 5:0:0:0: rejecting I/O to offline device
[99293.567898] sd 5:0:0:0: rejecting I/O to offline device
[99293.567907] sd 5:0:0:0: rejecting I/O to offline device
[99293.567930] sd 5:0:0:0: rejecting I/O to offline device
[99293.567940] sd 5:0:0:0: rejecting I/O to offline device
[99293.567948] sd 5:0:0:0: rejecting I/O to offline device
[99293.567971] sd 5:0:0:0: rejecting I/O to offline device
[99293.567981] sd 5:0:0:0: rejecting I/O to offline device
[99293.567990] sd 5:0:0:0: rejecting I/O to offline device
[99293.568070] usb 1-3: USB disconnect, address 10
[99293.569077] JBD: Failed to read block at offset 17914
[99293.569081] JBD: IO error -5 recovering block 17914 in log
[99293.569092] JBD: Failed to read block at offset 17915
[99293.569095] JBD: IO error -5 recovering block 17915 in log
[99293.569098] JBD: Failed to read block at offset 17916
[99293.569100] JBD: IO error -5 recovering block 17916 in log
[99293.569103] JBD: Failed to read block at offset 17917
[99293.569105] JBD: IO error -5 recovering block 17917 in log
[99293.569108] JBD: Failed to read block at offset 17918
[99293.569111] JBD: IO error -5 recovering block 17918 in log
[99293.569114] JBD: Failed to read block at offset 17919
[99293.569116] JBD: IO error -5 recovering block 17919 in log
[99293.569119] JBD: Failed to read block at offset 17920
[99293.569121] JBD: IO error -5 recovering block 17920 in log
[99293.569124] JBD: Failed to read block at offset 17921
[99293.569126] JBD: IO error -5 recovering block 17921 in log
[99293.569129] JBD: Failed to read block at offset 17922
[99293.569131] JBD: IO error -5 recovering block 17922 in log
[99293.569134] JBD: Failed to read block at offset 17923
[99293.569137] JBD: IO error -5 recovering block 17923 in log
[99293.569140] JBD: Failed to read block at offset 17924
[99293.569142] JBD: IO error -5 recovering block 17924 in log
[99293.569145] JBD: Failed to read block at offset 17925
[99293.569147] JBD: IO error -5 recovering block 17925 in log
[99293.569150] JBD: Failed to read block at offset 17926
[99293.569152] JBD: IO error -5 recovering block 17926 in log
[99293.569155] JBD: Failed to read block at offset 17927
[99293.569158] JBD: IO error -5 recovering block 17927 in log
[99293.569160] JBD: Failed to read block at offset 17928
[99293.569163] JBD: IO error -5 recovering block 17928 in log
[99293.569166] JBD: Failed to read block at offset 17929
[99293.569168] JBD: IO error -5 recovering block 17929 in log
[99293.569171] JBD: Failed to read block at offset 17930
[99293.569173] JBD: IO error -5 recovering block 17930 in log
[99293.569176] JBD: Failed to read block at offset 17931
[99293.569179] JBD: IO error -5 recovering block 17931 in log
[99293.569182] JBD: Failed to read block at offset 17932
[99293.569184] JBD: IO error -5 recovering block 17932 in log
[99293.569187] JBD: Failed to read block at offset 17933
[99293.569189] JBD: IO error -5 recovering block 17933 in log
[99293.569192] JBD: Failed to read block at offset 17934
[99293.569194] JBD: IO error -5 recovering block 17934 in log
[99293.569197] JBD: Failed to read block at offset 17935
[99293.569200] JBD: IO error -5 recovering block 17935 in log
[99293.569202] JBD: Failed to read block at offset 17936
[99293.569205] JBD: IO error -5 recovering block 17936 in log
[99293.569208] JBD: Failed to read block at offset 17937
[99293.569210] JBD: IO error -5 recovering block 17937 in log
[99293.569213] JBD: Failed to read block at offset 17938
[99293.569215] JBD: IO error -5 recovering block 17938 in log
[99293.569218] JBD: Failed to read block at offset 17939
[99293.569220] JBD: IO error -5 recovering block 17939 in log
[99293.637203] JBD: recovery failed
[99293.637209] EXT3-fs: error loading journal.
[99293.803092] usb 1-3: new high speed USB device using ehci_hcd and address 11
[99308.912055] usb 1-3: device descriptor read/64, error -110
[99324.128151] usb 1-3: device descriptor read/64, error -110
[99324.344050] usb 1-3: new high speed USB device using ehci_hcd and address 12
[99339.468062] usb 1-3: device descriptor read/64, error -110
[99354.684532] usb 1-3: device descriptor read/64, error -110
[99354.900061] usb 1-3: new high speed USB device using ehci_hcd and address 13
[99354.932305] usb 1-3: device descriptor read/8, error -71
[99355.064300] usb 1-3: device descriptor read/8, error -71
[99355.280055] usb 1-3: new high speed USB device using ehci_hcd and address 14
[99355.312310] usb 1-3: device descriptor read/8, error -71
[99355.444308] usb 1-3: device descriptor read/8, error -71
[99355.548067] hub 1-0:1.0: unable to enumerate USB device on port 3
[99355.816057] usb 3-1: new full speed USB device using uhci_hcd and address 7
[99370.928059] usb 3-1: device descriptor read/64, error -110
[99386.152036] usb 3-1: device descriptor read/64, error -110
[99386.372067] usb 3-1: new full speed USB device using uhci_hcd and address 8
[99401.484047] usb 3-1: device descriptor read/64, error -110
[99416.700046] usb 3-1: device descriptor read/64, error -110
[99416.916057] usb 3-1: new full speed USB device using uhci_hcd and address 9
[99416.947085] usb 3-1: device descriptor read/8, error -71
[99417.075086] usb 3-1: device descriptor read/8, error -71
[99417.288059] usb 3-1: new full speed USB device using uhci_hcd and address 10
[99417.319155] usb 3-1: device descriptor read/8, error -71
[99417.447088] usb 3-1: device descriptor read/8, error -71
[99417.548068] hub 3-0:1.0: unable to enumerate USB device on port 1
phillip@phillip-laptop:~$

---

### Post by Hatchetz on 2012-09-09
I am having this problem too...


> steven@Steven:~$ sudo mount -t vfat /dev/sdc1 /media
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
* * * *missing codepage or helper program, or other error
* * * *In some cases useful info is found in syslog - try
* * * *dmesg | tail *or so



> steven@Steven:~$ dmesg | tail
[ 1032.431704]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1032.431723]         3a 07 cb be 
[ 1032.431731] sd 2:0:0:0: [sdc]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 1032.431742] sd 2:0:0:0: [sdc] CDB: Read(10): 28 00 3a 07 cb b8 00 00 08 00
[ 1032.431760] end_request: I/O error, dev sdc, sector 973589438
[ 1032.431792] ata3: EH complete
[ 1050.402437] FAT-fs (sdc1): bogus number of reserved sectors
[ 1050.402448] FAT-fs (sdc1): Can't find a valid FAT filesystem
[ 1079.150197] FAT-fs (sdc1): bogus number of reserved sectors
[ 1079.150210] FAT-fs (sdc1): Can't find a valid FAT filesystem



> steven@Steven:~$ dmesg | tail
[ 2022.041802] sd 2:0:0:0: [sdc] Unhandled sense code
[ 2022.041808] sd 2:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2022.041816] sd 2:0:0:0: [sdc]  Sense Key : Medium Error [current] [descriptor]
[ 2022.041826] Descriptor sense data with sense descriptors (in hex):
[ 2022.041831]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2022.041850]         3a 07 cb be 
[ 2022.041858] sd 2:0:0:0: [sdc]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 2022.041869] sd 2:0:0:0: [sdc] CDB: Read(10): 28 00 3a 07 cb b8 00 00 08 00
[ 2022.041887] end_request: I/O error, dev sdc, sector 973589438
[ 2022.041934] ata3: EH complete
steven@Steven:~$ dmesg | tail
[ 2022.041802] sd 2:0:0:0: [sdc] Unhandled sense code
[ 2022.041808] sd 2:0:0:0: [sdc]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2022.041816] sd 2:0:0:0: [sdc]  Sense Key : Medium Error [current] [descriptor]
[ 2022.041826] Descriptor sense data with sense descriptors (in hex):
[ 2022.041831]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2022.041850]         3a 07 cb be 
[ 2022.041858] sd 2:0:0:0: [sdc]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 2022.041869] sd 2:0:0:0: [sdc] CDB: Read(10): 28 00 3a 07 cb b8 00 00 08 00
[ 2022.041887] end_request: I/O error, dev sdc, sector 973589438
[ 2022.041934] ata3: EH complete

---

