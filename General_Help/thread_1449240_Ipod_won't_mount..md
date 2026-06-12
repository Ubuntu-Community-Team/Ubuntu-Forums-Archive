---
title: "Ipod won't mount."
date: 2010-04-07
forum: General Help
---

### Post by Linye on 2010-04-07
I have an 80gb classic, Ubuntu 9.10

When I plug in the ipod it shows the "Connected" screen but it does nothing else. It won't show on rhythmbox, desktop or computer folder.  I ran the  "lsusb"   command and it show  it as connected.

*Bus 002 Device 004: ID 05ac:1261 Apple, Inc. iPod Classic*

I have searched around and my guess is that need to manually mount it but I haven't found how to do it. Can someone help me how to do this? 

thanks in advance and sorry for my english as its not my first language.

---

### Post by Linye on 2010-04-07
Anyone please :(

I must add that it was working fine when I installed ubuntu (last week) but it suddenly decided not to.

---

### Post by Johnny B on 2010-04-07
reboot with IPOD connected, thats what works for me

---

### Post by Linye on 2010-04-07
lol 

That was simple and accurate. Thank you so much.

Hope I don need to restart with the ipod connected every time I need to manage my music.

---

### Post by littlegreenlights on 2010-06-28
Here's something to try: [http://support.apple.com/kb/HT1320](http://support.apple.com/kb/HT1320)

This worked for me. I followed the reset instructions with my iPod plugged in. The screen dimmed, displayed a do not disconnect message, and within thirty seconds the system recognized and mounted the device, asking me what application to associate it with. Music was not lost.

iPod Nano 2nd generation, model A1199

---

### Post by quantumottle on 2010-07-25
> **littlegreenlights said:**
> Here's something to try: [http://support.apple.com/kb/HT1320](http://support.apple.com/kb/HT1320)

This worked for me. I followed the reset instructions with my iPod plugged in. The screen dimmed, displayed a do not disconnect message, and within thirty seconds the system recognized and mounted the device, asking me what application to associate it with. Music was not lost.

iPod Nano 2nd generation, model A1199

GOD BLESS YOU!!! I have been working for 2 weeks to figure this out, I was so frustrated that I was seriously starting to lose it tonight. My iPod worked fine in every way, except that it would not mount in Ubuntu Lucid. Since it worked I never would have thought to reset it, thanks so much for the info littlegreenlights!

---

### Post by PaulReaver on 2010-07-25
lol,   

when I saw "ipod wont mount" I thought apple were starting some sort of mephisto type breeding program. :twisted:

---

### Post by Jezzaroo on 2010-08-11
> **littlegreenlights said:**
> Here's something to try: [http://support.apple.com/kb/HT1320](http://support.apple.com/kb/HT1320)

This worked for me. I followed the reset instructions with my iPod plugged in. The screen dimmed, displayed a do not disconnect message, and within thirty seconds the system recognized and mounted the device, asking me what application to associate it with. Music was not lost.

iPod Nano 2nd generation, model A1199

Fantastic :D. Worked on my 5th gen 80Gb ipod in Linux Mint 9.

---

### Post by olamina on 2010-10-19
> **littlegreenlights said:**
> Here's something to try: [http://support.apple.com/kb/HT1320](http://support.apple.com/kb/HT1320)

This worked for me. I followed the reset instructions with my iPod plugged in. The screen dimmed, displayed a do not disconnect message, and within thirty seconds the system recognized and mounted the device, asking me what application to associate it with. Music was not lost.

iPod Nano 2nd generation, model A1199

THANKS!! Worked for me too! Whew!

---

### Post by MarkMyWord on 2010-10-19
> **Jezzaroo said:**
> Fantastic :D. Worked on my 5th gen 80Gb ipod in Linux Mint 9.

Do iPod Nana 5g work with Ubuntu yet?  I can't try because Maverick has crashed.

---

### Post by DriftingSamurai7 on 2010-10-25
My 6th gen 80gb classic was giving me the same problem. But then all of a sudden Maverick and Rhythmbox both recognized and mounted my iPod. Now it wont mount in Maverick again. I tried resetting my ipod while connected and while disconnected and it still wont mount. :/


EDIT: I was able to get my iPod to mount after a factory restore using a win computer with itunes.Music transfers but wont play and thats an issue for another thread

---

### Post by laurenblah on 2010-10-26
I'm having the same damn problem

---

### Post by Tim_Crandall on 2010-10-30
I tried rebooting mine while it's connected and it doesn't work for me. I have an 80gb 6g classic, and I just updated to 10.10. I could really use some help with this.

---

### Post by Tim_Crandall on 2010-11-04
anyone?? I'm pretty desperate to get my ipod to work. I've tried virtualbox, resetting, restoring, and I still can't get my ipod to mount in Ubuntu. The hard drive on my ipod just got replaced and is brand new. Does that have something to do with it? ...Help!!!

---

### Post by Ben M on 2010-12-15
I'm having the same problem with my 80gb ipod classis. Has anyone managed to get it working. I have floola installed on the ipod which worked fine under vista and i thought it worked on any platform but not on maverick meercat. I've tried amarok, rythmbox and gtkpod but none of them work properly.
It seems to think floola is an archive.

---

### Post by nathan28 on 2010-12-22
I'm having a similar problem with my old 2gb nano (2g), but think it might be an issue w/ the iPod's disk, not nautilus. 

Nuke and pave: [http://ubuntuforums.org/showthread.php?t=1263715](http://ubuntuforums.org/showthread.php?t=1263715), which I'm trying to avoid.

---

### Post by nathan28 on 2010-12-22
Strange enough, now I can mount automatically but am getting "should not be accessed" in the console when trying to use gtkpod (even as root) to copy mp3s over.

The iPod is at sdcX. Here is fdisk -l:

>    Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           6       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 12)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(5, 31, 43)
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/sdc2               6         107     1886072    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(5, 31, 44)
Partition 2 has different physical/logical endings:
     phys=(61, 178, 52) logical=(106, 88, 7)
Partition 2 does not start on physical sector boundary.

here's (no -N, I'm a rebel) fsck.vfat

> dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Logical sector size (23597 bytes) is not a multiple of the physical sector size.





I'm not particularly interested in trying to figure out WTF the problem is and none of the files here are worth saving.

---

