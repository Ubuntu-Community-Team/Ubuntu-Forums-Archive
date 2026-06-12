---
title: "DMA hard drive error"
date: 2006-05-28
forum: General Help
---

### Post by Third Thoughts on 2006-05-28
I have been getting some rather disturbing hard drive errors. Here's my dmesg output. 
```
[4295527.845000] hda: DMA timeout error
[4295527.845000] hda: dma timeout error: status=0x50 { DriveReady SeekComplete }[4295527.845000]
[4295527.845000] ide: failed opcode was: unknown
[4295547.865000] hda: dma_timer_expiry: dma status == 0x21
[4295557.865000] hda: DMA timeout error
[4295557.865000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[4295557.865000]
[4295557.865000] ide: failed opcode was: unknown
[4295562.866000] hda: status timeout: status=0xd0 { Busy }
[4295562.866000]
[4295562.866000] ide: failed opcode was: unknown
[4295562.866000] hda: drive not ready for command
[4295562.916000] ide0: reset: success
[4295583.034000] hda: dma_timer_expiry: dma status == 0x21
[4295593.034000] hda: DMA timeout error
[4295593.034000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[4295593.034000]
[4295593.034000] ide: failed opcode was: unknown
[4295613.059000] hda: dma_timer_expiry: dma status == 0x21
[4295623.059000] hda: DMA timeout error
[4295623.059000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
[4295623.059000]
[4295623.059000] ide: failed opcode was: unknown

```

This is accompanied by my entire system locking up. From what I've googled this often suggests a dying disk, and thus I will be backing stuff up ASAP, but I've run a number of disk health utilities, (fsck and smartctl) and its come up with a clean bill. 

My own personal theory is that the problem is overheating. The last few times it locked up I removed the cover and pointed a room fan directly at the computer. In a matter of minutes things unlocked. Once I replaced the cover it would only be a matter of time before they locked up again. Basically I'm wondering if anyone can validate my theory. I don't know too much about DMA, or hard drive failure, so I'm basically taking a shot in the dark with the overheating hypothesis. Also if anyone can offer a solution less labor intensive than buy more fans that would be cool too.

~Andrew S.

---

### Post by daWabbit on 2006-05-28
I have encountered this 3 times in the last month. Once it was the drive, though everything checked out fine when it was put into an external enclosure and diagnostic utilities run against it. Total failure of the drive a few hours later convinced me the diagnostics were incorrect. 

The other two times, it was the IDE controller on the motherboard. Both machines in question were older (one 5 years and one 3 years old and both running continuously since new). I should add that both machines were "value" models from HP, meaning they were put together with less than premium components, though they served well enough for a while. 

On one machine, the controller acted up a couple times, locking the system and returning log entries similar to the ones you posted, then just died. On the other, problems were erratic and I decided the first thing to do was to clean out the dust (I live in a very dusty place, only a couple hundred meters from an active gravel pit) and make sure things were cooling as intended. This did indeed have a markedly positive effect, but did not cure the problem. I run a continuous backup, so had nothing to lose by continuing to experiment. 

After another few days of operation, with just a couple lockups, the controller failed totally. An hour's cooling off period would return function long enough to boot, but then the controller would simply fail. 

In both cases, motherboard replacement cured the problems. I took the opportunity to upgrade the boxes, as well, though still with well used, salvaged parts. 

If you are backed up, I would go ahead and play with it. Else I would back up what I could, even if I had to transfer the hard drive to another machine to do it, then stress test the drive. If it passes that, it's motherboard time for you, too. 

Jack

---

### Post by Third Thoughts on 2006-05-28
[QUOTE=daWabbit]I have encountered this 3 times in the last month. Once it was the drive, though everything checked out fine when it was put into an external enclosure and diagnostic utilities run against it. Total failure of the drive a few hours later convinced me the diagnostics were incorrect. 
[/QUOTE]

That scared me into backing up things right away. Now I've got things safely on an external harddrive (though not after some headaches, took me forever to figure out that the Simple Backup Utility doesn't like spaces in file names.) Thanks for the quick and informative reply.

[QUOTE=daWabbit]
The other two times, it was the IDE controller on the motherboard. Both machines in question were older (one 5 years and one 3 years old and both running continuously since new). I should add that both machines were "value" models from HP, meaning they were put together with less than premium components, though they served well enough for a while. 
[/QUOTE]

My machine doesn't quite fit your specifications. Its only two years old and it was a custom built machine (not by me, by an independent computer store). I don't run it anything close to continously, though it is on a good bit of the day. The components aren't top of the line, but to the best of my knowledge they're still pretty good (300G Western Digital Hard Drive, Jetway V4MDM/V4MDMP).  motherboard). 

I keep coming back to the overheating theory for a number of reasons. First off when doing the backing up today I had the cover off and a room fan pointed at drive. It was on for a number of hours because of my aforementioned difficulties, and I had no problems. Secondly, I have a Athlon CPU, my hard drive spins at 7200rpm,  I have a small case that's not too well ventilated. I've always been worried that things were running a little hot. Finally, this issue cropped up soon after I moved back home for the summer, and my room at home is much warmer than my dorm room. 

However, I will probably still stress test the drive just to make sure, then I'll probably look into hard drive cooling solutions. I've done a bit of google research but does anyone have any suggestions? I'm looking at the cheapo end of things, but I want something that works relatively well.

~Andrew S.

---

