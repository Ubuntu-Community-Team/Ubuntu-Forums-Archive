---
title: "Dvd Not readable in natty"
date: 2011-05-14
forum: General Help
---

### Post by slyblade900 on 2011-05-14
Hello, I'm using Ubuntu 11.04 and am unable to read any DVD from my DVD writer. I'm sure its some Software issues as CD's seem to work fine with this distribution. Can someone tell me how to get my DVD Writer working again. DVD's (all) are not detected at all by the system. They must atleast be mounted or something but nothing. I even check the Disk utility to see if the system can see the DVD but not able to mount it. No luck. The DVD is not Detected. btw All the DVD's i tested work fine in windows

---

### Post by nerdy_kid on 2011-05-14
you probably have to install the decryption library.  Note that this may be illegal in some countries (from what I've heard).

Do this:

```

sudo apt-get install ubuntu-restricted-extras

```


and then

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

and you should be good to go.

[edit]
in afterthought, I think that Ubuntu will at least recognize the dvd even without the decryption library...so maybe you have a totally different issue.  I would still give the above steps a shot though, just to rule out the possibility.  If it still doesn't work, post the output of 
```

 tail -n 50 /var/log/syslog

```
30 seconds or so after inserting a dvd.

---

### Post by slyblade900 on 2011-05-14
prasana@prasana-desktop:~$ tail -n 50 /var/log/syslog
May 14 21:21:50 prasana-desktop kernel: [  742.212188] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:21:50 prasana-desktop kernel: [  742.212191] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:21:50 prasana-desktop kernel: [  742.212194] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:21:50 prasana-desktop kernel: [  742.212197] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:21:50 prasana-desktop kernel: [  742.212201] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:21:50 prasana-desktop kernel: [  742.212207] end_request: I/O error, dev sr0, sector 0
May 14 21:21:50 prasana-desktop kernel: [  742.212210] quiet_error: 15 callbacks suppressed
May 14 21:21:50 prasana-desktop kernel: [  742.212212] Buffer I/O error on device sr0, logical block 0
May 14 21:21:59 prasana-desktop kernel: [  751.398093] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:21:59 prasana-desktop kernel: [  751.398096] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:21:59 prasana-desktop kernel: [  751.398099] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:21:59 prasana-desktop kernel: [  751.398102] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:21:59 prasana-desktop kernel: [  751.398106] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:21:59 prasana-desktop kernel: [  751.398112] end_request: I/O error, dev sr0, sector 0
May 14 21:21:59 prasana-desktop kernel: [  751.398115] Buffer I/O error on device sr0, logical block 0
May 14 21:22:08 prasana-desktop kernel: [  760.228213] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:22:08 prasana-desktop kernel: [  760.228216] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:22:08 prasana-desktop kernel: [  760.228219] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:22:08 prasana-desktop kernel: [  760.228222] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:22:08 prasana-desktop kernel: [  760.228225] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:22:08 prasana-desktop kernel: [  760.228232] end_request: I/O error, dev sr0, sector 0
May 14 21:22:08 prasana-desktop kernel: [  760.228235] Buffer I/O error on device sr0, logical block 0
May 14 21:22:17 prasana-desktop kernel: [  769.052008] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:22:17 prasana-desktop kernel: [  769.052010] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:22:17 prasana-desktop kernel: [  769.052013] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:22:17 prasana-desktop kernel: [  769.052017] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:22:17 prasana-desktop kernel: [  769.052020] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:22:17 prasana-desktop kernel: [  769.052027] end_request: I/O error, dev sr0, sector 0
May 14 21:22:17 prasana-desktop kernel: [  769.052030] Buffer I/O error on device sr0, logical block 0
May 14 21:22:26 prasana-desktop kernel: [  777.613438] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:22:26 prasana-desktop kernel: [  777.613441] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:22:26 prasana-desktop kernel: [  777.613444] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:22:26 prasana-desktop kernel: [  777.613448] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:22:26 prasana-desktop kernel: [  777.613451] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:22:26 prasana-desktop kernel: [  777.613457] end_request: I/O error, dev sr0, sector 0
May 14 21:22:26 prasana-desktop kernel: [  777.613460] Buffer I/O error on device sr0, logical block 0
May 14 21:22:34 prasana-desktop kernel: [  786.451154] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:22:34 prasana-desktop kernel: [  786.451157] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:22:34 prasana-desktop kernel: [  786.451161] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:22:34 prasana-desktop kernel: [  786.451166] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:22:34 prasana-desktop kernel: [  786.451170] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:22:34 prasana-desktop kernel: [  786.451178] end_request: I/O error, dev sr0, sector 0
May 14 21:22:34 prasana-desktop kernel: [  786.451182] Buffer I/O error on device sr0, logical block 0
May 14 21:22:43 prasana-desktop kernel: [  795.320387] sr 0:0:1:0: [sr0] Unhandled sense code
May 14 21:22:43 prasana-desktop kernel: [  795.320390] sr 0:0:1:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 14 21:22:43 prasana-desktop kernel: [  795.320393] sr 0:0:1:0: [sr0]  Sense Key : Medium Error [current] 
May 14 21:22:43 prasana-desktop kernel: [  795.320396] sr 0:0:1:0: [sr0]  Add. Sense: L-EC uncorrectable error
May 14 21:22:43 prasana-desktop kernel: [  795.320399] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 14 21:22:43 prasana-desktop kernel: [  795.320406] end_request: I/O error, dev sr0, sector 0
May 14 21:22:43 prasana-desktop kernel: [  795.320409] Buffer I/O error on device sr0, logical block 0

---

### Post by slyblade900 on 2011-05-14
Installed ubuntu restricted extras and executed that script too. Still no luck. And LOL to Microsoft if they banned all those Ubuntu restricted extras :)

