---
title: "cd -&gt; .iso"
date: 2011-10-23
forum: General Help
---

### Post by magnetsixdeuce on 2011-10-23
Hi
I am trying to back up my cd's to .iso files

I am using Ubuntu 11.10

acetoneiso, Brasero etc dont have options to create a .iso file

when i try readom..

```
bubba@big-laptop:~$ readom dev=/dev/cdrom f=Disk_1.iso
Read  speed:  4234 kB/s (CD  24x, DVD  3x).
Write speed:  4234 kB/s (CD  24x, DVD  3x).
Capacity: 226120 Blocks = 452240 kBytes = 441 MBytes = 463 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (0,0,0) disk to file 'Disk_1.iso'
end:    226120
Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 00 00 00 00 80 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s
readom: Input/output error. Cannot read source disk
readom: Retrying from sector 0.
.~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readom: Input/output error. Error on sector 0 not corrected. Total of 1 errors.
Time total: 0.389sec
Read 0.00 kB at 0.0 kB/sec.
Max corected retry count was 0 (limited to 128).
The following 1 sector(s) could not be read correctly:
0
bubba@big-laptop:~$ 

```

I dont want to use dd because there isnt any error checking..

do i have any other options?

i used to be able to do this.. whats up?

Thanks!

---

### Post by satanselbow on 2011-10-23
Looks like the disc you are trying to copy is in poor condition - dirty / scratched :(

---

### Post by maniandram on 2011-10-23
Doesn't Brasero have a option to rip the the disc (Make it into a .iso file) .
In K3b, press "more options" and go to Rip * disc or go to tools>Rip * disc

---

### Post by magnetsixdeuce on 2011-10-23
> **maniandram said:**
> Doesn't Brasero have a option to rip the the disc (Make it into a .iso file) .
In K3b, press "more options" and go to Rip * disc or go to tools>Rip * disc

With Brasero, under the "Copy CD/DVD" icon, you can "select a disk to write to"... which would be an image file. But, it only gives you "Readcd/Readom image" which lists .toc format, cue image which is .cue format and cdrdao image.. which is .toc format also.

no .iso

I thought i was missing something.. i made sure that brasero-cdrkit was installed, it was... but no obvious way to copy a cd to .iso using Brasero.

I will mess around with K3B some more and see what i can come up with..

---

### Post by oldtimer7777 on 2011-10-23
Brasero makes great image files.   

Select Disk Copy.

Use the drop down with "Select a disc to write to" and change it to image instead.


> **magnetsixdeuce said:**
> With Brasero, under the "Copy CD/DVD" icon, you can "select a disk to write to"... which would be an image file. But, it only gives you "Readcd/Readom image" which lists .toc format, cue image which is .cue format and cdrdao image.. which is .toc format also.

no .iso

I thought i was missing something.. i made sure that brasero-cdrkit was installed, it was... but no obvious way to copy a cd to .iso using Brasero.

I will mess around with K3B some more and see what i can come up with..

---

### Post by magnetsixdeuce on 2011-10-23
> **oldtimer7777 said:**
> Brasero makes great image files.   

Select Disk Copy.

Use the drop down with "Select a disc to write to" and change it to image instead.

Yeah.. as far as i can tell.. that is not a .iso

---

### Post by oldtimer7777 on 2011-10-23
> **magnetsixdeuce said:**
> Yeah.. as far as i can tell.. that is not a .iso

It is an ISO and I make them daily with Brasero on my Ubuntu 11.10 system. 


Select Disk Copy.

Use the drop down with "Select a disc to write to" and change it to image instead.

Try it, and screenshot the file properties of the image it creates so we can verify what you are saying.

---

### Post by magnetsixdeuce on 2011-10-23
Its looking like K3B will give me a .img .. which isnt a .iso .. i would have to convert that with ccd2iso.
I can create a .cue file with Brasero.. which isnt a .iso  i could convert that with bchunk?

I tried multiple cd's with the readom command.. all give the same error message.. i am thinking it has to do with copyright?

I am still looking.

---

### Post by oldtimer7777 on 2011-10-23
I didn't say use K3B..  Use Brasero.   Follow my instructions if you want an ISO file.  Thanks.

> **magnetsixdeuce said:**
> Its looking like K3B will give me a .img .. which isnt a .iso .. i would have to convert that with ccd2iso.
I can create a .cue file with Brasero.. which isnt a .iso  i could convert that with bchunk?

I tried multiple cd's with the readom command.. all give the same error message.. i am thinking it has to do with copyright?

I am still looking.

---

### Post by magnetsixdeuce on 2011-10-24
Brasero.. 3 options for writing to "image file"

Readcd/Readom, Cue, Cdrdao

I am running Brasero 3.2.0 on Ubuntu 11.10

---

### Post by magnetsixdeuce on 2011-10-24
> **oldtimer7777 said:**
> I didn't say use K3B.. 

I was responding to maniandram about the K3B

---

### Post by emiller12345 on 2011-10-24
ddrescue is a great tool. theres a howto here...

[http://www.howtogeek.com/howto/21876/rescue-old-damaged-cds-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/21876/rescue-old-damaged-cds-with-an-ubuntu-live-cd/)

---

### Post by oldtimer7777 on 2011-10-24
> **magnetsixdeuce said:**
> Brasero.. 3 options for writing to "image file"

Readcd/Readom, Cue, Cdrdao

I am running Brasero 3.2.0 on Ubuntu 11.10

I don't think you have installed everything you need to do what you are attempting to do with your system. Try using a walkthrough guide and go step by step to make sure you have all the packages you need to make the kind of image file you wish to create with Brasero and K3B.  I can make them just fine after installing everyone on this list:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by xianbei on 2011-10-24
image writer is the best tool i know for live cds. dunno if that's exactly what you're looking for, but it fits the topic of discussion.

to install (as long as you're later than 9.04):

```
sudo apt-get install usb-imagewriter
```

be sure you run it as sudo, or it will crash

bt dub, i got this from
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

recently when making a MeeGo boot USB. very nice interface, let's hope Tizen lives up to it and more!

---

### Post by oldtimer7777 on 2011-10-24
> **xianbei said:**
> image writer is the best tool i know for live cds. dunno if that's exactly what you're looking for, but it fits the topic of discussion.

to install (as long as you're later than 9.04):

```
sudo apt-get install usb-imagewriter
```be sure you run it as sudo, or it will crash

bt dub, i got this from
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

recently when making a MeeGo boot USB. very nice interface, let's hope Tizen lives up to it and more!

Well originally they were trying to make a *.iso image file. But they don't have the plugins for Brasero installed or something. That is why I posted a walkthrough. It looks like they may be missing some packages on their new installed Ubuntu system.

---

### Post by magnetsixdeuce on 2011-10-25
oldtimer7777 .. open up a terminal and "sudo dpkg -l bras*" post the results here please?

---

### Post by satanselbow on 2011-10-25
a picture pains a thousand toads

[IMG]http://i53.tinypic.com/258sarr.jpg[/IMG]

---

### Post by magnetsixdeuce on 2011-10-25
Ok.. 

1. Start up a virtual machine, the ubuntu 11.10 .iso as the boot image, 32 meg video, 3d acceleration, 2 gig ram, 2 processors, bridged ethernet to my dhcp network..
2. I attach the cddrive which has my "Buck Owens, All Time Greatest Hits" cd in it.
3. The audo disk icon shows up in my unity menu on the left.
4. I can click on it.. it opens the navigator, i can see all the .wav files. It gives me the icon "Open Banshee Media Player".. i select it.
5. Banshee opens
6. I select "Audio CD" from the menu on the left.. and selct the "Duplicate CD" icon at the top.
7. The Brasero Copy CD/DVD windo pops up.
8. Under "Select a disk to write to" i select image file.
9. It defaults to "Image File: "/home/ubuntu/Audio Disc.toc"
10. I select "properties", then "Disc Image type:"  it displays Cdrdao image, Cue Image, Readcd/Readom image.
11. For kicks i tried to select each one to see what extension is put on the filename. Cdrdao image and Readcd/Readom image are both .toc file extensions, Cue image is .cue extension.

I also tried to open Brasero directly, not through Banshee.. the only difference is that the filename is not populated automatically.. same file extension/types though..

So, out of the box.. default configuration, we show that Barasero does not create .iso files. You can create a file with a .iso extension.. but it actually is not a iso9660 file.

Lets change the original question a bit.
Is there a plugin or some other app that can make Brasero create .iso files? if so.. what specifically is it.

I am going to resort to "dd" to copy these cd's and experiment with "ddrescue" which sounds awesome.

---

### Post by oldtimer7777 on 2011-10-26
> **magnetsixdeuce said:**
> Ok.. 
but it actually is not a iso9660 file..

You want to convert a music cd into a data iso? 

That is all you needed to say.. :)

---

### Post by magnetsixdeuce on 2011-10-26
> **magnetsixdeuce said:**
> Hi
I am trying to back up my cd's to .iso files
Thanks!

Yup.

After more research i couldn't find anything.. maybe no one does stuff like that anymore.

Its sort of getting ridiculous..

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

### Post by oldtimer7777 on 2011-10-26
> **magnetsixdeuce said:**
> Yup.

After more research i couldn't find anything.. maybe no one does stuff like that anymore.

Its sort of getting ridiculous..

Nobody does this. I'm just saying.

---

### Post by wolfen69 on 2011-10-26
> **oldtimer7777 said:**
> Nobody does this. I'm just saying.

I just did yesterday because I needed an .iso but did not want to download it again. 

Btw, if your cd drive is sata, you need to make it /dev/scd0

---

### Post by oldtimer7777 on 2011-10-26
> **wolfen69 said:**
> I just did yesterday because I needed an .iso but did not want to download it again. 

Btw, if your cd drive is sata, you need to make it /dev/scd0

Why would you convert a Audio CD into a Data *.iso file?  Just out of our curiosity, what would be purpose of doing this?

There are hundreds of better ways to compress and convert Music CDs into thousands of other formats for archive or sharing...

It sounds like you are trying to spoof something, if you ask me.

---

