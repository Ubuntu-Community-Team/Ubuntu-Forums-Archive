---
title: "16GB flash drive won't mount"
date: 2011-07-10
forum: General Help
---

### Post by linuxuser12345 on 2011-07-10
Hey, we have a nice 16GB flash drive, but every time I try to plug it up to our Ubuntu powered system, the computer never even recognizes it. :( 
Is there a simple way I can fix this problem without having to go out and buy a new flash drive?

Also, we have the same problem with Ubuntu recognizing an old 128mb SD card.

---

### Post by wojox on 2011-07-10
What does it say when you plug in the drive, open the terminal and run:

```
dmesg | tail
```

---

### Post by linuxuser12345 on 2011-07-10
Nevermind. I got it once I reformatted it! :)

How about the 128mb SD card that the system won't recognize? Is there a way I can get THAT to mount?

---

### Post by wojox on 2011-07-10
Plug in that card and run that command.

---

### Post by linuxuser12345 on 2011-07-23
Sorry for not getting back to you in time. :/
Here is what the terminal tells me what's going on with this little 128MB SD:
```
jeb@Kitchen-PC:~$ dmesg | tail
[ 8799.036249] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 8799.036251] sd 7:0:0:0: [sdb]  Add. Sense: Medium not present
[ 8799.036255] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 20 00 00 08 00
[ 8799.036260] end_request: I/O error, dev sdb, sector 32
[ 8799.037695] sd 7:0:0:0: [sdb] Device not ready
[ 8799.037703] sd 7:0:0:0: [sdb]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8799.037707] sd 7:0:0:0: [sdb]  Sense Key : Not Ready [current] 
[ 8799.037711] sd 7:0:0:0: [sdb]  Add. Sense: Medium not present
[ 8799.037717] sd 7:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[ 8799.037724] end_request: I/O error, dev sdb, sector 4096
jeb@Kitchen-PC:~$ 

```

Can anyone help me get this card running okay with Ubuntu?

---

