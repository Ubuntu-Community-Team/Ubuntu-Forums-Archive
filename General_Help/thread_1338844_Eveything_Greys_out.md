---
title: "Eveything Greys out"
date: 2009-11-26
forum: General Help
---

### Post by Xog on 2009-11-26
Whenever I'm trying to do something, the computer completely stops for about 10 seconds with any windows open greying out. It's literally ANYTHING that I do. I went into my log viewer and went to messages.

```

Nov 26 22:00:54 logan-laptop kernel: [ 7509.136795] ata1.00: configured for UDMA/33
Nov 26 22:00:54 logan-laptop kernel: [ 7509.136825] ata1: EH complete
Nov 26 22:00:57 logan-laptop kernel: [ 7511.739901] ata1.00: configured for UDMA/33
Nov 26 22:00:57 logan-laptop kernel: [ 7511.739921] ata1: EH complete
Nov 26 22:00:59 logan-laptop kernel: [ 7514.300658] ata1.00: configured for UDMA/33
Nov 26 22:00:59 logan-laptop kernel: [ 7514.300675] ata1: EH complete
Nov 26 22:01:02 logan-laptop kernel: [ 7517.100653] ata1.00: configured for UDMA/33
Nov 26 22:01:02 logan-laptop kernel: [ 7517.100671] ata1: EH complete
Nov 26 22:01:05 logan-laptop kernel: [ 7519.700658] ata1.00: configured for UDMA/33
Nov 26 22:01:05 logan-laptop kernel: [ 7519.700675] ata1: EH complete
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292661] ata1.00: configured for UDMA/33
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292682] sd 0:0:0:0: [sda] Unhandled sense code
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292686] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292691] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292698] Descriptor sense data with sense descriptors (in hex):
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292701]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292716]         01 3e 24 6a 
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292721] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Nov 26 22:01:07 logan-laptop kernel: [ 7522.292759] ata1: EH complete
Nov 26 22:01:10 logan-laptop kernel: [ 7525.364652] ata1.00: configured for UDMA/33
Nov 26 22:01:10 logan-laptop kernel: [ 7525.364670] ata1: EH complete
Nov 26 22:01:13 logan-laptop kernel: [ 7528.184651] ata1.00: configured for UDMA/33
Nov 26 22:01:13 logan-laptop kernel: [ 7528.184667] ata1: EH complete
Nov 26 22:01:16 logan-laptop kernel: [ 7531.412656] ata1.00: configured for UDMA/33
Nov 26 22:01:16 logan-laptop kernel: [ 7531.412673] ata1: EH complete
Nov 26 22:01:19 logan-laptop kernel: [ 7534.020617] ata1.00: configured for UDMA/33
Nov 26 22:01:19 logan-laptop kernel: [ 7534.020633] ata1: EH complete
Nov 26 22:01:22 logan-laptop kernel: [ 7536.824628] ata1.00: configured for UDMA/33
Nov 26 22:01:22 logan-laptop kernel: [ 7536.824646] ata1: EH complete
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432664] ata1.00: configured for UDMA/33
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432685] sd 0:0:0:0: [sda] Unhandled sense code
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432688] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432694] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432701] Descriptor sense data with sense descriptors (in hex):
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432704]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432718]         01 3e 28 13 
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432724] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Nov 26 22:01:24 logan-laptop kernel: [ 7539.432758] ata1: EH complete
Nov 26 22:01:27 logan-laptop kernel: [ 7542.088643] ata1.00: configured for UDMA/33
Nov 26 22:01:27 logan-laptop kernel: [ 7542.088655] ata1: EH complete
Nov 26 22:01:30 logan-laptop kernel: [ 7544.668648] ata1.00: configured for UDMA/33
Nov 26 22:01:30 logan-laptop kernel: [ 7544.668662] ata1: EH complete
Nov 26 22:01:32 logan-laptop kernel: [ 7547.264652] ata1.00: configured for UDMA/33
Nov 26 22:01:32 logan-laptop kernel: [ 7547.264669] ata1: EH complete
Nov 26 22:01:35 logan-laptop kernel: [ 7549.844646] ata1.00: configured for UDMA/33
Nov 26 22:01:35 logan-laptop kernel: [ 7549.844662] ata1: EH complete
Nov 26 22:01:37 logan-laptop kernel: [ 7552.428649] ata1.00: configured for UDMA/33
Nov 26 22:01:37 logan-laptop kernel: [ 7552.428666] ata1: EH complete
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012652] ata1.00: configured for UDMA/33
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012670] sd 0:0:0:0: [sda] Unhandled sense code
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012673] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012678] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012685] Descriptor sense data with sense descriptors (in hex):
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012688]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012703]         01 3e 24 6a 
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012708] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Nov 26 22:01:40 logan-laptop kernel: [ 7555.012741] ata1: EH complete

```

