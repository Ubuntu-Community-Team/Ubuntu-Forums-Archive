---
title: "Where is it mounted?"
date: 2011-10-25
forum: General Help
---

### Post by magnetsixdeuce on 2011-10-25
So Ubuntu 11.10 automounts just about everything i stick in a USB port.

From the commandline, i want to see what the device is mounted as and ls or cp or whatever files on/from it.. and unmount it.

i think gvfs is sort of messing up what i am used to.

when i put a cdrom in the drive i would expect that it would be mounted as /dev/cdrom.. or /dev/sd0 or something like it used to be years ago.. and accessible at /media/cdrom. This does not seem to be the case currently.

If i look in /etc/mtab or execute "mount" nothing resembling a cdrom is listed. I do see a "gvfs-fuse-daemon /home/ubuntu/.gvfs " which is where its looking like the cd is mounted.. in a strange little directory in my user home dir under .gvfs/somecrazyname

I can "wodim --devices" to show me that the cdrom device is "/dev/sg0"

but i cant "umount /dev/sg0" mtab says its not mounted.

What gives? seems awfully weird.

---

### Post by garvinrick4 on 2011-10-25
USB's will mount in /media
```
cd /media
```Cd
```
eject /dev/sr0
```

---

### Post by magnetsixdeuce on 2011-10-26
Thanks..

If i wanted to umount /dev/sr0.. so it does not eject it out from the box.. it says its not mounted.. how do i do it without using the eject command

---

### Post by magnetsixdeuce on 2011-10-26
ok.. let me rephrase that.

I have a cdrom.. i want to make a .iso file of it.

what is the cdrom device that i can dd from?
/dev/sr0? /dev/sg0? /dev/cdrom?

I get input output errors from all of those.

I try to umount all of those and they dont exist or are not mounted (even with the gui showing an audo disc in the drive).

dd if=/dev/? of=cdcopy.iso

---

### Post by garvinrick4 on 2011-10-26
#Look in /media for mounted volumes.
/dev/sr0 /media/blah_blah_blah

---

### Post by magnetsixdeuce on 2011-10-26
ok.. did some research... Ubuntu 11.10.. default install

Experiment #1:
With a music cd in the drive.

Nothing shows up in dmesg.

It mounts it "$HOME/.gvfs/cdda mount on sr0" not /cdrom or /media/nameofcd

It does not show up as an entry in mtab. When you try to umount /dev/sr0.. no deals .. mtab says its not mounted.

If you try to "dd" it, the following is displayed to stdout.

```
bubba@big-laptop:~$ sudo dd if=/dev/sr0 of=test1.iso
[sudo] password for bubba: 
dd: reading `/dev/sr0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00580946 s, 0.0 kB/s
```

This is what shows up in dmesg from the dd
```
[  525.755213] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  525.755224] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  525.755234] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[  525.755247] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  525.755268] end_request: I/O error, dev sr0, sector 0
[  525.755276] quiet_error: 12 callbacks suppressed
[  525.755281] Buffer I/O error on device sr0, logical block 0
[  525.755292] Buffer I/O error on device sr0, logical block 1
[  525.755298] Buffer I/O error on device sr0, logical block 2
[  525.755303] Buffer I/O error on device sr0, logical block 3
[  525.758201] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  525.758209] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  525.758218] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[  525.758229] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  525.758248] end_request: I/O error, dev sr0, sector 0
[  525.758254] Buffer I/O error on device sr0, logical block 0
```



When you put a data cd in the drive.

This is what shows up in dmesg.
```
[  616.624727] ISO 9660 Extensions: Microsoft Joliet Level 3
[  616.668664] ISO 9660 Extensions: RRIP_1991A
```

It mounts it in /media/nameofcd not in /cdrom or "$home/.gvfs/nameofcd"

It does show up as an entry in mtab. When you try to umount /dev/sr0 it works.  

When you try to 'dd" it. It works.. the following goes to stdout.
```
bubba@bubba-big-laptop:~$ sudo dd if=/dev/sr0 of=test2.iso
391768+0 records in
391768+0 records out
200585216 bytes (201 MB) copied, 100.46 s, 2.0 MB/s
bubba@bubba-big-laptop:~$ 
```

So my theory is that copyright protection somehow prohibits me from creating an .iso file from my Buck Owens Greatest Hits cd.

I am going to mark this as solved and put it on the back burner.

---

