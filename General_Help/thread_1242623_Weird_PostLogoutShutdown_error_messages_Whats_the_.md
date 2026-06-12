---
title: "Weird PostLogout/Shutdown error messages? Whats the issue?"
date: 2009-08-17
forum: General Help
---

### Post by harry2006 on 2009-08-17
I got my brand new dell studio 1555 2 weeks back. It's having Vista and on a new unused partition I installed Ubuntu9.04-32 bit. Everything was working fine but to make use of available 4 gig RAM I installed the 32-bit server version 5/6 days ago. From last two days I'm facing some weird messages after i click shutdown...it starts shutting down and then It gives these messages.. I just noted down some of them and these are:

<code>
CPU0 - attaching NULL sched-domain
CPU1 - attaching NULL sched-domain
CPU0 - attaching NULL sched-domain

......

iwlagn: error sending
ata1: failed to identify (I/O error mask=0x4)

hard resetting link
status line....
ext3-abort called
EXT3_fs error(device sda6) ext3_journal_statrt-sb: detected aborted journal

remounting filesystem read-only.....

<something which i couldn't note>

JBD: detected IO error while flushing file data on sda6
sd 0:0:0:0: [sda] Result: hostbyte:=DID_BAD_TARGET drivertype=DRIVER_OK, SUGGEST_OK

end request: I/O error, dev sda, sector# <some number>
Journal count I/O error...

<the next line keeps repeating many many times with different sector nubers>
end request: I/O error, dev sda, sector# <some number>
</code>
and then system gets stuck there for 10/15 mins and I've to manually restart/shutdown .

As far as the system is concerned I thought there might be something wrong with my hard disk and did a check for badblocks on Windows section and it passed without any warnings...and then i did the same for Ubuntu using "badblock" and it said no badblocks found... i tried usign fsck and it gave warning " running this on mounted file sys may corrupt the filesys" so i dint run that...

Googling led me to some odl mail-archives but no solution but got some pic taken by someone here:
[http://folk.uio.no/vegardno/DSCF2543.JPG](http://folk.uio.no/vegardno/DSCF2543.JPG)
which has more less some part of the error messages I'm getting...

Can someone plz help me out? What exactly is the issue? How to fix that? I'm bit worried if that says I've some bad sectors on my new disk. BTW I've 320 hdd [WDC WD32000BJKT-75F4T0, i got this from device manager in vista] and using 26GB for Ubuntu. Please let me know if I need to put some more information. Any help/advice is highly appreciated. Thank you.

---

### Post by harry2006 on 2009-08-19
bump!!!
i even tried running badblocks which gave the output

ubuntu@ubuntu:~$ sudo badblocks -o badblock -v /dev/sda6
Checking blocks 0 to 27374727
Checking for bad blocks (read-only test): done                                
Pass completed, 0 bad blocks found.

and then run fsck which gave this:
ubuntu@ubuntu:~$ sudo fsck -n -v /dev/sda6 
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda6: clean, 181868/1712128 files, 3206342/6843682 blocks

I ran all this thru 8.10LiveCD.
Can someone please help me fix the issue? After running the above two tests I'm kinda sure there is no issue related to BadSector/BadBlocks and its something else and m kinda relieved as I got this brand new sys just couple of weeks back...But everytime I shutdown my system, I starts showing those error messages and kind of gets stuck and I've to manually power it down by pressing the power button. Please help me fix this, its really annoying me . Thank you.

---