What's up? I only receive these errors when bittorrent is "verifying local data" 

Edit-
Just got a notification that my HD is failing :popcorn:

---

### Post by Xog on 2009-11-26
Anyone know how long it usually takes from this point for my HD to go capoot?

My screen keeps flashing like my video card is disconnecting from it being loose. :P

---

### Post by cariboo on 2009-11-26
Your hard drive is OK, you have other problems, probably video drivers if you are getting a flashing screen.

---

### Post by Xog on 2009-11-27
> **cariboo907 said:**
> Your hard drive is OK, you have other problems, probably video drivers if you are getting a flashing screen.

I'm pretty sure its HD related. Recently on a bootup I wound up getting several errors after the ubuntu splash screen, had to do an fsck. found like 100 problems and i kept having to press "y" to replace whatever it was, i didn't even know what I was doing. Needless to say I didn't care much, this laptop is very old and has no useful files on it. If you see in the screenshot, my harddrive's ACTIVE life is 1.8 years. That's just counting how long my laptop was on and the HD in actual use.

However, when I'm watching videos (currently watching the whole ruroni kenshin series) the video stops at intervals between 16 minutes and 17 minutes on any video. I go into my log viewer and see the message:

Nov 27 00:36:56 logan-laptop kernel: [16870.861613] ata1.00: configured for UDMA/33
Nov 27 00:36:56 logan-laptop kernel: [16870.861637] sd 0:0:0:0: [sda] Unhandled sense code
Nov 27 00:36:56 logan-laptop kernel: [16870.861640] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Nov 27 00:36:56 logan-laptop kernel: [16870.861646] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Nov 27 00:36:56 logan-laptop kernel: [16870.861652] Descriptor sense data with sense descriptors (in hex):
Nov 27 00:36:56 logan-laptop kernel: [16870.861656]         72 03 13 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Nov 27 00:36:56 logan-laptop kernel: [16870.861670]         01 3a ac f3 
Nov 27 00:36:56 logan-laptop kernel: [16870.861676] sd 0:0:0:0: [sda] Add. Sense: Address mark not found for data field
Nov 27 00:36:56 logan-laptop kernel: [16870.861711] ata1: EH complete


I looked these messages up and they're all related to hard drive failures. :(

From what I can understand, it's basically saying it can't read certain parts of my hard drive, thus the video problems.


However, if there's a way you can help me by making sure it's NOT a HD failure, please let me know now so I don't have to waste money buying a new one tomorrow :-p

---

### Post by Xog on 2009-11-27
I just found something very interesting.

```
logan@logan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G   57G   46G  56% /
udev                  501M  252K  501M   1% /dev
none                  501M  620K  501M   1% /dev/shm
none                  501M  200K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
```

Lol??

The reason I find this interesting is, 

1) before the boot up problem i mentioned in my previous post, I only had 15GB available. 31GB of files were erased, I have no idea what it could be! I wonder what I deleted during the boot up. It was all gibberish to me. All I kept reading was "bad sector blah blah blah erase?(y)' y  'replace blah blah?(y)'
2) What are these? I've never seen them before:
none                  501M  620K  501M   1% /dev/shm
none                  501M  200K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/r

---

