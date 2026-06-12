---
title: "Ubuntu doesn't detect Sansa Fuze MP3 player"
date: 2009-11-22
forum: General Help
---

### Post by e.m.fields on 2009-11-22
sigh...
I'm sorry to be one of the people shouting for help on the forums, but I'm feeling very defeated here.

Got a new Sansa Fuze MP3 player.  (product [here]("http://www.sandisk.com/products/sansa-music-and-video-players/sandisk-sansa-fuze.aspx")) I knew it was good to hope that it would simply work.  Ubuntu does not detect the device. 

lsusb does not show device.
I've tried changing the settings on the MP3 player itself from "auto-detect" to "MSC" and "MTP" modes, with no effect.
Firmware is up to date. (version 2.2 something)
USB cable is fine.

dmesg gives me this: 
```
usb 1-3: new high speed USB device using ehci_hcd and address 19
hub 1-0:1.0: unable to enumerate USB device on port 

```

I haven't seen anyone else on the forums saying it doesn't work for them. It should be supported.  Can anyone help me figure out how to mount this device?

despondently yours,

---

### Post by megadave on 2009-11-26
I have a cheapo Sandisk 4 GB player that worked great under 9.04.  As soon as I upgraded to 9.10 it no longer automounted.

Other USB sticks and external drives mounted fine.

I had the same error with "unable to enumerate".  I switched the USB settings to MSC, rebooted the device, reconnected it.  

**lsusb** showed the device
**dmesg | tail** showed that it was now on sde
I can mount sde and use the device but it still doesn't automount.

Looking at solutions other's used, but they haven't worked for me.

---

### Post by megadave on 2009-11-26
Things have went from weird to retarded.  

Just after I typed out the previous reply, after having manually mounted my Sansa player and umounting it, I plug it back in and now it's getting auto mounted.

I'm confused.:popcorn:

---

### Post by VonSpyder on 2011-01-19
let me know if this works as it may be the solution ot both our problems.

[http://spicifer.blogspot.com/2008/07/sandisk-sansa-fuze-8gb-on-ubuntu-804.html]("http://spicifer.blogspot.com/2008/07/sandisk-sansa-fuze-8gb-on-ubuntu-804.html")

---

### Post by VonSpyder on 2011-01-19
Also, I tried plugging fuze into my comp that has maverick (10.10) and it detected it in MSC mode. I think this is a bug for Lucid that may have been solved with maverick. Normally I feel more comfortable with LTS releases, but i refuse to load windows everytime i need to put mp3s on my fuze so im upgrading my desktop to mav as well.

---

### Post by aripaul on 2011-09-28
hi,

I have a playbox quadro 440 and i recently installed ubuntu 11.04 but  when i connect my mp3 player it does not recognize it. it charges his  battery but i cannot access it to add music/remove music. any help?

i tried the dmesg but i am very new to linux and i have just installed unbuntu 11.04

this is what dmsesg shows me:

 Direct-Access     GENERIC  USB DISK DEVICE  1.00 PQ: 0 ANSI: 0 CCS
[  834.048976] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  834.052238] sd 4:0:0:0: [sdc] 3833344 512-byte logical blocks: (1.96 GB/1.82 GiB)
[  834.052982] sd 4:0:0:0: [sdc] Write Protect is off
[  834.052994] sd 4:0:0:0: [sdc] Mode Sense: 00 12 00 00
[  834.053003] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  834.056491] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  834.060487]  sdc:
[  834.064843] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[  834.064859] sd 4:0:0:0: [sdc] Attached SCSI removable disk

---

