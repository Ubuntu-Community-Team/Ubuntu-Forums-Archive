---
title: "FileRecovery crash before finish, Foremost, Photorec"
date: 2010-11-20
forum: General Help
---

### Post by ironic.demise on 2010-11-20
I've recently came into an old HDD that was corrupted and lost all it's files.

Using Photorec and Foremost I've been able to get some of the files back (Mostly photos I don't have elsewhere).

Thing is, The pc always freezes before the file recovery finishes.

I've tried both photorec and foremost.

Each time it's ran it will recover various amounts, sometimes it will get up to family photos, other times it will crash with just restored rubbish.

I've tried quick mode, fails fairly quickly again.
I've tried several recoveries... failed again and again.
I've tried outputting the progress to a text file so I can see WHERE it crashed and I tried resuming from there, only it didn't start where it left off, I started it just a little from where it failed and though it ran for long enough to get several pictures it didn't recover the SAME photo that I knew was in front of where it started...

Am I right that using the -s argument you should put the number where "File offset" is in the Verbose output?

:edit:
The verbose output on the session using -s.
The file offset of files recovered were low numbers, it didn't start from where I told it to as far as I can tell.


:
File offset, the amount of read/writes to a file?
So File offset is the wrong digit to find?
File offset starts at "3121336320"

I assume that's very wrong, it's a 300gb hdd
that number means that the hdd is well over 300gb (3,121,336,320=3tb?)

---

### Post by ironic.demise on 2010-11-20
+1
If somebody could tell me either why it crashes my computer on every run
: or:
How to find the correct information to put into the -s (start the scan after N blocks) argument?


For some reason, it hasn't crash in the longest time yet from what I can tell...
All I'm doing differently is not leaving it to do it's thing and using the PC as I would usually.

---

### Post by ironic.demise on 2010-11-20
Hate to be impatient, I know how pointless that is around here.

Just throwing a bump up because the sooner this get's fixed the sooner I can clean install my computer.

---

### Post by ironic.demise on 2010-11-21
Will LiveCD solve this problem?

---

### Post by C.B.Leslie on 2011-01-02
Better late than never...

Instead of performing the recovery on the damaged device, you should image the damaged device with as many passes as your patience can handle.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Scroll down to "Imaging a damaged device, filesystem or drive", and read that section thoroughly to make sure you understand the rough concept of imaging a device.

---

