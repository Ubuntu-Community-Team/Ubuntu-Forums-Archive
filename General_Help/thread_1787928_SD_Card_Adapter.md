---
title: "SD Card Adapter"
date: 2011-06-21
forum: General Help
---

### Post by Hman242 on 2011-06-21
I'm trying to use an adapter for a SDmicro to a normal SD card on my laptop. I get a notification tath something has been plugged in, but it doesn't appear to be recognized. It doesn't show in Nautilus or Gparted. The light next to the SD card reader blinks when the card is inserted instead of being solid. If left in the computer for a few minutes, the light eventually turns off.

I tried booting up Windows on the same computer to see if it recognized it. It told me I needed to format it, but when trying it said that it was write protected. I'm really not sure what to do here, help would be appreciated.

---

### Post by inameiname on 2011-06-21
Is there anything currently on the device? If not, the easiest solution is to simply erase it and reformat it.

To erase, type in the terminal (where /dev/sdX is whatever your device is: /sda, /sdb, /sdc): 

sudo dd if=/dev/zero of=/dev/sdX conv=notrunc

Just be sure to know for sure which one it is before attempting it.

And then once erased, use Gparted to format it to NTFS, Fat32, Ext4, or whatever you want. If you still have issues its gotta be a hardware thing.

---

### Post by Hman242 on 2011-06-21
EDIT: I am able to use this card through my phone, so it's all good. The SD card originally came with the phone, so I guess it is supposed to be used this way.

---

### Post by inameiname on 2011-06-22
The format for phones is either Fat16 or Fat32, both of which are accessible by Ubuntu, so that is strange it works on your mobile only. Who knows, though. I'm sure phone companies will create their very own filesystem just to force you to buy only their products.

---

### Post by westie457 on 2011-06-22
I had a similar problem to this once and when I realised what had caused it I went and bashed my head against a wall.

On the adapter is a little sliding tab. Somehow this had been put into the write-protect position.

---

### Post by inameiname on 2011-06-22
> **westie457 said:**
> I had a similar problem to this once and when I realised what had caused it I went and bashed my head against a wall.

On the adapter is a little sliding tab. Somehow this had been put into the write-protect position.

Good catch...I hadn't thought of that as the culprit. ;)

Although, rereading the threader's first post, I'm not sure that would be the issue as even if it was in the write-protected, read-only position, it would still get recognized.

---

