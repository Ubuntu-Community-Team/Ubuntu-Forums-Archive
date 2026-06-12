---
title: "Is my hard disk failing?"
date: 2010-04-15
forum: General Help
---

### Post by Brandon110 on 2010-04-15
This is about the 3rd time I've reinstalled my operating system on my hard drive and somehow it seems to be working fine as of right now, but the other two times the same thing happened. I installed ubuntu 9.10 and it worked for about a week each time, then one day when I booted it up it would say hard disk failure. It hasn't happened yet, but im sure it will. It says hard disk failure directly after the motherboard's default screen, and I can't do anything other then restart, of which it repeats the same error message again. I've done several disk checks with the seatools and seatools dos, my hard drive type and what not is posted in the image. Seatools, the disk checking tools for my specific hardware brand, said that the disk had 17 errors and corrected all 17 of them supposedly, afterwards i have ran the same thing about 2 or 3 more times and it has reported that there are  no errors, yet my computer keeps "crashing" basically and telling me that there is a hard drive error. I just want some assurance that sending the hard drive in for replacement is the correct option - or is there anything else that someone may suggest I do before? to guarantee that it is the hard drive and nothing else? (I have a custom built computer and I'm sure there can be another problem). Thank you for your time.


edit: The screenshot is not uploading, I believe the reason is because I am downloading things on my other computer(laptop) I will post the screenshot before 8:00pm Central American time.

---

### Post by hackb0y294 on 2010-04-15
It sounds like it is failing. Most fairly recent mobos have S.M.A.R.T. Monitoring, which will notify you on startup if a Hard Disk has problems. I'm surprised the Ubuntu Disk Utility (which also uses S.M.A.R.T.) didn't show it though. It has always notified me of problems with Hard Disks.

How old is it? If it's less than a couple years old, I doubt it's bad, but that could happen with very heavy use.

---

### Post by hangfire on 2010-04-15
Why is SMART not available? Do you have SMART turned off in the BIOS or don't have smartmontools installed or the smartd daemon running? In your situation it doesn't make any sense to not run the smart daemon.

What were the 17 errors you received?

In any case, if you get one more crash after Seatool's corrections, RMA the drive immediately.

---

### Post by Claus7 on 2010-04-15
Hello,

first of, try to write with paragraphs, as the reading of your message becomes a little bit difficult.

Now, concerning your problem, I would like to inform you to use the following:

1) with this command you will see the mounted disks of your pc.
```
df -h
```

2)unmount as root the one you think is causing you troubles, e.g.:
sudo umount /dev/sd## (where the first # is a letter: a, b, c ... referring to the disk you are interested in and the second # is a number referring to the partition you want to check)

3)remember the disk you unmounted and run a checking for this disk:
```
sudo fsck -y -f -v /dev/sd## (where ## as before)
```

The final step will take a lot amount of time, depending on the errors of the hdd and its capacity.

If things go well your hdd will be ready to work. If not, you will be informed about it.

Hope this helped,
Regards!

PS: I used fsck. There are also other commands like e2fsck, which are specific for the type of formatting of your disk (ext2, ext3). I think that this is the general command you can use.

---

### Post by philinux on 2010-04-15
The disk utility palimpsest has been slightly crippled on purpose till they fix the bug about it reporting bad sectors when there in fact aren't any. This bug does not affect everyone though.

There is another smart tester in synaptic that I'm using meanwhile.

The app is gsmartcontrol and it's menu item is goes in Apps>system tools.
If a hard drive appears to be failing it's best to back up anything important quickly.

---

