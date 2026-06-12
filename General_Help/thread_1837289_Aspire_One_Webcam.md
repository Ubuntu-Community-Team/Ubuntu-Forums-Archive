---
title: "Aspire One Webcam"
date: 2011-09-01
forum: General Help
---

### Post by Lighthorse01 on 2011-09-01
ubuntu 11.04
AspireOne KAV10
 
Has anyone figured out how to get the webcam and mic recognized ??
trying to setup Skype.
 
typed lsusb in terminal and it was in the list but I still dont get any drivers for it  ????

---

### Post by mikewhatever on 2011-09-01
As far as I am aware, Acer doesn't make webcams, in fact, it doesn't make computers either, but the point here is, you need to post the output of lsusb.
It also would have been nice if you could explain why you think you need drivers.

---

### Post by Lighthorse01 on 2011-09-01
Well I would asume that if ubuntu does not see or recognize the web cam or the internal mic then it needs some kind of driver.
As far as the laptop is concerned, whether you believe Acer makes a computer or not is not the point or the issue, that can be solved the next time you go to the store and look at laptops for sale.
As I said it is an Acer AspireOne KAV10 and Acer used the "Acer CrystalEye Webcam**".**
IF the list would help here it is.
 
[FONT=Batang][SIZE=2]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 003 Device 002: ID 045e:074f Microsoft Corp.[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 001 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 001 Device 002: ID 093b:0027 Plextor Corp.[/SIZE][/FONT]
[FONT=Batang][SIZE=2]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
 
the webcam is listed but not the mic.
anyway Skype does not see it either.

---

### Post by mikewhatever on 2011-09-01
As you can see, the real webcam manufacturer seems to be Suyin Corporation. Try Cheese to check it the webcam works, and if it does, use workarounds for Skype as outlined [->here<-]("https://help.ubuntu.com/community/Webcam/Troubleshooting").
If that doesn't help, the output you provided will be useful in searching for a solution.

The mic is not listed among USB devices because, presumably, it has nothing to do with ..., well, usb devices. To troubleshoot that, you'll need the output of 'aplay -l'.

PS: Good luck with asking about the real computer makers at computer stored. I'd bet that sales staff never heard of Compal Electronics or Quanta Computer.

---

### Post by Lighthorse01 on 2011-09-02
> **mikewhatever said:**
> 
PS: Good luck with asking about the real computer makers at computer stored. I'd bet that sales staff never heard of Compal Electronics or Quanta Computer.
Probably not but if you go in and ask for a machine made by them , they would be lost so to be easier on everybody it is still an Acer weather they made it or not.
imagine asking for a Quanta KAV10 , LOL.
 
anyway I did try Cheese and yes it sees it not to clearly, but it does see it. I will look into the work arounds
I forgot about aplay -l
Thanks

---

