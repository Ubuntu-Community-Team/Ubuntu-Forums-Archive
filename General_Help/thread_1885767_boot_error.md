---
title: "boot error"
date: 2011-11-23
forum: General Help
---

### Post by jdwood83 on 2011-11-23
I've had some issues with my Ubuntu 11.10 crashing in the middle of my classes (running on an Eee PC 1000 w/ the SSD), but managed to get that fixed for the most part. But after a recent crashing in class, I haven't been able to boot up. When I hit the power button, I see normal BIOS stuff and then the following:

```
fsk from util-linux 2.19.1
/dev/sdb1: clean, 289429/3940832 files, 2873758/7880615 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
*Starting AppArmor profiles..................................[ok]
*Setting sensors limits......................................[ok]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
*Starting bluetooth..........................................[ok]
*PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
*Checking battery state... ..................................[ok]
```


And then it just stops. Normally these items just pop up and I'm onto the purple log-in screen. I tried just doing a complete reinstall, but as this is an Eee PC I need to use the USB drive method & for some reason, the CPU will not recognize the USB drive--I have changed the boot order to have USB 1st & have used "Unetbootin" and "Start-up Disk Creator" separately.

I am able to get into the text-only mode through using CTRL+ALT+F1, so if there's anything I need to do there that might help someone help me I'd be able & willing to do so.


Any help is greatly appreciated!

---

### Post by maverickaddicted on 2011-11-24
I was also having the same problem. I solved this problem by logging in as root by pressing CTRL+ALT+F1 and running this command

```
fsck -y /
```

Use sudo, if not root.

---

### Post by jdwood83 on 2011-11-30
Thanks for the quick reply Maverick, and sorry it has taken me so long to get back to you, but that suggestion did not work for me. I still get to the same stopping point of the loading screen as mentioned in Post #1.

Anyone else have a suggestion?

---

### Post by Rex Bouwense on 2011-11-30
Yes here is one.  I too have an EeePC 1000 and it recognizes the flash drive as another hard drive.  Go to the BIOS and change the order of the hard drives (move the flash drive to the first position) and you should be good to go.

---

### Post by jdwood83 on 2011-11-30
Rex, I cannot get my external USB drives to mount either. I have tried mount several times with limited success (it can be mounted, but it's still in read-only mode). In any event, I must be logged onto the computer to mount the USB drive, so I still wouldn't be able to boot from it.

When I do insert a USB drive while in the text-only mode (via CTRL+ALT+F1), I get the following message to come up:
```

[numbers] sd 3:0:0:0: [sdc] No Caching mode page present
[numbers] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[numbers] sd 3:0:0:0: [sdc] No Caching mode page present
[numbers] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[numbers] sd 3:0:0:0: [sdc] No Caching mode page present
[numbers] sd 3:0:0:0: [sdc] Assuming drive cache: write through
```

where "numbers" looks to be a time-stamp and vary depending on how long the computer has been on at the time when I inserted the drive. I've tried using Google to get something that might help with the above, but nothing is similar to my case.

I ran dmesg | grep sdc and got the following:
```
[numbers] sd 3:0:0:0: [sdc] 8082624 512 byte logical blocks: (4.13 GB/ 3.85 GB)
[numbers] sd 3:0:0:0: [sdc] Write Protect is on
[numbers] sd 3:0:0:0: [sdc] Mode Sense: 03 00 80 00
[numbers] sd 3:0:0:0: [sdc] No Caching mode page present
[numbers] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[numbers] sd 3:0:0:0: [sdc] No Caching mode page present
[numbers] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[numbers] sd 3:0:0:0: [sdc] No Caching mode page present
[numbers] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[numbers] sd 3:0:0:0: [sdc] Attached SCSI removable disk
```

And "numbers" here match the numbers above.


Any other suggestions?

---

### Post by Rex Bouwense on 2011-11-30
Yes,  I am assuming that you have a flash drive on which there is an ISO that you burned.  I also assume that you have already checked the MD5sum.  If that is not correct.  Check it now.
OK, with the computer turned off, insert the flash drive and press the power button.  When the EeePC splash comes up, quickly hit the F2 button.  That will get you to the BIOS.  Toggle over to Boot and hit enter.  Just toggle down to hard drive and once again hit enter.  You will see two entries, one will represent your hard drive and the other will represent the flash drive.  Make sure that the flash drive is listed to boot first.  Then hit F10, I believe, to exit and save.  Now your computer should boot from the flash drive.  You can try it to make sure everything works.  It should because it did on mine.  I move to Lubuntu not because Ubuntu wouldn't work, but because of the Unity interface.

---

