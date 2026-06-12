---
title: "Multisession dvd data recovery"
date: 2010-05-20
forum: General Help
---

### Post by linuxyogi on 2010-05-20
Hi. 

I created a data[COLOR="Red"] udf[/COLOR] DVD in multi-session mode & it took about 11 sessions to complete/finalize the disk.

Now the problem is when I insert the DVD, first of all it refuses to mount automatically & so I mount it using the mount command in Terminal.

But there is no signs of any physical damage.In fact, the DVD disk is absolutely clean.

Even when I mount it using the mount command via Terminal --------

sudo mount -t udf /dev/cdrom /home/user0/cd

only a few files are actually visible. Most of the files are not even visible (as if they are not there).

These files are really important to me.

Please tell me a way to recover these files.

I will never burn another multisession disk in my lifetime !!! I promise !!!

Please help.

---

### Post by linuxyogi on 2010-05-20
Dmesg |tail prints something like ---------------


[ 1280.412419] sr 0:0:0:0: [sr0] Unhandled sense code
[ 1280.412423] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1280.412426] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1280.412430] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[ 1280.412435] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 16 0d 24 00 00 01 00
[ 1280.412441] end_request: I/O error, dev sr0, sector 5780624
[ 1283.297868] sr 0:0:0:0: [sr0] Unhandled sense code
[ 1283.297873] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1283.297876] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1283.297880] sr 0:0:0:0: [sr0] Add. Sense: Unrecovered read error
[ 1283.297884] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 16 0d 24 00 00

---

### Post by linuxyogi on 2010-05-20
I just installed gddrescue.

But the command "ddrescue -d -n -b2048 -v /dev/cdrom /home/user0/123.img"

recovers very few files. Most of them are still not visible (even in the ddrescue's image file.)

Which means that the earlier sessions are still not accessible. 

This is really getting difficult.

---

### Post by viktor489 on 2011-01-04
Thankyou linuxyogi!
This information was very helpfull to me for read a DVD without closing of an 4D ecography of my baby!... I was thinking that the files were lost.

---

### Post by linuxyogi on 2011-01-08
> **viktor489 said:**
> Thankyou linuxyogi!
This information was very helpfull to me for read a DVD without closing of an 4D ecography of my baby!... I was thinking that the files were lost.

You are welcome.

---