---

### Post by nerdy_kid on 2011-05-14
Look like a bunch of I/O errors -- usually a hardware problem, but not always.  You said you tested the dvds on Windows -- did you use the same laptop?

If so, I hope someone else can help you, cause I won't be able to help any more.

If not, then I suggest cleaning your laser head on your laptop and giving it another try.

---

### Post by slyblade900 on 2011-05-15
If thats the case then why does CD's get read properly, It's only the DVDs that won't get detected. So i'm sure it's a software problem. As for the testing no, i own another machine with windows on it. Tested it with windows!! Thanks for replying though. And this problem occurs for every DVD.... Sigh. Must wait for another stable distro. util then , I'll have to ISo the disk , transfer in pendrive and use. A real pain !!

---

### Post by bcavagnolo on 2011-08-23
I have this same problem:

```

$ dmesg
[  540.859123] sr 3:0:0:0: [sr0] Unhandled sense code
[  540.859127] sr 3:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  540.859132] sr 3:0:0:0: [sr0]  Sense Key : Medium Error [current] 
[  540.859137] sr 3:0:0:0: [sr0]  Add. Sense: No seek complete
[  540.859142] sr 3:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  540.859153] end_request: I/O error, dev sr0, sector 0
[  540.859158] quiet_error: 97 callbacks suppressed
[  540.859161] Buffer I/O error on device sr0, logical block 0

```

The disk is actually a Mac OS X Snow Leopard install disk, and I get the same errors with a Microsoft Visual Studio Install disk (don't ask :( ).  As the previous posts mention, CDs work fine, so I don't believe this is a hardware issue.  I'm happy to do some testing grunt work here.  Please advise.

---

### Post by philinux on 2011-08-23
> **slyblade900 said:**
> Hello, I'm using Ubuntu 11.04 and am unable to read any DVD from my DVD writer. I'm sure its some Software issues as CD's seem to work fine with this distribution. Can someone tell me how to get my DVD Writer working again. DVD's (all) are not detected at all by the system. They must atleast be mounted or something but nothing. I even check the Disk utility to see if the system can see the DVD but not able to mount it. No luck. The DVD is not Detected. btw All the DVD's i tested work fine in windows

If these are encrypted dvd's then you need medibuntu. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bcavagnolo on 2011-08-23
> **philinux said:**
> If these are encrypted dvd's then you need medibuntu. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

That did it.  Thank you.  There seems to be a lot of confusion out there on this matter.

EDIT: Hmm.  It looks like my success was a fluke.  After using the DVD for a while I slept my laptop.  When I resumed, I was getting the same disconcerting SCSI errors in dmesg.  I rebooted, but the problem persisted.

I also tried adding the all_generic_id=1 kernel arg, and also tried "sudo hdparm -E 0 /dev/sr0" as advised in some other posts.  The rationale for this shotgun approach was that I had tried these things variously prior to my initial success.

Anyway, jumping back a step: these appear to be low-level SCSI errors.  This makes me skeptical that a userspace fix is going to work.  Can somebody advise on how DVD decrypt works (i.e., what's the kernel interface, what daemons do the work, etc.) so I can dig deeper?

Thanks,
Brian

---

### Post by ubermike on 2012-01-03
I have been having this same problem. I can read any CD just fine but all DVDs show the same IO Error.

Any help would be greatly appreciated.

Thanks,
Mike

---

### Post by slyblade900 on 2013-02-19
Hi I'm closing this thread. The solution I found at that time was that the DVD writer did not work. It's still there. It can still read CD's 
I bought a new DVD writer. If you face the exact similar problem, DVD(all) not read, CD's read, then you better buy another DVD writer.
(Someone explained that the DVD spindle that reads the DVD's is different from the CD spindle :) But I came back to this forum after 2 years. It's so wonderful to see a stupid post I posted years ago. =) Closed for good

---

### Post by oldos2er on 2013-02-19
Hi, only staff can close threads, so I've done that for you.

---

