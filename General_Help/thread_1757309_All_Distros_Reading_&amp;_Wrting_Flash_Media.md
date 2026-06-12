---
title: "All Distros: Reading &amp; Wrting Flash Media"
date: 2011-05-13
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-13
Hello,

In all of the last several distros, I've always had trouble reading and writing 'any' type of Flash media; thumb drives, SD Cards, mp3 players, etc.

**Explanation:**

During reading or writing of Flash media, the file transfer often ***hangs*** near the end of the last file to be transfered; even when I had ***'no'*** other applications running.  This was especially problematic in Lucid, and improved ***somewhat*** in Maverick & Natty.  Since I have a dual-boot configuration, I tested this repeatedly in Windows 7, and had no such problems.  Also, I never had this problem in either Vista or XP. (Same unit, same devices).

In an effort to analyze what was going-on with the hardware internally, I opened the System-Monitor to the Resources tab, so that I could watch CPU activity during the file transfer.

**I Noticed The Following:**

The file transfer would actually take place in very small ***'bursts,'*** represented by spikes in the CPU activity.  I verified this by observing that the activity in the file transfer window was concurrent with the spikes in the CPU activity, ***without exception.***  I also observed the above mentioned delay near the end of the last file to be transfered; as I observed ***'no'*** futher CPU activity spikes for some time.  The final spike ***'always'*** coincided with the end of the file transfer, and the closing of the file transfer window.  I believe the file-transfer process ***'may' even have been asleep.***  What I also noticed, on some of the occassions when I had to manually terminate the file transfer for excessive delay, was that the destination file on the Flash device, was the same size as the source file on my HDD, and vice-versa; ***indicating that the file transfer 'may' have actually completed, without the file-transfer process terminating.***  So it appears that there are two problems:

1. The file transfer takes place in [COLOR=Blue]*'small-bursts,'*[/COLOR] even when no other applications are running. [COLOR=Red]* (This could be due to the file transfer process 'not' having a high-enough priority).*[/COLOR]

2. The file transfer [COLOR=Blue]*'**delay,' or 'hang'*[/COLOR] near the end of the last file to be transfered.  (This could be caused by the file-transfer 'application,' or 'device-drivers' ***waiting*** for an end-of-file or end-of-process signal that is never received).  ***This is most likely a [COLOR=Blue]Linux [/COLOR]kernel issue 'not' an Ubuntu issue; but is an important issue to be resolved none-the-less.***

Can anyone offer an explanation for why this might be happening and a possible solution???

[IMG]http://img697.imageshack.us/img697/4379/screenshotsystemmonitor.jpg[/IMG]

---

### Post by dargaud on 2011-05-13
Block transfers between devices are often coded as DMA (Direct Memory Access) in the drivers, so the CPU doesn't actually do anything except setup the transfer.

This being said I have no idea why your transfer doesn't end, but I've had this problem in the past: it was a faulty USB key. Do you also have the problem if you copy from the command line ?
```
cp -v BigFile /media/UsbDevice/
```

---

### Post by coljohnhannibalsmith on 2011-05-13
> **dargaud said:**
> This being said I have no idea why your transfer doesn't end, but I've had this problem in the past: it was a faulty USB key. Do you also have the problem if you copy from the command line ?
```
cp -v BigFile /media/UsbDevice/
```

***Yes, and with several devices...***

In fact, there's a 'hang' near the end of ***each*** file to be transfered.  I selected two files to be transfered together, to verify this. [I][COLOR=Blue] (Same situation with the spikes).

[/COLOR]
[/I]


Thanks, Hannibal

---

### Post by oldfred on 2011-05-13
Writing to flash via USB is always slow. 

I think it is just the progress bar gets ahead of the flash drive. My flash drive(s) with LEDs continue to flicker at the same pace from start to finish even though progress is hung near the end.

---

### Post by coljohnhannibalsmith on 2011-05-15
> **oldfred said:**
> Writing to flash via USB is always slow. 

I think it is just the progress bar gets ahead of the flash drive. My flash drive(s) with LEDs continue to flicker at the same pace from start to finish even though progress is hung near the end.

I think it's more than that; but I have observed what you've described, in addition to everything else...

Anyway, Ubuntu/Linux doesn't do this as well as Windows, I'm sorry to say; and I can't think of any reason why we can't get this right...

[IMG]http://www.adamsattics.co.uk/images/getting_it_right.jpg[/IMG]




[COLOR=Blue]***Thanks Hannibal***[/COLOR]

---

