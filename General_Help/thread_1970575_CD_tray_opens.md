---
title: "CD tray opens"
date: 2012-05-01
forum: General Help
---

### Post by rsb61 on 2012-05-01
The CD-R tray keeps opening on my mini-tower for no apparent reason.

I am currently running Ubuntu 12.04 LTS after having tried 11.10 for about 6 weeks.  The tray opened on 11.10 as well.  My system also has a DVD drive which does not open.  

My system is an older (5-6 years) min-tower which used to run Win-XP.  It has an Intel Celeron 2.4GHz CPU with 1GB RAM.  Apart from being a Genuine Intel motherboard, I don't know the exact model.

The CD-Writer is    	 	 	 	a Maxtor 34098H4 MAXTOR 6L080J4 - tray opens.

The DVD drive is a    	 	 	 	 	CR-4804TE HITACHI DVD-ROM GD-7500 - normal behavior.

The CD tray opens whether I'm using the computer or not.  My work-around is to leave a CD-ROM in the drive - with a disk in the tray, it does not seem to open.  In all other respects, both optical drives work properly.

Has anyone else seen this?  Any suggestions for a fix?  I am new to Ubuntu so I will need step by step instructions

Thanks

---

### Post by th1 on 2012-05-01
it also happens to me, with an old samsung dvd read/write drive

I'm on 11.10

---

### Post by Lindus on 2012-05-31
Sorry to be a "me too!".  This did not happen on any earlier versions for me.  It is rather annoying, especially as it happens intermittently and not on a regular schedule.

Can someone figure out what process may do this and if so in what logfile to look?

With many many thanks in advance,
/Lindus

---

### Post by roelforg on 2012-05-31
Check if someone's pranking you.
I once added a bootscript to my friends pc that listens to the keyboard and opens/closes the tray when you pressed certain keys (it was the first of april, we both had a good laugh about it).

---

### Post by Lindus on 2012-06-01
> **roelforg said:**
> Check if someone's pranking you.
I once added a bootscript to my friends pc that listens to the keyboard and opens/closes the tray when you pressed certain keys (it was the first of april, we both had a good laugh about it).
Well, unfortunately it ain't so, unless this is part of the noob hazing which I am not assuming it is as it is a clean install of 12.04 LTS so...

This is what seemingly appear in syslog when it happens:
kernel: [516908.000027] [Hardware Error]: Machine check events logged

I have seen similar reports in other releases but not really any solutions so if someone could please figure out what may be going on would be greatly appreciated!

With many thanks in advance,
/Lindus

---

### Post by Sularco on 2012-06-01
I would suggest to use an elimination process to find the problem; does this happen if you boot your PC into the BIOS instead of allowing grub to start Ubuntu? In that case it is most likely a hardware problem and you should try other cables for data and power. If that does work, then the CD writer itself is probably faulty.

If it does not happen if you boot into the BIOS, then it gets really tricky; I once had a machine doing the same thing and nothing really looked wrong with it. In the end I found that the CPU had it and replacing it fixed the problem with the CD tray. Given however that you already have found that Kernel error message, I'd put my money on a faulty CD writer unit.

---

### Post by dibuntux on 2012-10-23
Just upgrade my system running 10.04 lts AMD64 for over 2 years without a glitch to 12.04...
At logon the CD-ROM burner opens up. I have a second DVD burner that does not open...

Any ideas?

---

### Post by Gotti on 2012-10-23
Since it's happening to a bunch of folks I assume this isn't the issue..but worth a mention...make sure you don't have anyone connecting to you via ssh. I used to have a blast opening my brothers tray from my laptop...expletives and hilarity ensued every time.

---

### Post by dibuntux on 2012-12-06
No, it cannot be. I'm on a private subnet and it happens just after the computer is turned on. Then it maybe stays quite for hours and then it will do a couple of times in few minutes. Totally random.
Thanks anyway for your suggestion.

---

### Post by rnerwein on 2012-12-06
> **rsb61 said:**
> The CD-R tray keeps opening on my mini-tower for no apparent reason.

I am currently running Ubuntu 12.04 LTS after having tried 11.10 for about 6 weeks.  The tray opened on 11.10 as well.  My system also has a DVD drive which does not open.  

My system is an older (5-6 years) min-tower which used to run Win-XP.  It has an Intel Celeron 2.4GHz CPU with 1GB RAM.  Apart from being a Genuine Intel motherboard, I don't know the exact model.

The CD-Writer is                       a Maxtor 34098H4 MAXTOR 6L080J4 - tray opens.

The DVD drive is a                            CR-4804TE HITACHI DVD-ROM GD-7500 - normal behavior.

The CD tray opens whether I'm using the computer or not.  My work-around is to leave a CD-ROM in the drive - with a disk in the tray, it does not seem to open.  In all other respects, both optical drives work properly.

Has anyone else seen this?  Any suggestions for a fix?  I am new to Ubuntu so I will need step by step instructions

Thanks
have a look at: man eject  (e.g. eject -i on /dev/sr1  - this will lock the open buttom of your second drive)
for lazy people ( as me) use: eject -T /dev/srX (this toggle open/close)
cheers

---

### Post by dibuntux on 2012-12-07
I had already tried the proposed solution of letting a CD in the drive to no use, it still opens randomly.

I just tried the eject command: eject -i on /dev/sr1
with sr1 being the offending CD-R in my system. It has no effect on the eject button of sr1, but instead it blocks sr0, the DVD!
And no, if I do eject -i on /dev/sr0 it does not block anything.

But anyway, this are unacceptable tricks for a serious OS like linux should be. This is happening just after an upgrade on perfectly running hardware since Ubuntu 7.10.

Any more ideas? TIA

---

### Post by rnerwein on 2012-12-07
> **dibuntux said:**
> I had already tried the proposed solution of letting a CD in the drive to no use, it still opens randomly.

I just tried the eject command: eject -i on /dev/sr1
with sr1 being the offending CD-R in my system. It has no effect on the eject button of sr1, but instead it blocks sr0, the DVD!
And no, if I do eject -i on /dev/sr0 it does not block anything.

But anyway, this are unacceptable tricks for a serious OS like linux should be. This is happening just after an upgrade on perfectly running hardware since Ubuntu 7.10.

Any more ideas? TIA
i agree - but if you can't fix it fake it
cheers

---

