---
title: "DVD video not recognized"
date: 2012-09-04
forum: General Help
---

### Post by joakes90 on 2012-09-04
Hey, so this may be a little long and drawn out but i've done some lurking and some googling and can quite find the source of my issue. So what's going on is my machine is not recognizing any commercial DVD videos. I have tested out a few data dvds and they mount with no issue. i know that i have been able to mount DVD videos in the past and get the video_ts and audio_ts folders to appear on this install. the issue first appeared when trying to rip a few dvds I have laying around the house using dd. when i did this i got an io error saying that the copy failed. so i tried to unmount the drive and just used umounr /dev/sr0. After unmounting the disk dd just returns with the same error ```
dd: reading `/dev/sr0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00725333 s, 0.0 kB/s

``` but with the exception that this is reporting 0b copied when before it would report a minuscule amount, usually less ~20 MB.
so naturally I tried to remount but it just told me ```
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
``` so i then tried to reboot to see if it would recognize the dvd again, but no such luck.
so the trouble shooting steps i took from there where i tried swapping out the disk with another moviebut  it behaved the same. i attempted to play the disk in both VLC and Mplayer. VLC returned with ```
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details[/COLOR]

``` i put in an OS X install dvd to see if it would mount and it appeared in the side bar of nautilus almost instantly and showed the boot camp install .exe. im not quite sure why it just doesn’t like these specific kinds of disks. 
more info that might be helpful is im running 12.04 on an asus U46-E
the the info returned form lshw for this drive is ```
 *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ892AS
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 1.00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```and i ran region set to verify it is still set to region 1 (in the US) and it is ```
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE
```also I cleared dmesg and tried to see if it listed anything after inserting a disk. it listed nothing and the same was true trying to run dd on it again but i was able to get this after attempting to play the disk in VLC ```
[ 5345.734191] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[ 5345.734204] sr: Sense Key : Hardware Error [current] 
[ 5345.734207] sr: Add. Sense: Tracking servo failure
[ 5345.739608] sr 2:0:0:0: [sr0] Unhandled sense code
[ 5345.739613] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5345.739618] sr 2:0:0:0: [sr0]  Sense Key : Hardware Error [current] 
[ 5345.739623] sr 2:0:0:0: [sr0]  Add. Sense: Tracking servo failure
[ 5345.739627] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 00 00 00 02 00
[ 5345.739642] end_request: I/O error, dev sr0, sector 1024
[ 5345.739645] quiet_error: 136 callbacks suppressed
[ 5345.739647] Buffer I/O error on device sr0, logical block 128
[ 5345.742911] sr 2:0:0:0: [sr0] Unhandled sense code
[ 5345.742914] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5345.742918] sr 2:0:0:0: [sr0]  Sense Key : Hardware Error [current] 
[ 5345.742921] sr 2:0:0:0: [sr0]  Add. Sense: Tracking servo failure
[ 5345.742925] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 00 00 00 02 00
[ 5345.742933] end_request: I/O error, dev sr0, sector 1024
[ 5345.742937] Buffer I/O error on device sr0, logical block 128
[ 5345.764030] sr0: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[ 5345.764041] sr: Sense Key : Hardware Error [current] 
[ 5345.764044] sr: Add. Sense: Tracking servo failure
[ 5345.769401] sr 2:0:0:0: [sr0] Unhandled sense code
[ 5345.769404] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5345.769407] sr 2:0:0:0: [sr0]  Sense Key : Hardware Error [current] 
[ 5345.769411] sr 2:0:0:0: [sr0]  Add. Sense: Tracking servo failure
[ 5345.769414] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 00 00 00 02 00
[ 5345.769420] end_request: I/O error, dev sr0, sector 1024
[ 5345.769425] Buffer I/O error on device sr0, logical block 128
[ 5345.772658] sr 2:0:0:0: [sr0] Unhandled sense code
[ 5345.772661] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 5345.772664] sr 2:0:0:0: [sr0]  Sense Key : Hardware Error [current] 
[ 5345.772667] sr 2:0:0:0: [sr0]  Add. Sense: Tracking servo failure
[ 5345.772671] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 00 00 00 02 00
[ 5345.772678] end_request: I/O error, dev sr0, sector 1024
[ 5345.772682] Buffer I/O error on device sr0, logical block 128
justin@justin-U46E:~$ 

```sorry if this is all a bit much but i tried to provide as much information as I could. i it seams the do the same on both newer and fairly old DVDs

---

### Post by SeijiSensei on 2012-09-04
You need to add the "restricted extras" package for your distribution:

```
sudo apt-get install ubuntu-restricted-extras
```

If you use a different flavor like Kubuntu or Lubuntu, replace "ubuntu" above with the appropriate name.

Even with restricted extras installed, you cannot use dd to copy a commercial DVD.  Most of the burning software can do so though.  I know the KDE burner, K3b, can do so.

---

