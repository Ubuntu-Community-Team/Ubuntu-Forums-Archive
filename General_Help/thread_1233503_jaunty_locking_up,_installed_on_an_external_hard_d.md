---
title: "jaunty locking up, installed on an external hard drive"
date: 2009-08-06
forum: General Help
---

### Post by jcm1107 on 2009-08-06
Hi, my brother has jaunty installed on an external hard drive and it locks up sometimes. I would like to fix it because I don't want him or anyone else that might see or use his computer, think that ubuntu locks up (like windows) cause it don't, at least my hardy does not lock up. I have not used jaunty but I know ubuntu good enuff to know that it is awsome and there is some fix to his problem. I just have not used jaunty and I have only seen it on his computer and it is on an external hard drive. Could someone please tell me if jaunty has problems like this or if it is because of it being on an external hard drive which I think is usb 2.0?

---

### Post by quixote on 2009-08-07
It's not jaunty, it's the USB external drive.  Those take longer for the computer to recognize during the boot up process, so sometimes things time out before it does.  There is a workaround, but I haven't had to use it myself, so I'm not sure how complicated it really is.

Two sites for some more info:

ubuntu wiki on how to [boot from a USB HD]("https://help.ubuntu.com/community/BootFromUSB") 

Supergrub is an alternative to grub you can download, and it also has a good wiki: "[Grub On Removable External Hard Disk Not Booting]("http://www.supergrubdisk.org/w/index.php5?title=GrubOnRemovableExternalHardDiskNotBooting")"

---

### Post by jcm1107 on 2009-08-08
thanks for the info. It is some really good stuff about grub. But the problem is not getting it to boot up it is when using ubuntu it freezes sometimes.It usually is ok after 5-10 seconds sometimes more though and sometimes you have to push the reset button on his computer because it is locked up. I have never had a problem like this with Hardy but I don't know if his problem is because it is an external drive or what. I am sure ubuntu shouldn't lock up like that. I have not really been able to check his computer out though and I just want to get it fixed or know what the problem is so people don't see it and think ubuntu is bad. I love Ubuntu.

---

### Post by quixote on 2009-08-08
Sorry.  I misunderstood.  Lockups like that can be due to running out of system memory, or sometimes issues with the graphics card.  The memory can be too little system memory in the computer, or badly behaved programs that don't handle memory well.  (Much as I love Firefox, before version 3, it was sometimes a culprit there.)

How much memory is in his computer?  Is there any pattern to when the lockups happen?  Eg bittorrent running?  Watching video?  Running spreadsheet calcs?

What are the system specs generally, and what kind of graphics card has he got?

---

### Post by Mrandersonjr on 2009-08-08
Could it be the drive is spinning down when you don't want it to,thus going into hibernation while you are still using it?

[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

Scroll down to section 3 and follow the instructions and it should work :) :popcorn:

---

### Post by Crunchy the Headcrab on 2009-08-08
I don't recommend running any OS off of an external drive.

---

### Post by jcm1107 on 2009-08-09
Crunchy the Headcrab
I would say I agree with you but he got one just to install jaunty on becase he loved my ubuntu and his windows drive is small (40 gig). I told him he should of let me know he was going to do that and I would have helped him pick a good internal drive, he said he wanted external so it was portable(Kids!! wont listen to nothing!) I don't know what graphics card but I know it is older 2 years or more old and he has 512 mb of ram I don't know what kind, well it is kingston but I mean modle it is older not like the new stuff I have.I know he has an older pentium processor but it is decent. He does not run spread sheets just surfs the net and he watches youtube/myspace videos alot and uploads them he didn't install anything extra before the problem started it did it since the fresh install. One thing I wonder about is I unhooked his internal drive when I installed jaunty and now it is hooked up and his jauny boots when his external drive is pluged in and his windows boots when the external drive is unpluged. I just kind of have to wonder if possibly windows could be also running or mabe trying to boot when his external drive is running jaunty. I know if it is that would deffinatly cause the lock up. He told me not to wory about tinkering with it (the menu.lst) becuase it boots up but I just have to wonder. I have edited my grub boot list and I know how to. I edited his to boot windows even when his external drive is pluged in but it says error 17 I think. So I think the right way would be install grub to the internal hard drive. I have an external drive (I just use for backups and storage) I have to have it unpluged or windows will not even boot on my computer so I just wonder what might be also trying to run when he is using jaunty. Mrandersonjr, I checked out your link. This very well may be what is happening and that link is about a segate drive and it is kind of funny but his is a segate so if that brand is pickey then that would also explain it. I really appreciate all the help, like I said it is my brothers computer and I just want him and everyone else that uses his computer to know Ubuntu is awsome and dont want anyone to think it is bad. I am just doing this out of love for Ubuntu.

---

### Post by jcm1107 on 2009-08-09
I read the link about the drive spinning down and I think that may be what it is doing. I know that when it does lock up it usually starts again after a while so that seems to sound like the drive may have went to standby. I did what it said with sdparm and I will see if it  freezes anymore. THANKS!!

---

### Post by quixote on 2009-08-09
Good thought, about the drive spinning down.  Doesn't matter for data, but I can see an OS getting huffy about it.  By the way, 512MB memory is not much these days.  Ubuntu takes about 350MB to run.  (Just for comparison, Vista I think takes about 1.7GB or so.)  So advise your brother not to run lots of stuff simultaneously, and certainly not to run two memory-intensive things at the same time.

Let us know how the fix works.  I'm going to need it myself one of these days!

---

### Post by jcm1107 on 2009-08-09
to quixote
I know that 512mb is not that much I have 4 gig but of course not all is recognized but I will definatly let you know if this worked I just want to know if it is going to lock up anymore and it is not my computer so I don't use it and he really never is home much lately so as soon as I am sure it is fixed I will let you know. Maybe I will try to test it some just to see if it is fixed. I really do think it seems like the drive spinning down though, but I do know his system is getting on the older side for the hardware. I do have to say that using an OS off of an external drive is not as bad as I would have thought. I would say it is a lot better than running from the live cd. The only thing different about the external drive was the lockup problem. I had more problems than that when I installed Hardy on my internal drive (I did get them all fixed though, much with the help of people on this forum!)

---

